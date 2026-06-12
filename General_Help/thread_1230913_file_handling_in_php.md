---
title: "file handling in php"
date: 2009-08-03
forum: General Help
---

### Post by yogi4 on 2009-08-03
Hi m doing file handling in php, my script is -

<html>
<head>
<title>
Flat file
</title>
</head>
<body>
<?php
$today=date("Y-m-d");
$fh=fopen("wtf.txt","a");
fwrite($fh,$today);
fclose($fh);
?>
</head>
</html>

but its showing following error on execution

Warning: fopen(wtf.txt) [function.fopen]: failed to open stream: Permission denied in /var/www/fha.php on line 10

Warning: fwrite(): supplied argument is not a valid stream resource in /var/www/fha.php on line 11

Warning: fclose(): supplied argument is not a valid stream resource in /var/www/fha.php on line 12

I hd tried both in fedora & ubuntu m doing all my work as a root user...

Pls help me in dis regard.Thanx in advance

---

### Post by wojox on 2009-08-03
Did you set the permissions for that file your appending to?

---

### Post by yogi4 on 2009-08-03
yeah m writing it in append mode so i guess d file will be created by default if it dont exist

---

### Post by LoneWolfJack on 2009-08-03
the folder you are trying to create the file in probably is not writable by php

---

### Post by yogi4 on 2009-08-03
i hd changed my directory folder to home bt its still givivng me d same msg

& i m doing all dis as root

plus i hd read sumwhere dat i hd to set my file permission to 755& 711 to make it wrk bt hw to do it ??

---

### Post by LoneWolfJack on 2009-08-03
your home dir needs to be writable by php then. php has its own process and does NOT run as root. besides, you shouldn't work with the root account yourself as well because you're ridiculing the whole security concept of linux this way.

---

### Post by yogi4 on 2009-08-03
bt to save my files in /var/www file i hv to login as root otherwise it gives permission denied message

How to make my home directory writable by php??

---

### Post by yogi4 on 2009-08-04
ppl pls help me in this regard!

---

### Post by credobyte on 2009-08-04
```
sudo chmod 775 /var/www

```

or 

```
sudo chown -R user:user /var/www
```
[COLOR=DimGray]** replace user:user with your username[/COLOR]

---

### Post by yogi4 on 2009-08-04
> **credobyte said:**
> ```
sudo chmod 775 /var/www

```

or 

```
sudo chown -R user:user /var/www
```
[COLOR=DimGray]** replace user:user with your username[/COLOR]

Your command wrked i hd to type apache username instead of my username 
Thank u to all 4 ur support

---

