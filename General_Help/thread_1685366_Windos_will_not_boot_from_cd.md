---
title: "Windos will not boot from cd?"
date: 2011-02-10
forum: General Help
---

### Post by ledwardz on 2011-02-10
Hey. Ive completley changed to ubuntu 10.10 but i can't use my printer and so need to go back to xp, vista or win 7 ( i have the disks for all of them).  When i insert the windows 7 disk i get a message saying "can't boot from disk code 5"
Windows vista and xp both come up with press any key to boot from cd and then loads ubuntu.

I got my laptop back to windows by loading up vista then deleting the partitions and rebooting windows. I think it would be great if someone would maybe put this in a massive form so that newbies like me don't have to waste a week of their lives trying to figure it out. 

Ive also tried disk utility but wont reformat any of the hardrive probably because im using it. I was gunna try boot in safemode then reformat but cudn't find any mention on how to do this anywhere. Dont get me started on Gparted that thing is usless or i dunno maybe i'm useless probably the second opinion is right. :(

 I'm at the end of the line with this now, Its driving me nuts. Any help for a newbie (please try and keep it simple im no computa wizz) is much appreciated. Thanks, Lee.

---

### Post by dabl on 2011-02-10
From your friends at Google:

[http://forums.speedguide.net/showthread.php?249387-Windows-7-cannot-boot-from-CD-code-5&p=2294125&viewfull=1#post2294125](http://forums.speedguide.net/showthread.php?249387-Windows-7-cannot-boot-from-CD-code-5&p=2294125&viewfull=1#post2294125)

and (see last post)

[http://forums.cnet.com/7723-7591_102-325608.html](http://forums.cnet.com/7723-7591_102-325608.html)

---

### Post by 3Miro on 2011-02-10
If your windows CD doesn't boot, it is a problem with your windows CD. A boot CD takes over your system long before anything from Ubuntu has a chance to load/start. For more information on this issue, you can refer to Microsoft/Windows vendor/Windows Forum.

As for formatting your hard-drive. Formating completely erases all information on it, hence you cannot format a drive while you are using it (with any operating system). You can use an Ubuntu CD, boot from it and then use Gparted to format anything (when you use a live CD the hard-drive is not being used). Note that if you reformat your hard-drive, you will erase Ubuntu, so it is best to do this from a Windows/Ubuntu CD so that you can immediately install another system.

---

### Post by ledwardz on 2011-02-10
> **3Miro said:**
> If your windows CD doesn't boot, it is a problem with your windows CD. A boot CD takes over your system long before anything from Ubuntu has a chance to load/start. For more information on this issue, you can refer to Microsoft/Windows vendor/Windows Forum.

As for formatting your hard-drive. Formating completely erases all information on it, hence you cannot format a drive while you are using it (with any operating system). You can use an Ubuntu CD, boot from it and then use Gparted to format anything (when you use a live CD the hard-drive is not being used). Note that if you reformat your hard-drive, you will erase Ubuntu, so it is best to do this from a Windows/Ubuntu CD so that you can immediately install another system.


its defnitley not a problem with any of the cd's ive tried them all on my laptop any they work no problem. And before installing ubuntu they all worked also. I started with xp and upgraded to vista then 7 hence i have all the cd's and it did this no problem too. If i put in the ubuntu reboot cd and reinstall ubuntu but only use say half the hardrive will i be able to reformat the other half? (it will boot from the ubuntu cd) Also im prepared to lose ubuntu, i will install windows then dual boot with ubuntu.

---

### Post by ledwardz on 2011-02-10
> **dabl said:**
> From your friends at Google:

[http://forums.speedguide.net/showthread.php?249387-Windows-7-cannot-boot-from-CD-code-5&p=2294125&viewfull=1#post2294125](http://forums.speedguide.net/showthread.php?249387-Windows-7-cannot-boot-from-CD-code-5&p=2294125&viewfull=1#post2294125)

and (see last post)

[http://forums.cnet.com/7723-7591_102-325608.html](http://forums.cnet.com/7723-7591_102-325608.html)
  

Thanks, i will try this.

1. Allow Hard disk boot
2. Press F8 on startup
3. Select Safe Mode with command prompt
4. Select CD drive "<CD Drive>:"
5. type "Setup"
6. Press Enter key

---

### Post by 3Miro on 2011-02-10
> **ledwardz said:**
> its defnitley not a problem with any of the cd's ive tried them all on my laptop any they work no problem. And before installing ubuntu they all worked also. I started with xp and upgraded to vista then 7 hence i have all the cd's and it did this no problem too. If i put in the ubuntu reboot cd and reinstall ubuntu but only use say half the hardrive will i be able to reformat the other half? (it will boot from the ubuntu cd) Also im prepared to lose ubuntu, i will install windows then dual boot with ubuntu.

You can boot from a Live CD and change the size of your partitions or completely repartition and reinstall Ubuntu. Then you can install Windows. However, note that Windows will replace your boot loader, so after getting windows to work, you will have to reinstall Grub 2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by ajgreeny on 2011-02-10
> **ledwardz said:**
> Thanks, i will try this.

1. Allow Hard disk boot
2. Press F8 on startup
3. Select Safe Mode with command prompt
4. Select CD drive "<CD Drive>:"
5. type "Setup"
6. Press Enter key
Sorry, you will find that this is only any use if you already have windows installed, F8 for safe mode is a standard windows key press.

As you seem to have ubuntu only on hard disk, you are wasting your time trying this.

I suggest that you make sure there is some free space, enough for Windows, on your hard disk by shrinking your ubuntu partition using gparted on the Ubuntu live CD.  You can not do this from your installed ubuntu as you can not work on mounted partitions, and if you are using ubuntu from hard disk, obviously it is mounted.

You may now find that windows CD will boot as it should see that there is space for the installation.  I don't know why this happens when it's only a CD that is booting, but I have read that this is the case, so give it a try.

---

### Post by Mark Phelps on 2011-02-11
> **ledwardz said:**
> When i insert the windows 7 disk i get a message saying "can't boot from disk code 5"
Windows vista and xp both come up with press any key to boot from cd and then loads ubuntu.

If I understand what you're saying, the following is true:
1) Insert XP CD ... get press any key ..
2) Insert Vista DVD ... get press any key ...
3) Insert Win7 DVD ... get can't boot ...

Since two of the three media work (presuming that Vista is a DVD, not a CD), it's obviously a problem with the third disk.

---

### Post by ledwardz on 2011-02-11
> **Mark Phelps said:**
> If I understand what you're saying, the following is true:
1) Insert XP CD ... get press any key ..
2) Insert Vista DVD ... get press any key ...
3) Insert Win7 DVD ... get can't boot ...

Since two of the three media work (presuming that Vista is a DVD, not a CD), it's obviously a problem with the third disk.

After it says this press any key (i press a key) the screen goes black for about 1 minute after doing so it just loads ubuntu again......

---

### Post by ledwardz on 2011-02-11
> **3Miro said:**
> You can boot from a Live CD and change the size of your partitions or completely repartition and reinstall Ubuntu. Then you can install Windows. However, note that Windows will replace your boot loader, so after getting windows to work, you will have to reinstall Grub 2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

okay, i now have my 2 partitions, i erased one and click format ntfs using the disk utility but am stuck on what to do. Ive tried booting up with vista but screen goes black and it loads ubuntu again????

---

### Post by coffeecat on 2011-02-11
I don't know whether this has been suggested, but are you sure your CD/DVD drive is OK? If you are not able to boot CDs/DVDs, then this is due either to  wrong BIOS settings, faulty discs or a faulty CD/DVD drive. None of your Windows discs will boot, if I read this thread correctly. Can you boot an Ubuntu live CD to see whether the optical drive is working properly?

**EDIT**: OK, you seem to be saying earlier in the thread that you can boot from an Ubuntu CD. Can you confirm I've read that correctly?

---

### Post by ledwardz on 2011-02-13
> **coffeecat said:**
> I don't know whether this has been suggested, but are you sure your CD/DVD drive is OK? If you are not able to boot CDs/DVDs, then this is due either to  wrong BIOS settings, faulty discs or a faulty CD/DVD drive. None of your Windows discs will boot, if I read this thread correctly. Can you boot an Ubuntu live CD to see whether the optical drive is working properly?

**EDIT**: OK, you seem to be saying earlier in the thread that you can boot from an Ubuntu CD. Can you confirm I've read that correctly?


yeah that is correct. I now have 2 partitions both with ubuntu on but am stuck on what to do now have formatted one half i think..... but now how do i install windows?

---

### Post by ledwardz on 2011-02-16
Anyone? Im gunna had to buy a new computer at this rate

---

