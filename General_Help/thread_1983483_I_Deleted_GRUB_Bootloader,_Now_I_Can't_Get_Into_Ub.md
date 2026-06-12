---
title: "I Deleted GRUB Bootloader, Now I Can't Get Into Ubuntu"
date: 2012-05-20
forum: General Help
---

### Post by Doodling Unity on 2012-05-20
So I Deleted The GRUB Bootloader Because Everytime I Turn On The Computer I Don't Get The DOS, I Get The GRUB, So My Dad Didn't Like That, So I Removed GRUB With a Program Called testdisk, And Now I Can't Boot Into Ubuntu  :oops: 
BTW I'm Using Ubuntu 12.04, The Previous Versions of Ubuntu Booted Into DOS, But 12.04 Boots in GRUB........](*,)](*,)](*,)
Any Help Would Be Appreciated!!
Thanks!! :)

---

### Post by 2F4U on 2012-05-20
Umm, yeah it would be a wonder if you could get into Ubuntu, since you delete what is responsible for booting it. But it is not too difficult to recover grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Doodling Unity on 2012-05-20
> **2F4U said:**
> Umm, yeah it would be a wonder if you could get into Ubuntu, since you delete what is responsible for booting it. But it is not too difficult to recover grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
But I Don't Want GRUB :/
Is There an Another Way To Get Into Ubuntu???

---

### Post by idoitprone on 2012-05-20
> **Doodling Unity said:**
> But I Don't Want GRUB :/
Is There an Another Way To Get Into Ubuntu???

ummmm alll version of ubuntu boots uses  grub to boot

from what I hear, you want to make DOS the default os and boot that first.

there is an alternative to grub lilo bootloader
[http://manpages.ubuntu.com/manpages/lucid/man8/lilo.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/lilo.8.html)

---

### Post by Doodling Unity on 2012-05-20
> **idoitprone said:**
> ummmm alll version of ubuntu boots uses  grub to boot

from what I hear, you want to make DOS the default os and boot that first.

there is an alternative to grub lilo bootloader
[http://manpages.ubuntu.com/manpages/lucid/man8/lilo.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/lilo.8.html)
Does Lilo looks Like grub or does it look DOS-ish

---

### Post by coffeecat on 2012-05-20
What, specifically, is your problem with grub, and what do you mean by DOS? Ubuntu has been using one version or another of grub since for ever. What has changed for you? And what do you mean when you say you removed grub with testdisk? Testdisk is for recovering partitions, not for removing bootloaders, and can cause problems if you don't know how to use it. I wonder if you have done more damage to your system than just removing the bootloader.

---

### Post by Doodling Unity on 2012-05-20
> **coffeecat said:**
> What, specifically, is your problem with grub, and what do you mean by DOS? Ubuntu has been using one version or another of grub since for ever. What has changed for you? And what do you mean when you say you removed grub with testdisk? Testdisk is for recovering partitions, not for removing bootloaders, and can cause problems if you don't know how to use it. I wonder if you have done more damage to your system than just removing the bootloader.

DOS is The Windows Default Bootloader + I Used Testdisk To Remove GRUB.

---

### Post by 2F4U on 2012-05-20
These posts suggests that it seems to be possible to boot Ubuntu from Windows boot loader:

[http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)
[http://www.sevenforums.com/installation-setup/40553-adding-ubuntu-boot-manager.html](http://www.sevenforums.com/installation-setup/40553-adding-ubuntu-boot-manager.html)

But, to be honest, I have no intention to find out if that really works.

---

### Post by wilee-nilee on 2012-05-20
You could use easybcd a app that will place ubuntu in the windows boot loader, but we need to get you into windows first.

Do you have a recovery or install disc for the windows install, and what windows version is it?

Was the ubuntu install that used the windows bootloader installed from windows a wubi install?

As suggested using testdisk to remove grub leaves us all scratching our heads going "what". So  we can use as script to look closer at the whole HD, and boot setups for what may be left.

Using a ubuntu live cd download this link, exstract it to your desktop and run the command. You will see a results.txt appear, copy and paste all the text from the results.txt to a reply.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by gordintoronto on 2012-05-20
You could have configured Grub to do what you want. It's not very difficult.

[http://www.youtube.com/watch?v=UDh0-lWBVdo&feature=g-all-u](http://www.youtube.com/watch?v=UDh0-lWBVdo&feature=g-all-u)

---

### Post by wilee-nilee on 2012-05-20
> **gordintoronto said:**
> You could have configured Grub to do what you want. It's not very difficult.

[http://www.youtube.com/watch?v=UDh0-lWBVdo&feature=g-all-u](http://www.youtube.com/watch?v=UDh0-lWBVdo&feature=g-all-u)

The pixie is quite helpful, but I don't think she does family counselling.

> So I Deleted The GRUB Bootloader Because Everytime I Turn On The  Computer I Don't Get The DOS, I Get The GRUB, So **My Dad Didn't Like  That**, So I Removed GRUB With a Program Called testdisk, And Now I Can't  Boot Into Ubuntu ;)

---

