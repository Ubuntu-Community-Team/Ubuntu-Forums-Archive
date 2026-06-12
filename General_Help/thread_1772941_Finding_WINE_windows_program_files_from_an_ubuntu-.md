---
title: "Finding WINE windows program files from an ubuntu-formatted external HD"
date: 2011-06-01
forum: General Help
---

### Post by andrewcd on 2011-06-01
I recently destroyed my laptop, but was able to save the harddrive. As I'm transferring everything over to my new machine (both lenovo x200s, both Lucid), I can't find the location where WINE stored all of the programs and such -- the things that you see if you go to the applications menu, go to WINE, and go to "browse c drive."  

I read [this]("http://ubuntuforums.org/showthread.php?t=249812") old thread, which says that it should be located at  /home/name/.wine/drive_c, but I don't know how to point the terminal at an external hard drive, nor do I know how to use the GUI to un-hide a hidden folder.  I tried gksudo nautilus, but it didn't show me anything that wasn't there without nautilus.

I'd appreciate any help with 
1.  How to point the terminal at an external hard drive
2.  How to use the GUI to un-hide hidden files
3.  Any other ways of transferring wine programs from an external HD

---

### Post by seawolf167 on 2011-06-01
Open your terminal, change the directory to the external harddrive

```
cd /path/to/external/drive
```If your device is mounted it will mount by default in /media, you can see available mounted drives by typing

```
ls /media
```Then change to that directory (say it is /media/200GBFilesystem)

```
cd /media/200GBFilesystem
```Your Wine programs are in the ~/.wine directory, which would be

```
cd /media/200GBFilesystem/home/*yourusername*/.wine/drive_c
```where *yourusername* is the username that you used on that Ubuntu install.

Hopefully this helps

---

### Post by andrewcd on 2011-06-01
Thanks!  

Now: stupid question: how do you use the terminal to move files from one location to another?

---

### Post by seawolf167 on 2011-06-01
No question is stupid! 

to move files, use the *mv* command, to copy files, use the *cp* command

```
mv /source/file.extension /destination/file.extension
```For lots more command info, check out the "LinuxCommands" link in my signature. Also *man* pages are your best friend.

To see the man page for mv

```
man mv
```gives you all its options, switches, examples, etc.

---

