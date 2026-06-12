---
title: "Sound Blaster X-Fi Xtreme Gamer Fatal1ty"
date: 2009-08-23
forum: General Help
---

### Post by The Living Homer on 2009-08-23
Hi there everyone. This is my first post on the forums and I just started using Ubuntu 9.04 x64. I'm not familiar with Linux at all and came here for some help (obviously). The following link are the drivers that I need for my sound card. ( [http://support.creative.com/downloads/download.aspx?nDownloadId=10792](http://support.creative.com/downloads/download.aspx?nDownloadId=10792) ). When I go to download the drivers for this sound card, it comes downloaded as a .tar.gz file extension. I can open it with 7-zip and there is a folder followed by several different types of files. I have no clue on how or what to install from all of these files. If someone could please tell me how to get this working properly, I would greatly appreciate it. Thanks in advance for the help.

[CENTER]The Living Homer. :)

[LEFT]*NOTE* I've attached the file to this thread so everyone will know what I'm talking about.
[/LEFT]
[/CENTER]

---

### Post by Diskotekno on 2009-08-23
Hi,

Extract the archive onto your desktop and open up the terminal and navigate to the folder you just extracted and type: sudo make , when that completes type sudo make install 

After that reboot and you should have sound....

---

### Post by The Living Homer on 2009-08-23
This may sound extremely stupid but, how would I navigate to the folder in the terminal?

---

### Post by j.bell730 on 2009-08-23
> **The Living Homer said:**
> This may sound extremely stupid but, how would I navigate to the folder in the terminal?

```
cd name-of-folder
```

EDIT-
If the folder is in a different directory, such as your desktop, open a terminal and type:
```
cd ~/Desktop/name-of-folder
```
**cd** - Stands for change directory.
**~** - Your home directory.
**Desktop** - The desktop directory :P.
**name-of-folder** - Variable, could be named anything. Make sure to press Tab to help you out before you type this part.

---

### Post by The Living Homer on 2009-08-23
Thanks very much to both of you. It works perfectly now.

---

### Post by absolute linux noob on 2009-09-11
Hi i had the same problem and attempted to use the same fix but got an Error 1

andre@andre-desktop:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
make -C /lib/modules/2.6.28-15-generic/build M=/home/andre/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
andre@andre-desktop:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
FATAL: Error inserting ctxfi (/lib/modules/2.6.28-15-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
andre@andre-desktop:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 


any advice? Thanks

---

### Post by The Living Homer on 2009-09-11
Now I installed it and it says it's installed but I still have no sound. Now I really don't know.

---

