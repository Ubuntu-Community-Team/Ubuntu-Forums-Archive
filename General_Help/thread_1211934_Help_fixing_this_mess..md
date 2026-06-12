---
title: "Help fixing this mess."
date: 2009-07-13
forum: General Help
---

### Post by uuntub on 2009-07-13
Allo. The complete story (I think it's best not to leave out any details.) -

I'm on my laptop one night, A toshiba A200 Satellite, and im using vista and suddenly the screen goes blank.. I restart the machine and it wont boot up properly, it goes to load vista and then the Hard drive hangs. I ask a very knowledgeable friend about the problem and I ask him to give me a quick fix because my laptop could not be out of order for very long due to the fact I needed it to keep in contact with what turned out to be the love of my life..

He suggested UBUNTU loaded from a live CD.. And that's exactly what I did, I bought the CD which was UBUNTU 8.10 DESKTOP EDITION and it works like a charm, I prefer this over any other system. The only problem I have is I was brought up on MICROSOFTS products and now that I have got further advice (which is using the LINUX equivalent to MICROSOFTS chkdsk to fix disk errors) I have no idea on how to use the terminal.

[I]I have looked profusely around various forums and on google to find the commands that make sense but I have only been met with frustration.

[/I]
[LIST]
[*]The instructions previously given to people that I have seen are to general for someone who has used linux for the first time.
[*]No manuals came with Linux so I cant look up a command line structure.
[*]That friend of mine, while extreamly knowledgeable is hard to keep in contact with.
[/LIST]
[I]All I need is how to 'chkdsk' the C drive in linux terminal or if anyone has a better suggestion.. Im all ears..

I dont know if a new partition would work? That I can boot from? If this is a good idea, how do I do it from Linux terminal?

[/I]**Cheers.**

---

### Post by miklcct on 2009-07-13
> **uuntub said:**
> omitted
[/I]
[LIST]
[*]The instructions previously given to people that I have seen are to general for someone who has used linux for the first time.
[*]No manuals came with Linux so I cant look up a command line structure.
[*]That friend of mine, while extreamly knowledgeable is hard to keep in contact with.
[/LIST]
[I]All I need is how to 'chkdsk' the C drive in linux terminal or if anyone has a better suggestion.. Im all ears..

I dont know if a new partition would work? That I can boot from? If this is a good idea, how do I do it from Linux terminal?

[/I]**Cheers.**

There is a full set of manuals which you can access it either using the command line:

man fsck

for usage for fsck (UNIX eqivalent for DOS/Windows chkdsk)

or inside Konqueror, type into the URL field:

man:/fsck

Actually, the usage of fsck is simply "fsck your partition":

fsck /dev/sda1

to check /dev/sda1 for errors.

When Linux is booted, the kernel assigns a device number to each hard disk and partition called /dev/sd? where ? is a letter starting from a:

/dev/sda is your first hard disk,
/dev/sdb is your second hard disk,
/dev/sdc is your third, etc.

In each hard disk, the kernel assigns a partition number. For primary partitions, the number is taken from the partition table; for logical partitions, the number is assigned sequentially from 5:

/dev/sda1 is your first primary partition on /dev/sda
/dev/sda2 is your second primary partition on /dev/sda
/dev/sda5 is your first logical patition on /dev/sda

Linux allows you to have at most 15 partitions on a single hard disk, that is, 4 primary partitions and 11 logical partitions. To use more, you needs to use LVM.

---

### Post by uuntub on 2009-07-13
> **miklcct said:**
> There is a full set of manuals which you can access it either using the command line:

man fsck

for usage for fsck (UNIX eqivalent for DOS/Windows chkdsk)

or inside Konqueror, type into the URL field:

man:/fsck

Actually, the usage of fsck is simply "fsck your partition":

fsck /dev/sda1

to check /dev/sda1 for errors.

When Linux is booted, the kernel assigns a device number to each hard disk and partition called /dev/sd? where ? is a letter starting from a:

/dev/sda is your first hard disk,
/dev/sdb is your second hard disk,
/dev/sdc is your third, etc.

In each hard disk, the kernel assigns a partition number. For primary partitions, the number is taken from the partition table; for logical partitions, the number is assigned sequentially from 5:

/dev/sda1 is your first primary partition on /dev/sda
/dev/sda2 is your second primary partition on /dev/sda
/dev/sda5 is your first logical patition on /dev/sda

Linux allows you to have at most 15 partitions on a single hard disk, that is, 4 primary partitions and 11 logical partitions. To use more, you needs to use LVM.

Look, seriously man, thanks for your help but what you said - you might as well have said it in german. I have NO experiance in Linux what so ever... 

With a microsoft dos prompt you simply type in: chkdsk C:

To me, that was quick and easy to learn.. And I see that you gave me a link to the manuals but seriously is it so hard to give me a line of code to do what I want?

Im not a smart man - I would never claim to be. That's why I need help.

---

### Post by Celauran on 2009-07-13
> **uuntub said:**
> but seriously is it so hard to give me a line of code to do what I want?

He did.

```
sudo fsck partition
```

You just need to replace partition with the partition you want to check (eg. /dev/sda1)

Which partition you'll need to format really depends on how you set up your drive and how many drives you have. Assuming one hard drive and only one partition, /dev/sda1 is what you want.

---

### Post by nlinecomputers on 2009-07-13
You shouldn't use Linux fsck to try and fix a Windows formated disk.  Support for NTFS in Linux is limited to standard reads and writes.   Repairing file errors on NTFS formatted disks isn't really reliable from Linux.

If your system can't boot into Windows then you to use Microsoft based tools to fix it.  If possible.  You'll need your Windows Xp CD or Vista DVD to fix it.

Is this a Vista machine or an Xp one?

---

### Post by dave_i on 2009-07-13
Does it start booting before it hangs? If it does, pressing F8 as Vista starts to boot should bring up a menu which will allow you to try and fix the problems.

If not, then you will need to boot from a Vista DVD to fix problems with the drive. 

Failing that, if you can mount the drive via the Ubuntu live CD, you could copy all the files you need to keep onto an external drive, then do a fresh install of Vista or Ubuntu.

---

### Post by Rob_H on 2009-07-13
> **nlinecomputers said:**
> You shouldn't use Linux fsck to try and fix a Windows formated disk.  Support for NTFS in Linux is limited to standard reads and writes.   Repairing file errors on NTFS formatted disks isn't really reliable from Linux.

If your system can't boot into Windows then you to use Microsoft based tools to fix it.  If possible.  You'll need your Windows Xp CD or Vista DVD to fix it.

Right! Don't try to use fsck to fix a Windows partition. At best, it'll refuse to run. At worst, you'll ruin it beyond repair.

The advantage of booting up with a live CD is that it will give you an opportunity to copy your important files off of the failing NTFS partition (assuming it's healthy enough to be read by Linux) and onto some backup media like another hard drive, USB thumbdrive, DVD-RW, etc. Afterwards, you can safely proceed to reformat the Windows partition and reinstall either Ubuntu or Windows over it, since your data has been backed up.

If Microsoft tools cannot fix the problem and Ubuntu is unable to read the partition, I would recommend buying a low-level disk recovery tool like [SpinRite]("http://www.grc.com/sr/spinrite.htm") if you really need to get at your data. (No, I don't work for them.) It's not cheap, but I've had good luck using it for "in-place" data recovery. Good luck!

---

### Post by uuntub on 2009-07-13
> **Celauran said:**
> He did.

```
sudo fsck partition
```You just need to replace partition with the partition you want to check (eg. /dev/sda1)

Which partition you'll need to format really depends on how you set up your drive and how many drives you have. Assuming one hard drive and only one partition, /dev/sda1 is what you want.

I tried the code he said and it said I couldnt because I wasnt 'root' or some other error.

My post was designed for someone who could go through the process step by step .. NOT SOMEONE ASSUMING I HAVE EVEN LIMITED EXPERIANCE.

I have NONE? I was looking for code... And again... is it that hard?

> **nlinecomputers said:**
> You shouldn't use Linux fsck to try and fix a Windows formated disk.  Support for NTFS in Linux is limited to standard reads and writes.   Repairing file errors on NTFS formatted disks isn't really reliable from Linux.

If your system can't boot into Windows then you to use Microsoft based tools to fix it.  If possible.  You'll need your Windows Xp CD or Vista DVD to fix it.

Is this a Vista machine or an Xp one?

I shoved an xp disk in and it tried to perform a setup .. but it started to hang so .. back to UBUNTU .. 

[I]Come on people... It cant be hard to give a straight answer... 

Chkdsk but the linux equiv -> How to do this on C drive (which has no name) -> [/I]????

---

### Post by Rob_H on 2009-07-13
> **uuntub said:**
> 
[I]Come on people... It cant be hard to give a straight answer... 

Chkdsk but the linux equiv -> How to do this on C drive (which has no name) -> [/I]????

Rudely demanding help isn't going to get you far. 

This has been stated a couple of times already, but I'll say it again: You can't use Linux utilities to fix a Windows partition. You can use the live CD to try to backup your data. That's it. If you want to fix the partition, you need to use a Windows/Microsoft tool or a low-level disk recovery tool like SpinRite.

---

### Post by moody_mark on 2009-07-13
I got to agree with the above. **Backup the data from your windows disc before you attempt any repair**

Booting into ubuntu with the live CD is great and gives you the opportunity to archive important data before you fix the problem. Running a Linux tool for partition repair on a windows disc will very likely cause you problems. I too would stay away from this option. Instead once you have backed up you data, try using windows tools like hitting F8 while booting windows and going into safe mode (does Vista support that?) to get back into your windows system to try and fix the problem.

It sounds like you may well have a disc problem if you are hearing clunks etc. In fact dont be surprised if you have trouble getting linux to access the disc too if its got problems no matter what OS you use a bad disc is a bad disc.

---

