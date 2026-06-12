---
title: "windows ME/XP"
date: 2006-04-12
forum: General Help
---

### Post by mr1989 on 2006-04-12
I recently but ubuntu on my computer and i didn't set a partition on the computer so now it's all ubuntu, and now i want windows back, i but in the restore disks i put in the Windows ME ones that came with the computer and  the start up screen for the installation for WINDOWS ME and when it came to formating the drive it said it was unable to read the media in my (c:) drive? what do i do to get windows back. My friend said he will give me a copy of windows XP cause installing me didn't work. so basiclly what can i do to get windows back? thanks

---

### Post by dbcummings on 2006-04-12
I personally thing you should stick with Ubuntu.  ME was the worst of the Windows OSes.  You probably won't get much help from this forum if you want to reinstall Windows.  Do you know if your reinstallation software is a full-version or is it simply an image?  Either way, your system should boot from the CD.  Have you ever reinstalled from these CDs before?

---

### Post by mr1989 on 2006-04-12
it's the full version, and i have reinstalled from the cds before.

---

### Post by evilregis on 2006-04-12
Sounds like your media is at fault.  It's not like Ubuntu rewrites your CD-ROMs firmware to reject Windows images.  So if it can't read the media try cleaning the disc itself and if it still doesn't work, try it on another computer and see if you get the same results, but without going through the whole install process.

---

### Post by ssalman on 2006-04-12
I don't see why it won't read your HD! Maybe Windows ME have a problem with the partition types

Try to put in the Ubuntu live-CD and reformat the HD using FAT as one partition. you can use Gparted.

Hopefully this will work.

---

### Post by Al3xanR0 on 2006-04-12
[QUOTE=mr1989]I recently but ubuntu on my computer and i didn't set a partition on the computer so now it's all ubuntu, and now i want windows back, i but in the restore disks i put in the Windows ME ones that came with the computer and  the start up screen for the installation for WINDOWS ME and when it came to formating the drive it said it was unable to read the media in my (c:) drive? what do i do to get windows back. My friend said he will give me a copy of windows XP cause installing me didn't work. so basiclly what can i do to get windows back? thanks[/QUOTE]

Get a hold of a floppy boot disk, make sure that it has both the fdisk and format utilities on it, then run ```
fdisk /mbr
``` This will clear your boot record. Next run ```
fdisk
``` if you are a windows user you should be familiar with its options. the last thing you should do is run ```
format c:
```
you should be able to install anything at this point. 

Personally I would stick with Ubuntu.

---

### Post by traherom on 2006-04-12
[QUOTE=Al3xanR0]Get a hold of a floppy boot disk[/QUOTE]Windows boot disk, btw. :)

---

### Post by W. Irving on 2006-04-12
How about reinstalling Ubuntu and making place for Windows XP? IMHO, it's the best combination. Ubuntu for reliability, productivity and general coolness, and Windows for gaming. :)

---

### Post by Al3xanR0 on 2006-04-12
[QUOTE=traherom]Windows boot disk, btw. :)[/QUOTE]

I stand (or sit) corrected :D

---

### Post by mr1989 on 2006-04-12
thanks all for your help will try your suggestions in the next hour and see what happens, 
also the computer never came with floppy disks only cds

---

### Post by threethirty on 2006-04-12
[QUOTE=evilregis]Sounds like your media is at fault.  It's not like Ubuntu rewrites your CD-ROMs firmware to reject Windows images. [/QUOTE] We hope to have this working in Dapper ;)

---

### Post by GoodPanos on 2006-04-12
> We hope to have this working in Dapper  I don't think it's an Ubuntu issue.  I have the same problems too whenever I install Linux on a machine (Xandros, Suse, Mandriva etc) and then install Windows over; it will stall.

The only way I am able to proceed is to do what Al3xanR0 suggested.  Not even a Windows boot CD will do.

None the less stick with Ubuntu. ;)

---

### Post by Omnios on 2006-04-12
Id advise dual booting, I dual booted Xp and Ubuntu for a year now to check out linux and now I find I bearly use XP any more. Anyways this gives you the ability to boot up in ME when needed and play with Ubuntu and gradualy learn Linux over a longer period of time.

---

### Post by threethirty on 2006-04-12
[QUOTE=GoodPanos]I don't think it's an Ubuntu issue.  [/QUOTE]
i ment the making it impossible to install windows, sorry my  comedy-fu is not strong today

---

### Post by mr1989 on 2006-04-13
[QUOTE=Omnios]Id advise dual booting, I dual booted Xp and Ubuntu for a year now to check out linux and now I find I bearly use XP any more. Anyways this gives you the ability to boot up in ME when needed and play with Ubuntu and gradualy learn Linux over a longer period of time.[/QUOTE]

how do I dual boot cause the other ways you lovely people have suggested has failed. ](*,)

---

### Post by gibson on 2006-04-13
[QUOTE=mr1989]also the computer never came with floppy disks only cds[/QUOTE]

[http://www.bootdisk.com/](http://www.bootdisk.com/)

:)

---

### Post by mr1989 on 2006-04-13
thanks just downloaded it will try it now

---

### Post by dbcummings on 2006-04-13
I thinks it is your media, too.  If you can't reinstall Windows, you won't be able to a correct dual boot.  You want to have Windows installed and then let Ubuntu set up the dual boot for you.  Its pretty simple.  Three options:  get your computer's vendor to send you a replacement copy of ME (which they probably won't do and its a horrid OS anyhow), purchase XP (which you really don't need since Ubuntu/Kubuntu) is superior, or reinstall Ubuntu/Kubuntu and embrace Linux.  I've completely migrated my home system.  My wife is simply a desktop user and she has completely adpated.  I have a laptop that dual boots while I'm in tech school.  I need it for my Microsoft classes.  But I finish this term and am wiping it off permanently.  I may put together a separate PC to run XP Pro and Server 2003 on to prepare for MCSE.  But otherwise, I'm finished with Windows.  I personally would work only in Linux if I could.

---

### Post by twigboy on 2006-04-14
Why dont you try using gparted to resize your ubuntu partition.  Then create an ntfs or fat32 partition on what is empty then try reinstalling windows.

---

