---
title: "External Hard Drive will not let me backup files"
date: 2010-01-10
forum: General Help
---

### Post by BaldDumboRat on 2010-01-10
Hello, I've been working at this for the past 2 days now. My computer got some kind of virus or something that has caused it to loop at startup and continually reset. I run an XP OS on a Gateway. I desperately need to backup my files, because the person who had my backup absently deleted my stuff. I was able to boot up using an Ubuntu disc and I'm in it right now, I've found my files, I have an external hard drive. The problem:
First, it wont let me paste into the hard drive. If I drag, it says "Error while copying to "/media/FreeAgent Drive". You do not have permissions to write to this folder." I've mounted the external drive, nothing changes. I've gone in to properties, is says under permissions that the owner is root, folder access is "Access files" and at the bottom is says "You are not the owner, so you can't change these permissions." The drop downs where I need to change permissions is in gray, so I can;t change it.
So next, I tried [FONT=Courier New]"gksu nautilus", went to the drive through there, and it let me use the drop down selection under permissions. I tried to change the folder access and I got this message: "The permissions could not be changed. Couldn't change the permissions of "FreeAgent Drive" because it is on a read-only disk." So I tried changing the file access to Read and Write. It didn't give an error, so I thought perhaps it finally worked. I hit apply, and tried to put my files in. Once again I got the message from before that said I didn't have permission. I tried to change the owner so it was no longer root and I got "The owner could not be changed. Couldn't change the owner of "FreeAgent Drive" because it is on a read-only disk."

I'm getting so frustrated right now. These files are VERY important to me! 
The hard drive I have is a Seagate FreeAgent desk 500GB

If there are ANY suggestions I would really appreciate it!
[/FONT]

---

### Post by Crafty Kisses on 2010-01-10
I'm just going to guess here and say the drive is NTFS. To make sure though I need to see the results of the following commands, once you have posted the results up here on the forum, I or somebody else can help you further, what are the results of the following?
```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by BaldDumboRat on 2010-01-10
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1270    10201243+   7  HPFS/NTFS
/dev/sda2   *        1271       38913   302367397+   7  HPFS/NTFS

Disk /dev/sdf: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS

```

---

### Post by BaldDumboRat on 2010-01-10
I'm going to try using my NexStar SX external with the same  methods while I wait for a response, just in case it might work. 
I'd prefer to get the Seagate working though, because the space on my NexStar isn't enough to back everything up. Wish me luck.

I really hope the SeaGate will be workable, I just bought it for this purpose.

---

### Post by howefield on 2010-01-10
Use synaptic to install ntfsprogs and ntfs-3g.

The descriptions will tell you what they do.

---

### Post by BaldDumboRat on 2010-01-10
I'm sorry, I'm a little bit new to all this. Is Synaptic already on the computer or do I need to download it?

---

### Post by howefield on 2010-01-10
Go to System > Administration > Synaptic Package Manager.

In the search field type ntfs and check the boxes beside ntfsprogs and ntfs-3g, "Mark for Installation". 

Accept and dependancies and click apply.

Another good one I forgot to mention is ntfs-config

This will give you a menu item from which you can select your ntfs drive and make them read/writable etc.

So, the 3 useful applications are, ntfsprogs, ntfs-3g and ntfs-config

---

### Post by BaldDumboRat on 2010-01-10
It seems the only one listed when I search is ntfsprog. None of the others are there. I marked for installation, I think it installed because it now has the reinstall option on it, but I didn't see anywhere that said accept and dependancies. Perhaps I'm missing something here...

---

### Post by howefield on 2010-01-10
> **BaldDumboRat said:**
> but I didn't see anywhere that said accept and dependancies.

Sorry, my poor typing, I didn't mean "and" dependancies, should have been "any" dependancies.

They won't all have dependancies but ntfs-config will have one which is "menu"

I moved all my drives to ext4, so maybe a little rusty dealing with ntfs drives. Try searching for the other two by full names.

---

### Post by BaldDumboRat on 2010-01-10
It still looks like ntfsprog is the only ntfs related file in there. I looked down the list of 'all' by hand, even. Is there anything else I can do?

---

### Post by Icehuck on 2010-01-10
I thought NTFS was already built into the linux kernel? I don't belive you will need ntfs-3g.

Do you know how to unmount the drive? If so please unmount it and run the following. You need open a terminal to do so.

sudo mount -t ntfs /dev/sdf1 ~/Pictures -o nosuid,rw

When it asks for a password, just hit the enter key.

This will mount that device under the Pictures folder on the live CD. It will also make sure it's mounted read and write and not require user permisions.

Then to copy files to it just copy them to the pictures folder. I could totally be off on this but it seems to work for me.

---

### Post by BaldDumboRat on 2010-01-10
I got this message: mount: mount point ~pictures does not exist

---

### Post by Icehuck on 2010-01-10
> **BaldDumboRat said:**
> I got this message: mount: mount point ~pictures does not exist

Ok, looks like you might have forgot the "/" also Pictures is case sensative.

When you type it in, it should look exactly like this  ~/Pictures

---

### Post by BaldDumboRat on 2010-01-10
Alright, I tried that and got a similar message: 
mount: mount point /home/ubuntu/Pictures does not exist

---

### Post by Icehuck on 2010-01-10
> **BaldDumboRat said:**
> Alright, I tried that and got a similar message: 
mount: mount point /home/ubuntu/Pictures does not exist

Really? It exists on my live CD, but it's ok. We will just do this instead.

Type these lines in a terminal.  

cd ~
mkdir drive
sudo mount -t ntfs /dev/sdf1 ~/drive -o uid=ubuntu

then you can open up nautilus and your drive will be listed under the folder drive.

---

### Post by BaldDumboRat on 2010-01-10
I'm feeling a bit more dumb as this goes on, but that's because I'm not used to the system. I have nautilus open, the only file I see is desktop, which leads to nothing. It did say that the drive file exists, because I tried the commands a second time just in case, but I'm still not quite sure where it went.

---

### Post by Icehuck on 2010-01-10
> **BaldDumboRat said:**
> I'm feeling a bit more dumb as this goes on, but that's because I'm not used to the system. I have nautilus open, the only file I see is desktop, which leads to nothing. It did say that the drive file exists, because I tried the commands a second time just in case, but I'm still not quite sure where it went.

Easy way to find it is to go from the menu system, Exit nautilus and go the menu system on the top. Second from the left is Places. Select Places then Home Folder. It will be the 1st option. The folder "drive" will then be listed on the right side.

---

### Post by BaldDumboRat on 2010-01-11
Alright, thank you. I found it, and my external drive is detected under it. Now it says the owner is just the regular user, but it still has it as a read only, I tried to change permissions to make it read and write, but it still says "Couldn't change the permissions of "drive" because it is on a read-only disk"

Might this be an issue with the drive itself? It has a setup.exe file in it, but the computer wont detect the filetype.

---

### Post by Icehuck on 2010-01-11
> **BaldDumboRat said:**
> Alright, thank you. I found it, and my external drive is detected under it. Now it says the owner is just the regular user, but it still has it as a read only, I tried to change permissions to make it read and write, but it still says "Couldn't change the permissions of "drive" because it is on a read-only disk"

Might this be an issue with the drive itself? It has a setup.exe file in it, but the computer wont detect the filetype.

  
What do mean by filetype? Are you trying to run the setup.exe file? Also an easy way to make sure it's not read only is to type this into the terminal.

chmod 777 ~/drive

You will have full read/write/execute on the drive.

---

### Post by BaldDumboRat on 2010-01-11
I tried to run it in case it would do something but it says it can't.

I got this when I put in what you wrote: 
chmod: changing permissions of `/home/ubuntu/drive': Read-only file system

---

### Post by BaldDumboRat on 2010-01-11
Could any of this be because this is version 7.04 of ubuntu?

---

### Post by Icehuck on 2010-01-11
> **BaldDumboRat said:**
> Could any of this be because this is version 7.04 of ubuntu?

Yeah, that's an old version of the Ubuntu liveCD. I don't know if you can pull in the ntfs drivers for fuse on that liveCD. Try typing this in a terminal and see what you get.

sudo apt-get install ntfs-3g

Actually, this guide might help out. [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by BaldDumboRat on 2010-01-11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-3g



I'm working on downloading the newer version on a different computer right now. hopefully that might change some things...

---

### Post by Icehuck on 2010-01-11
> **BaldDumboRat said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-3g



I'm working on downloading the newer version on a different computer right now. hopefully that might change some things...

If you get the newest liveCD that will make everything work :P:P

---

### Post by BaldDumboRat on 2010-01-11
I certainly hope so! Well, wish me luck, I have about an hour to wait, so if any more problems surface after I get it running, I'll be back. Thank you for all the help so far, it was quite an interesting learning experience, to say in the least.

---

### Post by Icehuck on 2010-01-11
Ok, I'll check back on this in about an hour and see if you have any updates then.

---

### Post by BaldDumboRat on 2010-01-11
It works PERFECTLY! No changing anything, no mounting, and now my entire windows is being backed up on my drive as I type!
And all because I had the wrong version of Ubuntu, wow, I feel slightly embarrassed.

But thank you all for the help, I'm glad everyone was so quick to respond and thank you for being patient with me, hope I wasn't a bother!

---

### Post by BaldDumboRat on 2010-01-11
UGH! Nevermind! My computer shut off in the MIDDLE of backing up, and now it refuses to load into my external hard drive!
I get this:
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Edit: Also, whenever I have the external hard drive plugged in now, the fan gets EXTREMELY loud and stays that way until I take it out of the computer.

Also, it wont even acknowledge my previous External hard drive, NexStarSX. It acts like I didn't plug anything in. I'm not sure what's going on, but it's really starting to worry me.

---

