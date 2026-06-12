---
title: "My USB/Memory Sticks turn into Read-Only-File-System!"
date: 2010-01-15
forum: General Help
---

### Post by MKVCrazy on 2010-01-15
I have tried to write my files to 2 (2GB each) USB sticks and both turned into a Read-Only-File-System. Then I tried with my Memory Stick Duo and it also turned into that. So I give my last try with my SanDisk HC Memory Card (from photo camera) and resulted the same. I can copy the files of those portable storages into my HDD fine but not write into them or delete any files inside those portable storages.

Any idea what I am doing wrong?

---

### Post by saturnblackhole on 2010-01-15
well you can open your termanial and enter 
> sudo nautilus 
this will allow you to open nautilus as root. once its open right click on your flash drive and click properties and then go to permission and make sure to give yourself read and write capabilities.

---

### Post by stoneage on 2010-01-15
For graphical applications it is better to use gksudo. sudo is fine for command line use:-

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by MKVCrazy on 2010-01-15
Thank you, I'll try those.

---

### Post by warfacegod on 2010-01-15
If on the off chance your memory cards are not far32 but NTFS, you'll need to install ntfs-3g and ntfs-3g54 in Synaptic.

---

### Post by MKVCrazy on 2010-01-16
> **saturnblackhole said:**
> well you can open your termanial and enter 

this will allow you to open nautilus as root. once its open right click on your flash drive and click properties and then go to permission and make sure to give yourself read and write capabilities.
It doesn't work :( I can't even change the permission.
> **warfacegod said:**
> If on the off chance your memory cards are not far32 but NTFS, you'll need to install ntfs-3g and ntfs-3g54 in Synaptic.
I have those installed.

EDIT: When I check the "USB Properties" **Filesystem Type: msdos** is at the bottom.

---

### Post by warfacegod on 2010-01-16
> It doesn't work  I can't even change the permission.

But you can see them?

---

### Post by MKVCrazy on 2010-01-16
> **warfacegod said:**
> But you can see them?
Yes, I can see the files inside the USB. I can copy USB > My HDD but not backwards. I can't even delete any files on the USB.

---

### Post by warfacegod on 2010-01-16
It sounds like you need to make yourself the owner:

```
sudo chown -R warfacegod:warfacegod /media/drivename
```

Change my name to your user name and look in /media for the drive name, its probably a long string of numbers and letters. Make sure you get the right drive name and do not chown your filesystem drive.

---

### Post by MKVCrazy on 2010-01-16
Something I'm not sure. Which one is my username? Is it the one from owner@owner-desktop or my name?

I tried with owner there and I got a bunch of things like "Chaning ownership of etc etc". Then I tried to delete a file on the USB and it still doesn't work :( My username the one that's not "owner" has space. For example: my username is like this "User Name". I tried 'User Name' and it didn't work also tried without the single quotes, still didn't work.

---

### Post by dumblebee100 on 2010-01-16
IF you are the only user on your system then in your case it will be like this 
```
chown -R owner:owner /media/partion_name
```

---

### Post by warfacegod on 2010-01-16
> **MKVCrazy said:**
> Something I'm not sure. Which one is my username? Is it the one from owner@owner-desktop or my name?

I tried with owner there and I got a bunch of things like "Chaning ownership of etc etc". Then I tried to delete a file on the USB and it still doesn't work :( My username the one that's not "owner" has space. For example: my username is like this "User Name". I tried 'User Name' and it didn't work also tried without the single quotes, still didn't work.

You log in with say bob francis (note the space)?

If so then:

```
sudo chown -R user\ name:user\ name /media/drivename
``` (note the back slashes.

---

### Post by subreyfer on 2010-01-16
Do you have any other computers or operating systems available? Any luck writing to the USB sticks with those?

If the chown command doesn't seem to have an effect, could you copy and paste the output in the terminal when you try it?

My suggestion would be:
```
sudo chmod -R +rw /media/drivename
```
That should change the permissions so that anyone can write to the drive, but just be aware of the potential security issues.

---

### Post by Morbius1 on 2010-01-16
Something's not right here.

The USB sticks, unless you re-formatted them yourself are either FAT32 or NTFS. 

If it's FAT32 and they are automounted upon insertion they will mount with ownership / permissions of **user_name:root / 700**. You and only you would have the ability to read and write to that stick.

If it's NTFS they will mount as **root:root / 777**. Everyone can do anything they want to those sticks.

You can chmod or chown those sticks all you want but you cant change ownership or permissions on a windows filesystem outside of a mount command ( or fstab ).

The only thing that comes close to explain your predicament is if those USB sticks are formatted in ext3 which by default would mount to **root:root / 755**. In this case the chown commands above should have fixed it.

Are you the primary user of this system and / or have you got entries in /etc/fstab that control how these sticks are mounted  instead of having them auto mount?

---

### Post by C.S.Cameron on 2010-01-16
I had one memory stick do that once, I figure it is fried.

Some of the flash memory vendors have programs for recovering a flash drives.

---

### Post by warfacegod on 2010-01-16
> **C.S.Cameron said:**
> I had one memory stick do that once, I figure it is fried.

Some of the flash memory vendors have programs for recovering a flash drives.

I could see that in this situation if it were one. Unfortunately it's four, one right after the other unbelievably long odds that they fried at the same time.

---

### Post by clevertomato on 2010-01-25
I'm not sure if this will work for you, but I was experiencing the exact same problem and I got it fixed. Let me explain how it happened to me...

I have a SanDisk U3 Cruzer. It has a bootable Karmic system on it, but I'm sure that doesn't matter. It is brand new as of Christmas and I've used it in Ubuntu many times. A friend copied some files to it in Windows 7 the other night. The file copy process froze and he had the hardest time even trying to kill the process (thinking how easy that is to do in Linux, I had to chuckle a little, but as you'll soon read, I guess the laugh is on me). Anyway, he eventually got some files copied to it and yanked it out (I seriously doubt he clicked on "Safely Remove Hardware" before removing it). Since then I was unable to write to this flash drive in Ubuntu no matter what I did. Same symptoms as you (read-only file system).

I went upstairs, popped it into a machine with XP x64, it showed up, then I clicked "Safely Remove Hardware," then popped into Ubuntu machine and all is perfect again.

It's pretty sad that someone can royally mess up a flash drive with Windows this way so that it is not writeable again until inserting into a Windows system. What if I was an Ubuntu-only household. There must be a way to fix a USB flash drive in this condition WITHOUT having to put into a Windows machine, but I don't know how.

---

### Post by Herman on 2010-01-25
It's easy to run a file system check in Ubuntu and repair a corrupted file system or one that has been marked as 'dirty' by running commands in terminal.
If the file system suspected of having been damaged is an ext series file system, a command such as 'sudo e2fsck -C0 -f -v -p /dev/sdx,y' will normally fix it. That's the traditional way to do it. There are other commands for other kinds of file systems.
Never run a file system check on a file system while it is mounted.

If you have GParted installed or if you still have your Ubuntu Live CD, which has GParted in it, you don't need to know any commands at all. Just right-click on the partition in GParted and click 'Check', then confirm by clicking on the 'Apply' checkmark, then click 'Apply' again in the confirmation dialog box that pops up. In a few minutes your file system will be fixed, (in most cases).

There are lots of things that can go wrong and the file system is not always the problem, but a file system check is always good so it makes sense to try that first.

---

### Post by D3V11 on 2010-01-25
> **saturnblackhole said:**
> well you can open your termanial and enter 

this will allow you to open nautilus as root. once its open right click on your flash drive and click properties and then go to permission and make sure to give yourself read and write capabilities.

**do not open graphical applications with sudo. instead use gksudo. this is asking for file corruption.**

---

### Post by clevertomato on 2010-01-25
Thanks for the tip, Herman.

---

