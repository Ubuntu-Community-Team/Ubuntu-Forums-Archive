---
title: "How to transfer a 1.3gb file over the internet?"
date: 2009-08-16
forum: General Help
---

### Post by miggerish on 2009-08-16
Hi,

I am running Ubuntu the latest one.  I am wondering how do I transfer a 1.3gb file to my dad's computer with out having a usb disk drive.  I am looking for a way to do it over the internet. Oh, also it needs to be free.  Thanks in advance.

---

### Post by philcamlin on 2009-08-16
create an apache server and transfer it that way 
thats what i do for all my files

---

### Post by miggerish on 2009-08-16
> **philcamlin said:**
> create an apache server and transfer it that way 
thats what i do for all my files

can you give me a link to an easy to understand guide on how to do an apache server please?

---

### Post by snotplop on 2009-08-17
use an SSH and SCP combination.

Sitting at the machine that needs the file, open a terminal and enter
```
$ sudo apt-get install ssh scp
```Find the absolute path local to the machine that already has the file on it:
```
$ ssh yourusername@your.ip.address
```Use 'cd' and 'ls' within the ssh'd environment.

Once you've found it's path, open up another terminal on the destination machine and enter:
```
$ scp yourusername@ip.address.of.file's.machine:/absolute/path/to/file ./
```The './' means "copy the file to the directory I am currently in"

---

### Post by scouser73 on 2009-08-17
You could try uploading the file to one of those free online storage sites, then go onto your dad's pc and download it from there. [[COLOR="Red"]**Free Online Storage**[/COLOR]]("http://www.google.co.uk/#hl=en&q=free+online+storage&btnG=Google+Search&fp=1b311284ac0b25f6")

---

### Post by Nburnes on 2009-08-17
You could use something like Megaupload I guess?

---

### Post by credobyte on 2009-08-17
```
sudo apt-get install apache2

```

Move your file to /var/www/ and open from wherever you want ( dads pc, school, etc. ).
Example: [http://127.0.0.1/file.rar](http://127.0.0.1/file.rar) ( replace 127.0.0.1 with your external IP address ).

---

### Post by hyperdude111 on 2009-08-17
Its very easy.

Option 1: Look up ultra vnc. It runs on windows and ubuntu with wine.
If you have the local ip address (192.168.0.x) you can remote control the other machine. It also includes a dialog to do file transfers.

Option 2: is set up a samba share. Its very easy Right click on a folder you want to share go to share options. Open it up completely, you will then be asked to install samba just accept. 

You will need to know your computer name, mie is "hugo-dekstop" because my log in name is hugo.

Go to your dads windows machine and type \\xxxx-desktop\ open the folder that comes up and copy over the file.

---

### Post by nikhilk on 2009-08-17
From all the suggestions everyone has given, these are my comments:

 * Using Samba, Apache or FTP, all with proper authentication and configuration seems to be the best way
 * Using some free upload site would be wasteful if you are going to do the transfer only once as it involes data movement twice, one upload to the storage provider's site and one download to your Dad's machine.
 * Installing ssh just for file transfers seems to be an overkill as it exposes a lot more functionality than required for simple file transfer, hence greater risk

---

