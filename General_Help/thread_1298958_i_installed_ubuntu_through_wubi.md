---
title: "i installed ubuntu through wubi"
date: 2009-10-23
forum: General Help
---

### Post by confusedxp on 2009-10-23
i dont erally like it how do i get back to windows because when i dual boot it it automatically goes to ubuntu because i set it back when i was on windows
so where is the ubuntu setting for changing back to windows xp thanks

---

### Post by martrn on 2009-10-23
> **confusedxp said:**
> so where is the ubuntu setting for changing back to windows xp thanks

The settings for changing back is in windoze.  If you visit : [/wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide") :  and scroll down to the section entitled .."..how do I manually uninstall..".. you will find that when running windoze and editing your "C:\boot.ini" file and deleting the Ubuntu/Wubi line should do the trick.

You might need to use your windows recovery disc and boot the windoze cd or pressing some kind of key combination in your boot manager your should be able to change.

Windozse partitions might be available within the directories /host and /media to edit your "boot.ini".

---

### Post by MichaelDance on 2009-10-23
hey mate, well you need to have a cd to re-install FRESH Windows or you can if you can log into windows and remove the spare Drive for ubuntu but i wouldn't fully 100% recommend it. Good luck

---

### Post by lavinog on 2009-10-23
> **MichaelDance said:**
> hey mate, well you need to have a cd to re-install FRESH Windows or you can if you can log into windows and remove the spare Drive for ubuntu but i wouldn't fully 100% recommend it. Good luck

I don't think this is the solution the OP wants.

---

### Post by confusedxp on 2009-10-23
> **martrn said:**
> The settings for changing back is in windoze.  If you visit : [/wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide") :  and scroll down to the section entitled .."..how do I manually uninstall..".. you will find that when running windoze and editing your "C:\boot.ini" file and deleting the Ubuntu/Wubi line should do the trick.

You might need to use your windows recovery disc and boot the windoze cd or pressing some kind of key combination in your boot manager your should be able to change.

Windozse partitions might be available within the directories /host and /media to edit your "boot.ini".

I meant inside ubuntu because i cant even access windows or any safemode etc because im using a usb keyboard
So basically how do i do this inside ubuntu

---

### Post by confusedxp on 2009-10-23
bump

---

### Post by confusedxp on 2009-10-23
bump.

---

### Post by martrn on 2009-10-23
> **confusedxp said:**
> I meant inside ubuntu because i cant even access windows or any safemode etc because im using a usb keyboard
So basically how do i do this inside ubuntu

If you can read your directories /host and /media on ubuntu you can edit your "boot.ini". If you can't do that then you need to boot windowze.  Wubi Wubi installations are stored withinside the windows hard disk drive.  If windowze is on your system then the supergrub disc [www.supergrubdisk.org/]("http://www.supergrubdisk.org/index.php") might be able to boot your windoze disk easily,

---

### Post by fluffman86 on 2009-10-23
Dude, you don't need to post the same question over and over.  And you don't need to bump every 4 minutes.  Give it a break.

Boot into Ubuntu, Go to the "Places" menu, and select the hard drive that Windows is stored on.  It may say "180.0 GB Media" or have a name like "HP_PAVILION"  

Enter your password if necessary, and you should see the files on your C: drive. Scroll down and find "boot.ini"

Here's what mine looks like:
```

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

```

That's mine, and I have Windows installed on partition 2 (see on line 3?) because I have a recovery console (down a few more lines).

So, to fix your problem, if you already have a WINDOWS line on line 3, then make sure that the second line says "timeout=3" so that you have 3 seconds to select windows.

If you DO NOT have a WINDOWS line on line 3, then add one, but DON'T DELETE THE UBUNTU LINE YET.

Let us know what happens.

---

### Post by flipper9 on 2009-10-23
Wow, if I spam the forums and bump every 4 minutes, will my questions get answered quickly too? :mad:

---

