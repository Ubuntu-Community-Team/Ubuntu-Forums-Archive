---
title: "is wubi full install of ubuntu?"
date: 2012-05-20
forum: General Help
---

### Post by ytkuser12 on 2012-05-20
HI all i want to try out ubuntu and use it as a duel boot. but i'm not tech savvy and don't want to mess up my hard drive so i saw this cool wubi install for windows. What i was wondering is this full version ubuntu like can i install my video card drivers for this version of ubuntu?. can i install programs and native drives for it?. also how will my internal sound card work with it?. will i need to install drivers for it as well. My sound card is just realtek there is a linux/unix driver for it. if anyone can help would be awesome. also will my wireless Logitech kyb and mouse work with ubuntu?. or will i need drivers for it as well. thanks in advance and god bless.

---

### Post by wilee-nilee on 2012-05-20
> **ytkuser12 said:**
> HI all i want to try out ubuntu and use it as a duel boot. but i'm not tech savvy and don't want to mess up my hard drive so i saw this cool wubi install for windows. What i was wondering is this full version ubuntu like can i install my video card drivers for this version of ubuntu?. can i install programs and native drives for it?. also how will my internal sound card work with it?. will i need to install drivers for it as well. My sound card is just realtek there is a linux/unix driver for it. if anyone can help would be awesome. also will my wireless Logitech kyb and mouse work with ubuntu?. or will i need drivers for it as well. thanks in advance and god bless.

Yes it is a full install, and uses all the hardware like a partitioned dualboot, except the grub bootloader. It is just a file in windows though so if used like any OS backups are your best insurance.

Wubi was designed as a try it and if you like then install ubuntu to a partition. Some though use it longer term due to limitations, or a fear of a partitioned install it is your choice.

---

### Post by ytkuser12 on 2012-05-20
so will i need to install my video card drivers? and sound drivers?

---

### Post by wilee-nilee on 2012-05-20
> **ytkuser12 said:**
> so will i need to install my video card drivers? and sound drivers?

Chances are Ubuntu will do that automatically, you would generally not use any windows drivers in Ubuntu.

---

### Post by ytkuser12 on 2012-05-20
ok cool just asking cause there are linux drivers for my vid card and sound drivers.

---

### Post by wilee-nilee on 2012-05-21
> **ytkuser12 said:**
> ok cool just asking cause there are linux drivers for my vid card and sound drivers.

Always better to be informed for sure. :)

---

### Post by ytkuser12 on 2012-05-21
yup :) will install tomorrow and check it out if i like it i will try and get help to install on partition :).

---

### Post by ytkuser12 on 2012-05-21
a friend of mine suggested i just install ubuntu on its own partition. i was reading that ubuntu creates it's own partition if so is it as simple as putting in a bootable usb which i have experiences in making and hitting install?. is it pretty much push button?.

---

### Post by sammiev on 2012-05-21
It usually is but you can boot from the USB and try it live first. Then from that screen you can install it all seems to work well. :)

---

### Post by wilee-nilee on 2012-05-21
> **ytkuser12 said:**
> a friend of mine suggested i just install  ubuntu on its own partition. i was reading that ubuntu creates it's own  partition if so is it as simple as putting in a bootable usb which i  have experiences in making and hitting install?. is it pretty much push  button?.

Hmm, I would ask the friend to show you how, advice without a solution is well not very good advice. A dual boot can be a plug and play so to speak, but many are not, due to a maximum amount of primary partitions already on a single HD, and other anomalies.

---

### Post by ytkuser12 on 2012-05-21
> **wilee-nilee said:**
> Hmm, I would ask the friend to show you how, advice without a solution is well not very good advice. A dual boot can be a plug and play so to speak, but many are not, due to a maximum amount of primary partitions already on a single HD, and other anomalies.

he has no experience with Linux but he said he would think installing it with wubi would make it vulnerable to windows viruses and such so he recommended i install it on it's own partition is all.  i only have one OP installed and that's windows 7 it resides on my single HD drive. which is 500 GB i have 337 GB free of it. i admit i'm a new to all this for sure.

---

### Post by wilee-nilee on 2012-05-21
> **ytkuser12 said:**
> he has no experience with Linux but he said he would think installing it with wubi would make it vulnerable to windows viruses and such so he recommended i install it on it's own partition is all.  i only have one OP installed and that's windows 7 it resides on my single HD drive. which is 500 GB i have 337 GB free of it. i admit i'm a new to all this for sure.

Windows virus's wont run in linux. I would go with the wubi while you learn about dual booting in a partitioned setup. The wubi can be moved to a partition in the end there is a thread just on that on the forums.

I suggest this as some people don't like linux, and doing a dual boot if you have a OEM=manufacturers install of windows may include removing partitions and a bit of a juggling act, that when knowing how is easy, but not for a first time try. 

That is a personal opinion though.

People on the forum will help you though in whatever you want to do,  just be sure to have a full image of the Windows main OS off the computer, and the rest of anything you can not lose in a safe place as well.

---

### Post by ytkuser12 on 2012-05-21
ok i will take your advice your more knowledgeable in linux and this area then he is thanks :)

---

### Post by ytkuser12 on 2012-05-22
i love it been in it all day and playing around i like it. i only wish i could get it to play all my blu-ray's but cant figure that out. if i could i just might make the switch full.

---

### Post by bcbc on 2012-05-23
[http://www.omgubuntu.co.uk/2012/02/how-to-install-vlc-2-0-in-ubuntu-10-04-11-10/](http://www.omgubuntu.co.uk/2012/02/how-to-install-vlc-2-0-in-ubuntu-10-04-11-10/)

This states 'experimental BluRay support'. I've got it working before, just can't remember exactly how (!). Ubfortunately I overwrote that install... but it was probably vlc

You probably want to install [ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats") as well (if you haven't already).

Edit: I just tried it with VLC. Didn't work this time - might be a different bluray disc (apparently that can make a difference). So whatever I did before, it's obviously not that straightforward.

---

### Post by ytkuser12 on 2012-05-23
> **bcbc said:**
> [http://www.omgubuntu.co.uk/2012/02/how-to-install-vlc-2-0-in-ubuntu-10-04-11-10/](http://www.omgubuntu.co.uk/2012/02/how-to-install-vlc-2-0-in-ubuntu-10-04-11-10/)

This states 'experimental BluRay support'. I've got it working before, just can't remember exactly how (!). Ubfortunately I overwrote that install... but it was probably vlc

You probably want to install [ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats") as well (if you haven't already).

Edit: I just tried it with VLC. Didn't work this time - might be a different bluray disc (apparently that can make a difference). So whatever I did before, it's obviously not that straightforward.

i got it to work i guess it docent play BD+ but as long as it plays most. i followed these instructions here. [http://ubuntuforums.org/showthread.php?t=1967280&highlight=blu-ray](http://ubuntuforums.org/showthread.php?t=1967280&highlight=blu-ray)  my only concern now is i stream Netflix but not from my PC but i log in on my computer to check my account and settings. i know you cant stream Netflix on Linux. but will i still be able to change my account settings and monitor my account?.

---

### Post by bcbc on 2012-05-23
> **ytkuser12 said:**
> i got it to work i guess it docent play BD+ but as long as it plays most. i followed these instructions here. [http://ubuntuforums.org/showthread.php?t=1967280&highlight=blu-ray](http://ubuntuforums.org/showthread.php?t=1967280&highlight=blu-ray)  my only concern now is i stream Netflix but not from my PC but i log in on my computer to check my account and settings. i know you cant stream Netflix on Linux. but will i still be able to change my account settings and monitor my account?.

Cool thanks for the tip. I'll check it out.

Best way to check Netflix is to just see if it works. I don't see why they'd need something special for account management. Just the streaming with silverlight that requires drm.

---

### Post by ytkuser12 on 2012-05-23
> **bcbc said:**
> Cool thanks for the tip. I'll check it out.

Best way to check Netflix is to just see if it works. I don't see why they'd need something special for account management. Just the streaming with silverlight that requires drm.

cool i can check my account stuff :) this weekend i think i might take the plunge and get out of Microsoft world all together :). lighter faster and the looks are better i like ubuntu. i'm defenatly going to have to ether duel boot install it like that or just ditch windows and install it full. the whey it's installed now sometimes hangs lol.

---

### Post by bcbc on 2012-05-23
> **ytkuser12 said:**
> cool i can check my account stuff :) this weekend i think i might take the plunge and get out of Microsoft world all together :). lighter faster and the looks are better i like ubuntu. i'm defenatly going to have to ether duel boot install it like that or just ditch windows and install it full. the whey it's installed now sometimes hangs lol.

Cool. I need Windows for work. But that also allows me to test wubi, which by the way shouldn't hang (at least, it's not likely because of wubi; check your logs for any errors). If it does hang completely use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") to safely reboot.

PS if you are going to overwrite Windows, I'd recommend creating restore disks - since you paid for it with the comp, you might as well.

EDIT: another thing - take your time before you decide... if you've just started using Ubuntu you should consider waiting say a month. Use Ubuntu exclusively and make sure before you wipe out Windows. You can easily shrink down windows and keep it as a dual boot. Just in case.

---

### Post by wilee-nilee on 2012-05-23
> **bcbc said:**
> Cool. I need Windows for work. But that also allows me to test wubi, which by the way shouldn't hang (at least, it's not likely because of wubi; check your logs for any errors). If it does hang completely use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") to safely reboot.

PS if you are going to overwrite Windows, I'd recommend creating restore disks - since you paid for it with the comp, you might as well.

+1 
I would leave the dual boot myself, but I use it so I can help windows users, but having a image is a good thing.

---

### Post by tumutanzi.com on 2012-05-23
Another point is that the performance of hard disk is a bit lower in the case of Wubi installation.

---

### Post by ytkuser12 on 2012-05-23
yeah notest that i might get somone to install it for me. i do only have one thing installed and thats windows 7. i installed it myself was a upgrade from vista that i installed myself as well. so not sure how hard ubuntu would be to put on.

---

### Post by Dave_in_MD on 2012-05-23
> **ytkuser12 said:**
> yeah notest that i might get somone to install it for me. i do only have one thing installed and thats windows 7. i installed it myself was a upgrade from vista that i installed myself as well. so not sure how hard ubuntu would be to put on.

If you are nervous but want to try to install yourself, get another hard drive, disconnect your current hard drive and install to the new drive. Ubuntu is pretty much hands off on the install once you tell it where, and who, you are and give it a password. If the install fails, quite unlikely, just swap your cable back to the other hard drive and you are back up and running.

---

### Post by ytkuser12 on 2012-05-23
> **Dave_in_MD said:**
> If you are nervous but want to try to install yourself, get another hard drive, disconnect your current hard drive and install to the new drive. Ubuntu is pretty much hands off on the install once you tell it where, and who, you are and give it a password. If the install fails, quite unlikely, just swap your cable back to the other hard drive and you are back up and running.

can i keep the install to another HD will i be able to boot from that like a duel boot? if so i might go this way as hard drives are not to bad in price these days.

---

### Post by wilee-nilee on 2012-05-23
> **ytkuser12 said:**
> can i keep the install to another HD will i be able to boot from that like a duel boot? if so i might go this way as hard drives are not to bad in price these days.

Yep grub can be in the master boot record of the 2nd HD the mbr, it will show Ubuntu and windows in the grub menu. Feel free to ask us about the install so we can get it done without grub being put in the windows HD's mbr, that can all be repaired but better avoided in general.

You can transfer that wubi to the second HD as well then I believe it loads the mbr for you here is a link. You can then expand that partition as big as you want.

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

link in the link

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by ytkuser12 on 2012-05-23
> **wilee-nilee said:**
> Yep grub can be in the master boot record of the 2nd HD the mbr, it will show Ubuntu and windows in the grub menu. Feel free to ask us about the install so we can get it done without grub being put in the windows HD's mbr, that can all be repaired but better avoided in general.

You can transfer that wubi to the second HD as well then I believe it loads the mbr for you here is a link. You can then expand that partition as big as you want.

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

link in the link

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
cool i have a older 250 gb IDE hard drive that might be ok for this i will have to check it out and also see if my mainboard has a ide plug lol. i think it might all be sata not sure.

---

### Post by wilee-nilee on 2012-05-23
> **ytkuser12 said:**
> cool i have a older 250 gb IDE hard drive that might be ok for this i will have to check it out and also see if my mainboard has a ide plug lol. i think it might all be sata not sure.

Cool bcbc has commented, so I would let them comment on this part if the ide works, with a transfer since the wubi is in a sata as of now, not sure if that is a problem, probably not, but yah never know. Mainly a sata set up to ide is my curiosity, with a wubi.

---

### Post by ytkuser12 on 2012-05-23
> **wilee-nilee said:**
> Cool bcbc has commented, so I would let them comment on this part if the ide works, with a transfer since the wubi is in a sata as of now, not sure if that is a problem, probably not, but yah never know. Mainly a sata set up to ide is my curiosity, with a wubi.

i have a usb that has a install for ubuntu itself most likely start from fresh on that drive.

---

### Post by wilee-nilee on 2012-05-23
> **ytkuser12 said:**
> i have a usb that has a install for ubuntu itself most likely start from fresh on that drive.

cool, enjoy. :)

---

### Post by Dave_in_MD on 2012-05-24
> **ytkuser12 said:**
> cool i have a older 250 gb IDE hard drive that might be ok for this i will have to check it out and also see if my mainboard has a ide plug lol. i think it might all be sata not sure.

you can get PATA to SATA converters such as: [http://www.microcenter.com/single_product_results.phtml?product_id=0287131](http://www.microcenter.com/single_product_results.phtml?product_id=0287131)

The method I meant for 2 drives was not a dual boot but two totally independent installs, neither OS knowing about the other.  If your  BIOS supports boot priority, it should with SATA drives, you can make a different type of dual boot. where you enter the BIOS to choose.  Works for me as I will use the box as Ubuntu pretty much exclusively. no matter what you may do to either OS it will have no affect on the other.

---

### Post by ytkuser12 on 2012-05-27
cool just did the install went painless now i need to find this file and i cant? were is it located i want to watch blurays.  Linux 64bit: put that file in VLC folder (or in LD_LIBRARY_PATH, usually /usr/lib64/) i find the /usr/lib file but not the lib64? any help appreciated thanks. got it to work i places it in the usr/lib folder works now :)

---

