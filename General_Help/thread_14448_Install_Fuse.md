---
title: "Install Fuse"
date: 2005-02-07
forum: General Help
---

### Post by Gangsta on 2005-02-07
Hi,

I wanted install fuse so i can use SieFS to acces my siemens SL55 Flexmem, but when i try to configure fuse it says,

checking kernel source directory... Noy found
configure: error:
*** Please specify the location of the kernel source with
*** the '--with-kernel=SRCDIR' option

But i cant find the source dir of my kernel,

Can someone help me.

Greetz Justin.

---

### Post by ioliver on 2005-02-08
You don't need the kernel source, just the headers. I just installed the headers for my kernel using synaptic and "It Just Worked"(tm)

I also needed to add (from memory) - autoconf, libtool, build-essential, coreutils.

You need to remember to do "sudo make install" after its all built.

Regards

Ian

---

### Post by Gangsta on 2005-02-08
[QUOTE=ioliver]You don't need the kernel source, just the headers. I just installed the headers for my kernel using synaptic and "It Just Worked"(tm)

I also needed to add (from memory) - autoconf, libtool, build-essential, coreutils.

You need to remember to do "sudo make install" after its all built.

Regards

Ian[/QUOTE]

Thnx but i still got this message:

checking kernel source directory... Noy found
configure: error:
*** Please specify the location of the kernel source with
*** the '--with-kernel=SRCDIR' option

---

### Post by DJ_Max on 2005-02-08
When you install the kernel headers, you need to tell where the directory it's in.

---

### Post by Gangsta on 2005-02-08
[QUOTE=DJ_Max]When you install the kernel headers, you need to tell where the directory it's in.[/QUOTE]

/usr/src/ There are the headers

---

### Post by ioliver on 2005-02-12
> When you install the kernel headers, you need to tell where the directory it's in.

Not IME

I installed the headers and fuse made without errors. Make sure the headers *exactly* match the version of the kernel you are using. Does fuse have a bootstrap script? If so, then run this 1st.

You may also need to copy the config from /boot into the kernel header directory. Please check this step - I only half remember it and have a feeling that it might not have been necessary in the end. I certainly haven't done it since when upgrading kernels.

Ian

---

### Post by droneboy on 2005-03-25
Coincidentally I've had exactly the same need & problem, to get my MC60 mounted under ubuntu using SieFS. I did this successfully under Mandrake 10.1 so was a tad disappointed that it's not happening under Ubuntu (hoary). 

The above recommendation worked as far as getting fuse 1.x to compile, but I've run across a new problem in that the fuse module doesn't want to load. It gets rejected as invalid or having unknown symbols depending on which version of gcc it was compiled with. 

After raking google thoroughly for a solution it seems that the 2.6.10 kernel is just incapable of playing nice with fuse 1.x, and as SieFS won't compile against fuse 2.x then there's really not much I can see to do other than install a different kernel. Maybe 2.6.11+ won't have the same issues, or maybe it will. The other option would be convincing the authors of SieFS to rewrite it to use fuse 2.x but it seems like an unmaintained project to me.

---

### Post by kamstrup on 2005-08-22
Just to update this thread; Version 0.5 of [SieFS](http://chaos.allsiemens.com/siefs/) uses FUSE 2, but states that it requires a 2.4 kernel..? Does anybody have knowledge on this? It would seem weird to have a kernel version dependancy when FUSE is a File system in User SpacE... Not?

It even seems that FUSE 2.2.1 is in Hoary universe... That should ease up SieFS installation. Furthermore from 2.6.13 the linux kernel will ship with FUSE out of the box. If I can find a a cable when I get home I'll play around a bit, and let you know.

Cheers

---

### Post by burlap on 2005-08-23
Both fuse and siefs work (tested with s65):

From Ubuntu repositories (main and universe, I think) you need: 
linux-headers 
module-assistant (or you can build the package yourself, module-assistant is easier)

Module-assistant will get fuse-source for you and compile it. Ready deb package is later placed in /usr/src (fuse-module-...). 

Install this module package and fuse-utils, libfuse2, libfuse2-dev (from the repositories). 

Compile siefs 0.5 (it works with 2.6 kernel and fuse 2).

Mount and browse your siemens as root (mount -t siefs /dev/depends_on_connection /your_directory).

---

### Post by primeirocrime on 2005-10-05
I've managed to get fuse and SieFs working following Burlap instructions on siemens M65. But I miss something I used to use on WinXP, it was an app that opened the hidden areas so I could change the icons and other stuff  [company logo etc etc] Is it possible to do this with SieFs?

---

### Post by ZiZi on 2006-03-15
Is there a way how to browse the mobile's content without having to be root? I tried to change permissions to the device (/dev/ircomm0 in my case), to the mountpoint, but it simply didn't do the trick :-k  :mad:

---

### Post by Grim_n_Evil on 2006-07-03
After 2 days of work I finally got my phone to mount via IrDA but when I ls the directory, I get an I/O :evil: :evil: :evil: :evil: 

Any ideas???

---

### Post by Kenzy88 on 2006-11-09
> **ZiZi said:**
> Is there a way how to browse the mobile's content without having to be root? I tried to change permissions to the device (/dev/ircomm0 in my case), to the mountpoint, but it simply didn't do the trick :-k  :mad:

Hi... u have the same problem... i want to browse it by being user... the problem is that there is something wrong with the permission... they seems malformed...
```

tux@tux-desktop:/media$ cd mobile
bash: cd: mobile: Permesso negato
tux@tux-desktop:/media$ sudo ls mobile 
Animation  EMS sounds  Internet  Ringing tone  telecom
Bitmap     Inbox       java      sms           tmp
tux@tux-desktop:/media$ ls -l
totale 4808
lrwxrwxrwx  1 root root          6 2006-06-05 17:43 cdrom -> cdrom0
drwxr-xr-x  2 root root       4096 2006-06-05 17:43 cdrom0
drwxr-xr-x  2 tux  root       4096 2006-07-29 02:30 dvd
dr-xr-x---  1 root plugdev 4874240 2006-11-09 05:13 hda1
drwxrwx--- 15 root plugdev    4096 1970-01-01 01:00 hdb2
drwxrwx--- 21 root plugdev   32768 1970-01-01 01:00 hdb5
?---------  ? ?    ?             ?                ? mobile
drwxr-xr-x  2 root root       4096 2006-07-26 15:42 virtual
tux@tux-desktop:/media$ 

```
This is what i get... and also with nautilus it seems that the folder is not a folder and it say that there is something wrong with the permisison... any hint???

[[IMG]http://img485.imageshack.us/img485/9533/screenshot1le8.th.png[/IMG]](http://img485.imageshack.us/my.php?image=screenshot1le8.png)
[[IMG]http://img485.imageshack.us/img485/2189/screenshot2hs8.th.png[/IMG]](http://img485.imageshack.us/my.php?image=screenshot2hs8.png)
[[IMG]http://img359.imageshack.us/img359/5452/screenshot3iu1.th.png[/IMG]](http://img359.imageshack.us/my.php?image=screenshot3iu1.png)

ps: sorry 4 my bad english

---

### Post by ciarlese on 2007-08-09
Hi, i am a new poster.
I have a siemens cellphone, mc60.
I installed fuse and siefs, I mount, but if I make sudo ls /media/cell, I get a I/O error.
I see the same things as Kenzy88 (the directory is not a directory anymore, something strange about permission), but I cannot access my cell's fs.
How can I?

---

