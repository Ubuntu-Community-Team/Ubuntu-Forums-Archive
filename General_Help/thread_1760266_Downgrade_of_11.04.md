---
title: "Downgrade of 11.04"
date: 2011-05-16
forum: General Help
---

### Post by Mudi_ on 2011-05-16
Hi guys 

I upgraded to Ubuntu 11.04 and I don't like it because there have been too many problems. I would like to downgrade to 10.10 and I want to know how to do this safely because I have a dual boot. I installed it inside Windows. (I read something goes wrong during startup if you uninstall it the wrong way)

Also I have the installation on CD and I was wondering if there was a way to use it during the downgrade instead of downloading other files because I don't have that much bandwidth left for this month.

Thanks in advance

---

### Post by r-senior on 2011-05-16
You can't downgrade. You can only backup your /home and reinstall.

Are the problems with usability of the Unity interface? If so, you can switch to the "Classic" desktop.

If there are other problems, I'd suggest posting them and seeing if there are solutions. Or have you done that already and got nowhere?

---

### Post by Mudi_ on 2011-05-16
Ok how do I uninstall Ubuntu 11.04?
And I have got problems that I looked up and got nowhere :\

---

### Post by mr clark25 on 2011-05-16
> **Mudi_ said:**
> And I have got problems that I looked up and got nowhere :\


what are these problems? if they are related to the desktop environment, you can revert to the old one as r-senior said. if it is more they are not all desktop environment related, we might still be able to help.

---

### Post by linuxuser12345 on 2011-05-16
Okay, to uninstall 11.04, make a LiveCD of an older version (like 10.10 or 10.04.2), and boot it up. Click "install", and tell it to remove everything on your hard drive.

WARNING: Back up your files before you do this.

---

### Post by Mudi_ on 2011-05-16
Well to start there is a problem when I open too many windows. They start showing up blank and I can only see the contents when I resize them. Also I cannot install Python IDLE 2.6.6 (I need it for school) and the interface is all bleh.

---

### Post by Cfhs_1 on 2011-05-16
Yea, linuxuser12345 has it right. Just make sure you back up your data, easiest way to do this is to just copy the whole /home/USERNAME folder to an external location like a flash drive or external HDD or maybe even your WINDOWS partition. (less safe)This should be a fairly straight forward process. That is unless you installed ubuntu using WUBI?

---

### Post by Mudi_ on 2011-05-16
Well I downloaded an ISO image, and installed it inside windows. And what do you mean, will my whole hard drive be wiped ? :S

---

### Post by linuxuser12345 on 2011-05-16
Just tell it to replace the Ubuntu 11.04 portion. You should be good to go! (thumbs up!)

---

### Post by Cfhs_1 on 2011-05-16
This may actually be a bit difficult since you are in a WUBI install. There are no actual partitions to just reinstall to since WUBI is basically just some files that reside within the windows partition. At this point rhe best bet would be to back up your data first, then delete your WUBI install through add/remove in windows. Finally do a full install by rebooting your computer while the ubuntu disc is in your CD drive. It should boot off the CD automatically, iff not you're gonna have to change your BIOS settings, this is different for most computers, so just google it. once you get all that straightened out select "install" when it gives you the option, and when it asks about where to install to, choose the "guided" option. This will resize your windows partition, and install ubuntu along side it in it's own partition. This will be a traditional dual boot setup. Finally just copy your files back over, and enjoy! :popcorn:

Hope this helps,
NCB

---

### Post by Mudi_ on 2011-05-18
> **Cfhs_1 said:**
> ...delete your WUBI install through add/remove in windows. ...

It's not in the list :s and sorry for the late reply

---

### Post by Cfhs_1 on 2011-05-18
> **Mudi_ said:**
> It's not in the list :s and sorry for the late reply

It's all good, try this uninstaller:
[https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe)

---

### Post by Mudi_ on 2011-05-18
> **Cfhs_1 said:**
> It's all good, try this uninstaller:
[https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe)

Thanks. I tried it and it took only a couple of seconds and at the end it said Wubi has been uninstalled. Was that what was supposed to happen? 
Also the C:\ubuntu folder is still there

---

### Post by Cfhs_1 on 2011-05-18
> **Mudi_ said:**
> Thanks. I tried it and it took only a couple of seconds and at the end it said Wubi has been uninstalled. Was that what was supposed to happen? 
Also the C:\ubuntu folder is still there

Yea, that's what it's supposed to do. Now you can delete the C:/ubuntu folder if you want. Next just preform a true dual boot install like I explained a few posts ago. It should be a fairly straight forward process.

:popcorn:

---

### Post by Mudi_ on 2011-05-18
> **Cfhs_1 said:**
> ... Finally do a full install by rebooting your computer while the ubuntu disc is in your CD drive. ...
You mean to install Ubuntu and wipe my hard drive ? :s Sorry I'm not that good with computers

---

### Post by Mudi_ on 2011-05-19
Ok well anyways I reinstalled it using wubi again, and when I rebooted it so it could finish the installation, I got a black screen. The monitor just shut off, I even tried continuing the setup in safe graphics mode. Is this a problem with my graphics card?

---

### Post by Cfhs_1 on 2011-05-19
> **Mudi_ said:**
> Ok well anyways I reinstalled it using wubi again, and when I rebooted it so it could finish the installation, I got a black screen. The monitor just shut off, I even tried continuing the setup in safe graphics mode. Is this a problem with my graphics card?

Try this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

