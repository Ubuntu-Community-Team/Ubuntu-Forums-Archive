---
title: "Su password problems"
date: 2011-05-24
forum: General Help
---

### Post by Jverm on 2011-05-24
It appears that I have forgotten my password for su or superuser or whatever it is. I need to find a way to disable it or change it or something. I'm on 11.04 natty

I looked at some other threads regarding the grub screen but some of the steps didn't really work for me so I'm seeking help in my own thread :P
Thanks

---

### Post by linuxinstalledfromhdd on 2011-05-24
You might be able to reset your system password from recovery mode and dropping to the root command line. If you don't know how to do this, you would need to contact your administrator who installed your system.  Or if that is you, reinstall your entire system.

---

### Post by Jverm on 2011-05-24
Jesus, ok. 
Yeah I installed it from USB onto my gateway. I'll try recovery mode
Thanks

---

### Post by linuxinstalledfromhdd on 2011-05-24
No problem.  Glad to be of help.:lolflag:

---

### Post by Jverm on 2011-05-24
Recovery mode doesn't do anything. 
Just turns my Monitor into a stage of command prompts telling me About my USB ports.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Well if you wait a while it gets to a blue screen menu where you can then arrow down and select drop to root command line.  How long did you wait? Or did you catch errors?

---

### Post by Jverm on 2011-05-24
It's been like 5 mins. 

[IMG]http://i1177.photobucket.com/albums/x345/jverm/a7129ece.jpg[/IMG]

---

### Post by linuxinstalledfromhdd on 2011-05-24
Uh-oh. It looks like you have a bigger issue than just losing your password. 

BUMP (wait a while for someone to find this thread who -may- know a work around)

---

### Post by NoNameWill on 2011-05-24
I can't get su either. For some reason my password doesn't work. Howerever if I use this command and password it works.

```
sudo su
```Unless you actually forgot your password this won't work as it will ask for password. I think it might be a 11.04 issue.

---

### Post by Jverm on 2011-05-24
Lol **** really? Damn you old gateway computer. This is the computer I play with so will re installing the os fix me?

---

### Post by linuxinstalledfromhdd on 2011-05-24
For now you can create a USB live stick of Ubuntu 10.10

Here is a walkthrough:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by Jverm on 2011-05-24
how do i re install 10.10 over existing 11.04? it only creates a windows type startup disk

---

### Post by linuxinstalledfromhdd on 2011-05-24
Just create a 10.10 for now so you can test it as a Live Bootable Disc. That way you can know if it helps your situation. You can burn the live version to a disc or USB. I like USB because it installs faster too.  It's up to you.

---

