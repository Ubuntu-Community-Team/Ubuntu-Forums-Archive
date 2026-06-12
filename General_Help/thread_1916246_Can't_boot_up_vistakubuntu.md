---
title: "Can't boot up vista/kubuntu"
date: 2012-01-27
forum: General Help
---

### Post by darnit on 2012-01-27
When installing, I it said something like /dev/hda1 or sda1.

After I restart, the computer only shown _ but nothing else.

I followed "How to restore the Windows Vista or 7 bootloader"

> How to restore the Windows Vista or 7 bootloader

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7.
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

Code:
bootrec.exe /fixboot
Code:
bootrec.exe /fixmbr
Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

Now NTLDR is missing.

I took out the external hard drive and now the operating system not found.


If I install vista again through the recovery disk, will it fix everything?

---

### Post by Quackers on 2012-01-27
Welcome to UF :-)
If you have a Windows installation disc (or repair disc - but not a recovery disc) it may be worthwhile running the automatic startup repair, up to 3 times. That may repair your Windows boot. It should be quicker than re-installing Windows.
But, in answer to your question, yes, it should solve everything. It may over-write any installed Ubuntu system though (depending on how you installed it).

---

### Post by darnit on 2012-01-27
Cheers for answering. Sadly I only have the recovery disk.

---

### Post by Quackers on 2012-01-27
If you do some googling you will find that a repair disc is available for download. You need the version of Windows that is installed and it must be the same architecture (ie 32 bit or 64 bit).
It's not too large a file to download. It is always wise to have a Windows repair disc.

---

### Post by Quackers on 2012-01-27
Does your recovery disc have the Windows repair console available? Most don't but some do. If you have the repair console available you can run the automatic startup repair from there.

---

### Post by darnit on 2012-01-27
(I burned the recovery disk). it came with this.[IMG]http://i.i.com.com/cnwk.1d/i/tr/Eve/figs02142008vista/I.png[/IMG] 

I didn't see Vista in this box [IMG]http://i.i.com.com/cnwk.1d/i/tr/Eve/figs02142008vista/H.png[/IMG]


Edit: No worries anymore. I decided to reinstall windows again. Not sure if ubuntu is for me D:

---

### Post by Quackers on 2012-01-27
That's the automatic startup repair. With Vista highlighted click on NEXT and let it run. If it doesn't fix it first time try again and if necessary a third time. 
I'm not sure that it will fix the NTLDR error but definitely worth a try before using the recovery option, which will wipe everything out.
Good luck! :-)

---

### Post by darnit on 2012-01-27
It didn't show me vista so nothing happened!!

Thank you anyway. (I took the easy way out.)

---

### Post by Quackers on 2012-01-27
Your screenshot show Vista! Isn't that from your system?
Anyway, if you've recovered from your disc it's too late :-)

---

### Post by miasmablk on 2012-01-27
all your have to do is run the utlity..and it will repair your MBR so you can boot back into windows.

---

