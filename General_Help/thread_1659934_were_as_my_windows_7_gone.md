---
title: "were as my windows 7 gone??"
date: 2011-01-04
forum: General Help
---

### Post by charlie111 on 2011-01-04
hi new to ubuntu. - windows 7 hp pc. 5gig memory.
i bought my nephew hacking the art of exploitation book, this came with a disc.
he put the disc in and left pc on over night.
next day ubuntu was the o/s.
checked which version of ubuntu 7.4?, which i read is no longer available?.
i tried to install the latest version, but sadly not been allowed to do anything??.
no install or download in fact not much happening on this pc.
can't get back into windows 7, can't reply to emails ??.
have checked with hp who inform me no disc provided, should of been burned to disc.
only way to open pc is via the hacking disc which i can't take out until i close down??.
this pc is 8 months old under warranty but hp say i need to contact pc world, to see if they can send windows 7recovery disc.:confused:
pc was bought for nephew by his cousin, who does'nt have the receipt. 
so much for happy new year.
can anyone plz advise on were i go next. to find windows 7o/s  :confused:

---

### Post by cchhrriiss121212 on 2011-01-04
Your nephew has installed Ubuntu, so you will have to ask him what he did. It could be that he wiped the entire hard drive or only used a portion of it.
Ubuntu 7.04 is old, but it should still work OK for the time being.

A restore disk would be the best option I think, so do try contacting the place you bought it from if you don't have one.

---

### Post by Fxkrait on 2011-01-04
I have a bad feeling that your cousin did a clean install on your hard drive, which means that windows is gone.

---

### Post by lidex on 2011-01-04
If windows is still intact, you can follow the links in this post to download a rescue disk:
[http://art.ubuntuforums.org/showpost.php?p=10275896&postcount=59](http://art.ubuntuforums.org/showpost.php?p=10275896&postcount=59)

---

### Post by MARP1961 on 2011-01-04
Things might not be as seriously messed up as you think. Unless someone intentionally let the Ubuntu disk delete the Windows 7 installation it is probably still there. If your computer will not boot normally, then you can try using an Ubuntu disk to see what has happened. You really need a more current version. Ubuntu 10.04 or 10.10 Live CDs can be burned easily from a free download on a borrowed computer (just Google 'Ubuntu Download' and follow instructions). When you have your free CD, just put it into the disk drive before you switch on. Your computer will most likely boot from the CD and you can follow the steps as if you are installing Ubuntu. During the preparation, the disk will find any Windows installation that is still on your hard drive. It will then give you options. You can proceed with letting Ubuntu install 'side by side' or even replacing Windows completely. If you lose your nerve, you can just 'have a look' and see if Windows is still there and then stop before installing. If Windows has been deleted you can take the opportunity to install a fresh Ubuntu operating system and enjoy the adventure that will unfold.

---

### Post by Joe of loath on 2011-01-04
I'm pretty sure Ubuntu just booted into live CD mode as default back then.

Reboot it with the CD out and see what happens.

---

### Post by charlie111 on 2011-01-05
not allowing me to reboot, no safe mode screen, can only get ubuntu with disc in thats hacking disc that is which as ubuntu on it. 
As i said can't download anything.
Its showing top tool bar that i'm not connected to internet, but i can get into internet, not sure how that happens, is it through windows in background??.
Trying to contact pc world when nephews cousin finds receipt?.

---

### Post by Joe of loath on 2011-01-05
PC world won't do anything, or they'll charge a ridiculous fee for reinstalling windows, whether it needs it or not.

Try this.

Hold down the eject button on the CD drive for 10 seconds, the tray should open. Take the disc out and bin it, it's pretty much useless since it's almost 4 years old. Then hold down the power button for 10 seconds, and the PC will turn off. Turn it back on, and see what it does.

I can't see how it installed Ubuntu automatically, it has safeguards to stop you doing that.

---

### Post by Mark Phelps on 2011-01-05
First thing you need to know is if the Win7 partition(s) are still present on the drive.  To find out, boot into Linux, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one".  That will list the partitions on your drive. If you still have NTFS partitions, there's a good chance that Win7 is still there and intact.

Next, if you have a Places entry in your menu system, open that and select the partition for Win7.  That will mount and open that partition.  Then, look through it to see if the directories and files are still present.  IF they are, that is good news.

If you simply want to get back into Win7, use the link that lidex posted to download and burn a Win7 Recovery/Repair CD.  Once you have that, boot from it and run Startup Repair three times -- that's right, three times.

IF it works, it will restore your Win7 boot capabilities.

---

### Post by charlie111 on 2011-01-06
Thanks for all your replies.
Sadly nothing seems to work.
One thing thats i find strange no windows 7 showing anywhere,  can only get on line throught ubuntu via mozilla firefox.
when ubuntu opens 2 monitors showing with red x.
i have tried to connect to internet after clicking on them, nothing happens [theres a surprise].
My question is were and how am i connecting to internet.?????, i know i click on mozilla firefox, and internet comes up.?

---

### Post by Dans564 on 2011-01-06
1st, its not a "hacking disc" its an install cd for Ubuntu 7.04, which is an OS, just like how windows 7 is an OS.  Windows 7 is not running in the background.  You need to find your windows 7 install dvd and reinstall windows 7.

---

### Post by Joe of loath on 2011-01-06
Have you tried what I suggested? It seems highly implausible that Ubuntu installed without any outside assistance.

What happens when you reboot **without** the Ubuntu CD in the CD drive?

---

### Post by charlie111 on 2011-01-06
without the hacking disc it takes u to ubuntu asking for user name and password.
theres no safe mode even continually clicking f8 etc.tried to upgrade to latest ubuntu wont allow wont allow anything.

---

### Post by Joe of loath on 2011-01-06
Oh, so it did install?

To get windows back you'll need a windows recovery disc. You won't be able to get to safe mode, because windows isn't installed any more.

You could probably borrow a friend's install disc and use the key from the COA sticker on the PC.

---

