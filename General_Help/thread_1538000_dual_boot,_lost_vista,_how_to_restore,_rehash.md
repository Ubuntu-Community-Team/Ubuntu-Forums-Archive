---
title: "dual boot, lost vista, how to restore, rehash"
date: 2010-07-24
forum: General Help
---

### Post by sepdna42 on 2010-07-24
There are way too many answers from archives on this so I decided to ask it again to maybe remove the confusion, for me and others.

I had Vista and Ubuntu as dual boot, something ate my Vista doc settings folder (probably me).  I want to reinstall it.  It won't because of the set up in the grub I guess.  I am not a serious Linux command line person but do follow directions well.  Is there some somewhat easy way for me to restore my Vista?

I am aware of Win 7 etc.  I have a Dell laptop so want to use the Dell restore CD.  I am not alone in this.  I run into people all over with a similar problem.  HELP!!!

---

### Post by BigCityCat on 2010-07-24
I have no idea what you are asking. I'm sure a lot of others feel the same way.

If you installed over the top of vista, then your screwed. If you installed side by side and Vista isn't showing up in grub then try this.

[http://ubuntuforums.org/showpost.php?p=8008800&postcount=3](http://ubuntuforums.org/showpost.php?p=8008800&postcount=3)

---

### Post by BigCityCat on 2010-07-24
What does ate my vista mean in technical terms?

---

### Post by spydeyrch on 2010-07-24
Correct me if I am wrong. I think that I understand you.

You originally had vista OEM installed. Then added another partition to install Ubuntu.

After installing ubuntu, you had a dual boot system: Vista and Ubuntu. GRUB was your boot menu.

Now, for some reason or another, something in Vista is not working correctly. (Can you still boot into Vista?)

You want to reinstall Vista and not Win7 because your machine came with the manufacturer's restore disk, which is based on Vista. Therefore, why purchase a new OS when you currently have the one that came with your system.

Yet you are running into an issue where the Vista restore install doesn't want to proceed and you think that it is due to GRUB, right?

Well, I see a couple things that might bee an issue here. And correct me if I am wrong anyone that knows better than I do. :D

If you use the Vista restore CD, I believe that it will install Vista to your HDD as it was the moment that you got it. That means that all the bloatware from the manufacturer will be present, all your settings will be lost, any programs you have currently installed will be gone (unless they came with the system). But the biggest thing is that the restore CD typically wipes clean the entire HDD for use by the OEM OS. This means that, if you have a dual partition single HDD, then you would lose your ubuntu install too.

I could be wrong but that is how I remember a restore CD works. It might give you an option to use a particular partition during setup/install but again, I am not exactly sure as I think that last OEM restore CD that I had and actually used was for Win98. Since then, I have always built my own systems and bought my own copy of the OS.

Let me know if I understood you correctly or if I was completely off. :o

-Spydey :KS

---

### Post by sepdna42 on 2010-07-25
Thanks, you are 100% accurate!  I too always built my own and just paid for an original from MS before I put software on.

Well dammit,  I have an MS copy of XP I bought some time ago I wonder if I can install it on the NTFS partition.  I have all my software from mfr anyhow although of late I have been using Ubuntu so much I can live without all of it.  And the Ubuntu reads the MS partition anyhow.  I can live without it  I just don't wanna loose the good files I have on the NTFS.  Looking like it is gonna be a straight up Linux box from here on . . .

Thanks

---

### Post by spydeyrch on 2010-07-26
> **sepdna42 said:**
> Thanks, you are 100% accurate!  I too always built my own and just paid for an original from MS before I put software on.

Well dammit,  I have an MS copy of XP I bought some time ago I wonder if I can install it on the NTFS partition.  I have all my software from mfr anyhow although of late I have been using Ubuntu so much I can live without all of it.  And the Ubuntu reads the MS partition anyhow.  I can live without it  I just don't wanna loose the good files I have on the NTFS.  Looking like it is gonna be a straight up Linux box from here on . . .

Thanks

You could install XP in place of Vista and thereby chose which partition to install it to. You wouldn't lose your ubuntu partition or its files but, you would loose access to Ubuntu until you repaired GRUB via a live CD. So you would have to get into the terminal but the instructions are pretty simple to follow.

Or you could use Gparted and expand your ubuntu partition to take over your vista partition.

Dos your HDD have a third partition known as a recovery partition?

-Spydey :KS

---

