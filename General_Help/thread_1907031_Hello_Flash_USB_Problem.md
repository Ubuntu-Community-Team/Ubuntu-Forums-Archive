---
title: "Hello Flash USB Problem"
date: 2012-01-10
forum: General Help
---

### Post by dak0 on 2012-01-10
Hello, friend of mine just came to me, beacus he knows i have linux, and he asked me to remove all viruses from his USB, beacus other friend infect them, the whole Flash USB is with music mostly MP3. formats, but the problem is that i can`t remove those "viruses: .exe files somehow i can`t move them to trash, can anybody help us please. ;)
I apologize for my English. 

Regards

---

### Post by Buntumatic on 2012-01-10
Well, I see several possibilities.

First, you could dress up in black, light six candles in a circle, put that USB drive in the middle and move around that circle jumping three times on left leg and three times on right, jamming uuuh-mmmh.

If that doesn't help, 
a) try copying all mp3 files off that drive and reformat it;
b) open a terminal and run ls -l on it to see what permissions those files have you want to remove, adjust permissions and run rm on them.

---

### Post by imachavel on 2012-01-10
that's all good, but another two things:

1) why do you believe a virus is on your usb drive? If you have a computer with windows, you could put the flash drive into the computer, install malware bytes or ms security essentials, then run scan on the f: drive or whatever it is you are trying to get your files off of, it should tell you if a virus is on it.

2) have you tried copy and pasting the files from one directory to another? Do you try to simply load the mp3 files into a music player from your d: drive? Try putting them into a different directory. Ok how about this? get those permissions, tell us all what they are

3) here is mine:

       ls -l
total 152
-rwxrwxr-x 1 ubuntu ubuntu 113514 2012-01-10 10:12 bootinfoscript
drwxr-xr-x 2 ubuntu ubuntu     80 2012-01-09 18:16 Desktop
drwxr-xr-x 2 ubuntu ubuntu     40 2012-01-09 18:16 Documents
drwxr-xr-x 2 ubuntu ubuntu    100 2012-01-10 12:45 Downloads
drwxr-xr-x 2 ubuntu ubuntu     40 2012-01-09 18:16 Music
drwxr-xr-x 2 ubuntu ubuntu     40 2012-01-09 18:16 Pictures
drwxr-xr-x 2 ubuntu ubuntu     40 2012-01-09 18:16 Public
-rw-r--r-- 1 ubuntu ubuntu  28087 2012-01-10 10:13 RESULTS.txt
drwxr-xr-x 2 ubuntu ubuntu     40 2012-01-09 18:16 Templates
-rw-rw-r-- 1 ubuntu ubuntu    939 2007-10-12 16:52 U710fix.zip
drwxr-xr-x 2 ubuntu ubuntu     40 2012-01-09 18:16 Videos


so weird, there is a boot info script on the drive, but I'm wondering if this is giving me the contents of my flash drive, I'm pretty sure it's not and that it's giving me the contents of wherever the files are loaded from my live cd to. I don't know I guess in the ram or proecessor or wherever all that stuff is cached. Isn't THIS the command you would want?:

 [FONT=monospace]lsusb[/FONT]

---

### Post by dak0 on 2012-01-10
Thank you for reply`s, we solved the problem like this, copied the mp3. files and put them on my hard drive, then deleted everything from the USB and put back mp3 files

---

