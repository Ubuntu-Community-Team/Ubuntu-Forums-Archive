---
title: "Brasero truncates file names for Windows (but not Linux)"
date: 2009-07-27
forum: General Help
---

### Post by ecol on 2009-07-27
Brasero on Ubuntu 9.04 seems to truncate and capitalize file names on DVDs, but only when the DVD is opened on Windows. When the DVD is opened on a Linux computer, the file names seem to have been written correctly. However, the same disk opened on a Windows computer shows 8.3 format all-capitals file names. This seems to be the case both with and without the "Windows compatibility" box ticked in Brasero.

Is there any way of making the full file names visible to Windows? This is quite an important feature for me!

---

### Post by wojox on 2009-07-27
Try something like 8-3 
Then it wont find the decimal so it can't truncate.

---

### Post by ecol on 2009-07-27
I am not sure I understand your reply. Are you suggesting I rename all my files to DOS-style 8.3 format (i.e. truncate the original file names myself)? This does not seem like a very practical solution, especially when both Linux and modern versions of Windows allow long file names.

I want long file names on Windows, not short file names on Linux!

---

### Post by The Cog on 2009-07-27
See if there is an option to enable joliet extensions in brasero. That adds extra info into the filesystem that contains the full filename. Here is a reasonable explanation:
[http://en.wikipedia.org/wiki/Joliet_%28file_system%29](http://en.wikipedia.org/wiki/Joliet_%28file_system%29)

I think Brasero can add the extended information, even if it doesn't actually call it Joliet.
If not, I know that k3b can.

---

### Post by moster on 2009-07-27
Use GnomeBaker till you find out why this happend.

---

### Post by ecol on 2009-07-27
I cannot find an option to enable Joliet extensions. For what it's worth, the full file names are being stored somewhere on the disk because they are used when the disk is opened on a Linux computer. They just seem to be invisible to Windows.

I tried Gnome Baker, but it seems to crash before writing anything.

---

### Post by moster on 2009-07-27
hm... now when I remember it crashed to me too first time. But never after that. Try with k3b, it must work with something, we are all burning something :)

---

### Post by moster on 2009-07-27
hm... now when I remember it crashed to me too first time. But never after that. Try with k3b like cog tell, it must work with something, we are all burning something :)

---

### Post by ecol on 2009-07-27
Writing a DVD using the default settings in K3b works perfectly. The file names are correct in both Linux and Windows. I guess I need to report a bug in Brasero. Thanks for your help and suggestions.

---

### Post by moster on 2009-07-27
You do that. I cannot believe in such obvious bug. Ok, bye :)

---

### Post by lautarop on 2009-08-15
I have the same problem.

I guess I'll try k3b...

---

### Post by MScapee on 2009-08-18
For what it's worth, I solved all of the problems I was having with Brasero by ditching it and installing Xfburn.  All I wanted was something to write data disks without either complaining, creating coasters or taking an hour to burn a damn disk...  Xfburn works flawlessly, it's fast burning and it's Gnome-friendly (I absolutely despise KDE apps).  Oh, and it's also actively developed unlike some Brasero alternatives.   Definitely worth checking out.

---

### Post by alfu on 2009-08-21
Yes, I am having the same problem too (the same data DVD shoved back into the Ubuntu machine shows file names just fine) and it is very frustrating, but it is in being read by Macintosh OS9 rather than Windoze.  Mac OSX shows the filenames just fine, as does Ubuntu.

Just tried Xfburn -- started it up (took a while to find out you CAN burn from files on other partitions -- look in 'Filesystem/media') and started it up -- walked back in a few minutes later to see how far it had gotten, and it was FINISHED!  It also capitalizes filenames when read with Macintosh OS9, but at least it does NOT truncate them.  I am impressed with it; thanks, MScapee.

A tip for people burning data files from Mac OS9: you will want to get rid of the many RESOURCE folders and ICON and FINDER.DAT files littering your file structure before burning because due to the directory limitations on the DVD they each take up half a megabyte!  

Ubuntu easily does this with 
   1) Select the partition the files are on
   2) <CTL-F> (find), typing the file name into the search box, hitting <RTN> 
   3) <CTL-A> to select all the files you want to trash
   4) <DEL>.  Presto-changeo, all gone.

I looked into the problem on the Web and could only find suggestions to write a bash script, FWIW.

---

### Post by mgarl10024 on 2009-09-20
I also have the same problem with 9.04.  Real shame.

I guess I'll try k3b as well...

---

### Post by PetruM on 2009-09-30
Same problem with Brasero. Using K3B with the default settings did not cause problems. :guitar:

---

