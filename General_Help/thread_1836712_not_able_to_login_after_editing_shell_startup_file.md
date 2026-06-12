---
title: "not able to login after editing shell startup files"
date: 2011-08-31
forum: General Help
---

### Post by shwety1085 on 2011-08-31
Hi,
I added a line to the sh based shell startup file (~/.profile ) and also to ~/.bashrc so as to reflect the read only copy of the course directory in my home directory. 
I was unable to login in my ubuntu after that. My system is locked now. 

Please help me with this !:(

---

### Post by krytorii on 2011-08-31
Try booting from a live cd and undoing the changes you have made.

If you have permission errors from the livecd, open a terminal and use sudo gedit [filename] to get access

---

### Post by shwety1085 on 2011-08-31
Thanks a lot for the help !
Could you please explain it a little bit. I am a newbie and not able to understand what exactly you are saying.

---

### Post by krytorii on 2011-08-31
The cd/dvd you used to install ubuntu with should have an option when you installed it to try rather than install ubuntu. Boot up the CD, and select that option (may take a while to load).

You'll end up in ubuntu and can even use firefox to view this thread whilst there. then go and enter your filesystem by going right to the very "top" of the folder tree thing. Then go into media, the hard drive partition that ubuntu is in, then find the files you need to edit. Undo whatever you did, save them and then turn on the computer without the cd.


The rest of this may be completely irrelevent, ty the above first.


The only problem is you may not have access to the files by default. If that happens, open up a terminal (Put terminal into the dash or press ctrl-alt-t).

Then navigate to the folders that have your files in. use [this ]("https://help.ubuntu.com/community/UsingTheTerminal#File_.26_Directory_Commands")to help, I'll put some more instructions just in case.

type ```
cd [name of folder]
``` to change folder. at first you'll want to go use ```
cd /
``` to go to the folder at the "top".

Then go into media (```
cd media
```). Then traverse through the file system to the folder you need to be in. us the command ```
ls
``` to see what is in each folder, and press tab to auto complete names (useful when there's a space in the name of a folder).

When you get to the right place, type in ```
sudo gedit [name of file]
``` to open it.

---

### Post by shwety1085 on 2011-08-31
I didnt use a cd or dvd for installing ubuntu. I have used wubi installer to dual boot it with windows 7.

Is there any other way i can undo the changes i made in the sh based shell startup files??

(I made those changes from the terminal itself by opening the files using vi command and proceeding from there.)

I have kernel version 3.0.1 installed in ubuntu 11.04 natty narwal

---

### Post by krytorii on 2011-08-31
Not too sure if there's another way...

Try making a livecd, just follow the instructions on the ubuntu main page. All you need is a blank disc and a computer with a disc writer.

This won't exactly fix your problems as such, but you can use the livecd to copy any important files to a pendrive or different partition (you could move them to your windows folders) and then do a proper install. I did my first proper install after wubi sort of stopped working.

Also, whenever editing anything important, make a backup first. Only the other week I couldnt log in because I screwed around with a config file to get my monitors working :lolflag:

Fixed it using a livecd too :D

---

### Post by bcbc on 2011-08-31
Boot into recovery mode. Drop to a root shell. Change files. Reboot.

---

