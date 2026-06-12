---
title: "Ubuntu possible fix?"
date: 2010-07-06
forum: General Help
---

### Post by homer2210 on 2010-07-06
using MS XP as my O/S and i got Unmountable_boot_volume error. Got this message the other night and I have some questions. I have been searching online about how to fix this and see that you need the OS installation CD's, well I have a Dell which had the OS already installed (XP) so no cd's. Is it possible for me to install ubuntu and gain access to my hard drive data? I have files that I really need to keep, need some major help.

---

### Post by Rubi1200 on 2010-07-06
> **homer2210 said:**
> using MS XP as my O/S and i got Unmountable_boot_volume error. Got this message the other night and I have some questions. I have been searching online about how to fix this and see that you need the OS installation CD's, well I have a Dell which had the OS already installed (XP) so no cd's. Is it possible for me to install ubuntu and gain access to my hard drive data? I have files that I really need to keep, need some major help.

Hi and welcome.

I suggest you get hold of an Ubuntu CD (or any live Linux distro for that matter; my personal suggestion would be Knoppix) and boot the computer with it, setting BIOS to boot from the CD/DVD drive of course.

Once you are in:

1) access your files and save them to an external HDD or USB stick.

2) click on the link at the bottom of my post. Follow the instructions there and post the results back here.

We could help you set up a dual-boot with Windows if you would be interested.

---

### Post by Anton32828 on 2010-07-06
I'll add a little more general information that may be useful if you are totally new to the subject of data recovery.
 
1) Ubuntu and other Linux distributions typically ship on a "Live CD" that contains a complete bootable operating system. You can download this disk-image from Ubuntu's website (or the previous poster's suggestion of using the Knoppix website). Use a friend's computer or a school computer to get the CD image and burn it to a CD.
 
2) Stick the CD in your computer's drive and boot from the CD. You do this by pressing a function key during start-up (F8 or F12 on many systems --- check your documentation or tech support website). This will load Linux into memory and present you with a desktop graphical interface.
 
3) If your hard drive is at all functional it should show up in the "Places" menu (in Ubuntu), or as an icon on your desktop. Linux can read all the common Windows file formats (FAT, NTFS). If you can see your hard drive in Linux you should be able to copy your "My Documents" folder to an external USB drive. Or you could install a second hard-drive in your computer and copy the files to that drive.
 
4) If your hard drive is NOT readable by Linux you can run the "disk utility" application. This will report the SMART status of your hard drive, which is a common hardware protocol built into the drive. It reports drive health. This will tell you whether the drive is physically damaged. If it is, you can do a web search on data-recovery companies in your area / country. These companies physically dis-assemble damaged drives to recover data. It is an expensive option but you'd be surprised at how much data they can manage to recover.
 
Good luck.

---

### Post by pricetech on 2010-07-06
You said it's a Dell; F12 will give you the one time boot menu.

Dell should have included media, but sadly they have joined other vendors who seem to think that saving a few cents on media can make the computer less expensive.

If you have a friend with a Dell and the same version of XP, see if you can borrow their installation media to do the repair.

---

### Post by homer2210 on 2010-07-06
> **pricetech said:**
> You said it's a Dell; F12 will give you the one time boot menu.
 
Dell should have included media, but sadly they have joined other vendors who seem to think that saving a few cents on media can make the computer less expensive.
 
If you have a friend with a Dell and the same version of XP, see if you can borrow their installation media to do the repair.
 
If I do find a CD and do the repair using the OS XP, will I lose the data? Is it like running with a clean slate? I will try the Ubuntu tonight to see if that works and leave results.

---

### Post by Rubi1200 on 2010-07-06
> **homer2210 said:**
> If I do find a CD and do the repair using the OS XP, will I lose the data? Is it like running with a clean slate? I will try the Ubuntu tonight to see if that works and leave results.

Make sure you run Ubuntu in live mode. That means when its menu appears choose the option to Try Ubuntu. Do NOT choose install otherwise you are likely to lose everything.

As I mentioned before, if you can use Ubuntu to boot the computer click on the link at the bottom of my post and follow the instructions there.

I don't know if this describes your situation, but it might be good to take a look:

[http://support.microsoft.com/kb/297185](http://support.microsoft.com/kb/297185)

---

### Post by pricetech on 2010-07-08
A repair using an XP disk is not supposed to cost you any data, but it's always a good idea to back up anyway before doing anything like that.  You should be able to back up your files using the Live CD.

---

### Post by ken_23434 on 2010-07-08
I hope you are able to recover your files.  I know the terminology in Linux is slightly different and can be a little confusing, initially.
 
Once you get your files recovered, keep that Linux disk.  Pull it out occassionally and select the "try Ubunutu" option (or what ever flavor you have).  The LiveCD format will allow you to boot your Windows machine up and use Ubuntu without altering ANY data on your computer.  After you experiment with Ubuntu a while, you might like it enough to do an install and become one of US.  :)
 
One thing I would like to point out, while you are running from a LiveCD, it will be MUCH slower than from a fully installed version (since the CD drive is MUCH slower than a HDD).  Don't let that lead you to believe the OS is slow to do things.
 
Even if you do not convert to Ubuntu, the knowledge of how to use it to recover your Windows data is priceless.

---

