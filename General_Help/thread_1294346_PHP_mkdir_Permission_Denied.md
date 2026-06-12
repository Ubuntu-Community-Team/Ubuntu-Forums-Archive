---
title: "PHP mkdir Permission Denied"
date: 2009-10-18
forum: General Help
---

### Post by Strega on 2009-10-18
Hello,

I'm making a PHP script on my ubuntu server wich has to make a dir with the 777 permission.
The script is located in
/home/concertband/public_html/pages/gallery/admin.php
and has to make a directory in
/home/concertband/public_html/gallery/

When I execute the script it gives me the Permission Denied error.
I've set the permissions of the /gallery/ directory to 777 but still I got that error.
What else can I try to do ?

edit :
I've posted this on this forum because I thought I might have to do something with chown or groups or something like that on my server, but have absolutely no idea what.

Regards, Strega

---

### Post by yeats on 2009-10-18
> I've posted this on this forum because I thought I might have to do something with chown or groups or something like that on my server, but have absolutely no idea what.


Since you mention it, why don't you:

```
ls -l /home/concertband/public_html/pages/gallery/admin.php
```

and report back the output :-)

---

### Post by Strega on 2009-10-18
Hello

This is the output:
```
-rw-r--r-- 1 concertband users 2.4K 2009-10-18 12:50 /home/concertband/public_html/pages/gallerij/admin.php
```

Thank you for the reply.
Regards

---

### Post by Joeb454 on 2009-10-18
I'd imagine that ```
ls -l /home/concertband/public_html/ | grep gallery
``` would also help, as we can see if the gallery directory is writeable to the correct groups :)

---

### Post by Strega on 2009-10-18
Hi,

This is the output of
```
ls -l /home/concertband/public_html/ | grep gallery
```
```
drwxrwxrwx 4 www-data    users 4.0K 2009-10-18 13:19 gallery
```

Regards

---

### Post by Strega on 2009-10-18
No idea what to do ?

Regards

---

### Post by OpenGuard on 2009-10-18
[PHP]$new = "../newdir";
mkdir($new);
chmod($new, "0777");
[/PHP]

[PHP]$base = "/home/concertband/public_html/"
$newdir = "newdir";
exec("mkdir $base $newdir");
chmod($base . $newdir, "0777");[/PHP]

Haven't tested them but they should work.

---

### Post by Strega on 2009-10-18
Still Permission Denied :s

---

### Post by OpenGuard on 2009-10-18
> **Strega said:**
> Still Permission Denied :s

Show us the output of the following command.
```
ls -l $HOME | grep public
```

---

### Post by Strega on 2009-10-18
Doesn't give me any output :s

---

### Post by OpenGuard on 2009-10-18
> **Strega said:**
> Doesn't give me any output :s

```
dainis@ubuntu:~$ ls -l $HOME | grep public
drwxr-xr-x 2 dainis dainis 4096 2009-10-18 19:48 public_html
```

Unless it looks like the code above, you are doing something completely wrong.

Does it ( directory ) even exist ?
```
stat ~/public_html
```

---

### Post by rhythmiccycle on 2009-10-18
its gotta be the permission of the 
*file running the script, 
*the folder its in
*the folder that the new dir is being put in
OR
*a file that you are including

you have to be overlooking something.

can you post the error message that the browser gives, and the url.

---

### Post by Strega on 2009-10-18
Sorry, I was doing that
```
ls -l $HOME | grep public
```
thing with root.
This is what I get with the "concertband" user
```
drwxr-xr-x 9 concertband root 4096 2009-10-18 17:36 public_html
```
This is the exact error
```
Warning: mkdir() [function.mkdir]: Permission denied in /home/concertband/public_html/pages/gallerij/admin.php on line 57
```

---

### Post by rhythmiccycle on 2009-10-18
> **Strega said:**
> 
```
Warning: mkdir() [function.mkdir]: Permission denied in /home/concertband/public_html/pages/gallerij/admin.php on line 57
```

this tells me that the error occurs after admin.php is open

what are the permission of the folder you are witting to?


what is the output of:

```
 
ls -l /home/concertband/public_html/gallery/

```

also can you show what is on ".../admin.php on line 57"

---

