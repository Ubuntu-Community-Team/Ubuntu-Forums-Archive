---
title: "Can't read or write to Android phone - ICS"
date: 2012-05-10
forum: General Help
---

### Post by Xero Xenith on 2012-05-10
I have a Samsung Galaxy SII and upgraded it to Android 4.0 today. When I plug it in, it's instantly recognised and my files show up perfectly (using MTP).

However, an error appears whenever I try and access a file, and whenever I try to create one or transfer one over. In other words, it lists them perfectly, but I can't do anything else!

Is there a way this can be done in Nautilus or do I have to go through all the special MTP setup?

Many thanks in advance :)

EDIT: I'm on 12.04 Precise 64-bit Ubuntu.

EDIT: two solutions posted.

Easy one that requires you to do things each time you connect:
> **lile001 said:**
> This worked for my Galaxy SII:

[http://www.tuxtrix.com/2011/07/how-to-access-samsung-galaxy-s-ii-usb.html](http://www.tuxtrix.com/2011/07/how-to-access-samsung-galaxy-s-ii-usb.html)

```
1. On Galaxy S II , go to
Menu -> Settings -> Wireless and network -> USB utilities 
2. Click on Connect Storage to PC
3. Connect the USB cable to your pc.
4. Click on Connect USB storage
5. Use your file manager to install/copy/paste.
6. Once finished, click on Disconnect storage from PC to disconnect and unmount drive from Ubuntu.
```

Very simple!

Hard techie one that sorts it out once-and-for-all:
> Ah, I found a fix for this and forgot to update. MTP still doesn't work but I found flashable zip that forces it to use USB Mass Storage (so I can't test MTP easily any more, AFAIK). For anyone interested here it is, but your phone needs to be ROM'ed (CF-Root; basically read the thing there):

[http://forum.xda-developers.com/showpost.php?p=23880938&postcount=35](http://forum.xda-developers.com/showpost.php?p=23880938&postcount=35)

---

### Post by mordak13 on 2012-05-24
I know this isn't the fix you were hoping for but to transfer files to and from my Ubuntu laptop,  I use SSHDroidPro or a program like SwiFTP start an SSH server session or an FTP server session and login that way. Saves needing a cable too.

---

### Post by vandorjw on 2012-05-24
I have Samsung Nexus S ICS and it works fine.
Is it possible to transfer files when using another computer? (windows?)

Are you mounting your SD card after it says USB connected. (click here to mount SD)

As far as I know, there is no special filesystem that Ubuntu is unable to read, but I could be wrong..

---

### Post by Xero Xenith on 2012-05-24
Ah, I found a fix for this and forgot to update. MTP still doesn't work but I found flashable zip that forces it to use USB Mass Storage (so I can't test MTP easily any more, AFAIK). For anyone interested here it is, but your phone needs to be ROM'ed (CF-Root; basically read the thing there):

[http://forum.xda-developers.com/showpost.php?p=23880938&postcount=35](http://forum.xda-developers.com/showpost.php?p=23880938&postcount=35)

---

### Post by lile001 on 2012-06-10
This worked for my Galaxy SII:

[http://www.tuxtrix.com/2011/07/how-to-access-samsung-galaxy-s-ii-usb.html](http://www.tuxtrix.com/2011/07/how-to-access-samsung-galaxy-s-ii-usb.html)

```
1. On Galaxy S II , go to
Menu -> Settings -> Wireless and network -> USB utilities 
2. Click on Connect Storage to PC
3. Connect the USB cable to your pc.
4. Click on Connect USB storage
5. Use your file manager to install/copy/paste.
6. Once finished, click on Disconnect storage from PC to disconnect and unmount drive from Ubuntu.
```

Very simple!

---

