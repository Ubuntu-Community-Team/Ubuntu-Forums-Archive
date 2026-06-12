---
title: "ISO master? (trying to create my own .iso)"
date: 2012-02-01
forum: General Help
---

### Post by cptrohn on 2012-02-01
Has anybody used this app much?  I got it installed, and I can highlight the files that I want to add to an .iso, but when I hit the ```
add
``` button in the middle of the GUI to try and add the files to create the actual .iso it doesn't do anything at all with the highlighted files.....

So is there something that I am missing here?  I might just end up giving up on it and doing it the old fashioned way in command line I guess....  Was just hoping for a quick and easy way to create my own .iso's

Any help from some more experienced pros out there would be GREATLY appreciated...

edit:  Oh yeah and to make it even harder I want to make it bootbable.... lololol
So do I need to create an .img file first and then convert it into an .iso?

---

### Post by jayshomebrew on 2012-02-02
download .img:
[http://www.stchman.com/tools/DosBootimage.zip](http://www.stchman.com/tools/DosBootimage.zip)
unzip and extract img file.

goto to the ubuntu software center and install k3b
run k3b
create 'new data cd project'.
[IMG]http://img546.imageshack.us/img546/1397/tmpfvorw8.png[/IMG]


click on 'edit boot images'
[IMG]http://img707.imageshack.us/img707/2561/tmp5jrns4.png[/IMG]


click new, add the img.
[IMG]http://img818.imageshack.us/img818/2514/tmpr7qvf2.png[/IMG]

click ok,
add your files, and burn..
[IMG]http://img515.imageshack.us/img515/1905/tmpwhpkza.png[/IMG]


other img files you can play with:
[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

---

### Post by cptrohn on 2012-02-02
> **jayshomebrew said:**
> download .img:
[http://www.stchman.com/tools/DosBootimage.zip](http://www.stchman.com/tools/DosBootimage.zip)
unzip and extract img file.

goto to the ubuntu software center and install k3b
run k3b
create 'new data cd project'.
[IMG]http://img546.imageshack.us/img546/1397/tmpfvorw8.png[/IMG]


click on 'edit boot images'
[IMG]http://img707.imageshack.us/img707/2561/tmp5jrns4.png[/IMG]


click new, add the img.
[IMG]http://img818.imageshack.us/img818/2514/tmpr7qvf2.png[/IMG]

click ok,
add your files, and burn..
[IMG]http://img515.imageshack.us/img515/1905/tmpwhpkza.png[/IMG]


other img files you can play with:
[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

Ah thank you very much!  I did the K3B process when I created my .iso on the first run but looks like I needed the Dosbootimage that you listed to do what I wanted to.  Thank you very, very much for the help!

---

### Post by Dumbestcrayon on 2012-02-02
I don't know if you prefer GUI or CLI, but here's a good way to do it in with CLI.

[Credit]("http://ubuntuforums.org/showpost.php?p=4349548&postcount=1")
> **Martje_001 said:**
> Hi,
I was looking for this (for a BASH script I wanted to write), and I found out how to do it. Now I want to share it ;)

**1.** Create ISO-file from folder
```
mkisofs -r -o /isofile.iso /folder
```
where */isofile.iso* is the relative or absolute path to the iso-file you want to create and */folder* the absolute or relative path to the folder you want to backup.

**2.** Create ISO-file from file(s)
```
mkisofs -r -o /isofile.iso /mybigfile
```

or if you want to backup multipi files (like you .mp3 collection):
```
mkisofs -r -o /isofile.iso *.mp3
```

**3.** Create ISO-file from a cd/dvd-drive
```
dd if=/dev/cdrom0 of=isofile.iso
```
where */dev/cdrom0* is your cd/dvd-drive and *isofile.iso* your iso-file you want to create.

*Note: An absolute path is like '/home/yn/myfile.iso', a relative path is like 'myfile.iso'*

---

