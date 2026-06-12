---
title: "php fopen function problem"
date: 2010-01-03
forum: General Help
---

### Post by aichan on 2010-01-03
i have a problem with php fopen() function on ubuntu..

[HTML]<html>
<head>
<title>File Encrypt</title>
</head>
<body>
Choose the file<br>

<form action="submit.php" method="post"><br>
Type (or select) Filename: <input type="file" name="unencrypted">
<input type="submit" value="Encrypt">
</form>

</body>
</html>[/HTML]

[PHP] <?php 
include 'gpg.php'; 
$fileloc = $_POST["unencrypted"]; 
$fh = fopen($fileloc, "r"); 
$text = $fileloc; 
?> 
 [/PHP]

when i try to run it, it error with message :
Warning: fopen(hehe.txt) [function.fopen]: failed to open stream: No such file or directory in /var/www/enkripsi/submit.php on line 4
i have chmod /home/user/ and /var/www/ folder to 777.
open_basedir is disabled..

but when i try this php code on windows platform, it runs fine. what is wrong?

---

### Post by mörgæs on 2010-01-04
I can not test your code on this machine, so it will only be a guess:

Which rights do you have on the file hehe.txt?

---

### Post by tiagoscd on 2010-01-04
The file **hehe.txt** is where in your system? Home folder or /var/www?

---

