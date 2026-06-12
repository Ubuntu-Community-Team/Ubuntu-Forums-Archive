---
title: "copy local files using wget"
date: 2010-06-24
forum: General Help
---

### Post by TheOne...more on 2010-06-24
hi, i was trying to copy some files over my hdd using wget.

this was the format of the command

```
wget -rkpLl 9 -nd ftp://myUSERID:myPASSWORD@mymachie//home/test
```

the catch is that there is a local website that is installed into directory heirarchy and i would like to use wget to make the html files link to each other in one directory level.

the command didn't work inspite of trying different forms, so what's the mistake in this command or is there another way?


thanx

---

### Post by 3Miro on 2010-06-24
In order to use wget you need to have either an http or ftp server installed. Then the address would be something like:
```
ftp://localhost/some_path
```

If you just have a bunch of files into a directory structure and you wish to move them all in one place, you should look for a script that does that. It would be easier then the http or ftp way.

---

### Post by TheOne...more on 2010-06-24
well i found this site before and it didn't mention the need for a local server installed [http://kspace.in/blog/2010/02/22/copy-files-using-wget/](http://kspace.in/blog/2010/02/22/copy-files-using-wget/)

also i can do some sed but the files are too numerous. so if there was some easier solution that would be great.

---

### Post by 3Miro on 2010-06-24
> **TheOne...more said:**
> well i found this site before and it didn't mention the need for a local server installed [http://kspace.in/blog/2010/02/22/copy-files-using-wget/](http://kspace.in/blog/2010/02/22/copy-files-using-wget/)

also i can do some sed but the files are too numerous. so if there was some easier solution that would be great.

From your link:

>  Since wget can download files using **HTTP/HTTP/FTP**, it seems to be an good solution for me. And Yes, It was!

A simple example of copying directory from **remote machine** would be 

Wget cannot do what you want it to do. Your best bet is bash scripting, but I am not good at it. Bash script is a simple program that you can create with gedit that will do all kinds of file manipulations, however, you will have to do some reading first (as I said I am not good at it).

You can also make a separate thread, explain that you need a bash script that does so and so and make sure people don't think this is some sort of a homework assignment.

---

