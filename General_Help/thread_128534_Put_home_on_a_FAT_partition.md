---
title: "Put /home on a FAT partition"
date: 2006-02-11
forum: General Help
---

### Post by el3ktro on 2006-02-11
I'm currently setting up a computer to be used by my parents. They both still need some Windows programs, but they WANT (no, I didn't force them to do so! ;-) ) to use Linux. So I'm setting up a dual-boot with WinXP & Ubuntu. I have sda1 as NTFS for Windows, sda2 as Ext3 for Ubuntu, and I want sda3 as a data partition for both OSes as VFAT. Is there a way to use this vfat partition as the home folder for the Ubuntu user? My first attempts of doing so failed - Gnome complained that a file .ICE... - don't remeber exaclty - couldn't be locked. So my question - is this possible at all, and if yes, what do I need to do. I know I could mount the vfat partition somewhere like /home/dad/data, but thats not nice. The main purpose for this is that when my parents click on the "Personal Folder" icon on Gnome that they are within this data partition - just for userfriendliness.

Any ideas?

Tom

---

### Post by aysiu on 2006-02-11
/home should never be FAT or NTFS.
Make one partition that's NTFS for Windows.
Make one partition that's Ext3 for Ubuntu (including /home).
Then make another FAT32 partition for sharing documents, but don't make it /home.

If you want, you can mount it at /home/username/documents

---

### Post by dcstar on 2006-02-11
[QUOTE=el3ktro]I'm currently setting up a computer to be used by my parents. They both still need some Windows programs, but they WANT (no, I didn't force them to do so! ;-) ) to use Linux. So I'm setting up a dual-boot with WinXP & Ubuntu. I have sda1 as NTFS for Windows, sda2 as Ext3 for Ubuntu, and I want sda3 as a data partition for both OSes as VFAT. Is there a way to use this vfat partition as the home folder for the Ubuntu user? My first attempts of doing so failed - Gnome complained that a file .ICE... - don't remeber exaclty - couldn't be locked. So my question - is this possible at all, and if yes, what do I need to do. I know I could mount the vfat partition somewhere like /home/dad/data, but thats not nice. The main purpose for this is that when my parents click on the "Personal Folder" icon on Gnome that they are within this data partition - just for userfriendliness.

Any ideas?

Tom[/QUOTE]
FAT partitions cannot support the security options required for a lot of things, you basically have only two options - Full RW for everyone or "Read Only" for everyone.

If you try to use anything that wants/needs to use the various Linux permission settings you could find trouble.

I believe there are Windows utilities to read ext2/3 partitions, it may be better to use that type and those utilities for Windows access.

---

### Post by lgmdaniel on 2006-02-11
Yep I would say setting the mount point in /home would be your best choice.
Or there are some utilities that allows windows to read ext2 as said above.

---

### Post by el3ktro on 2006-02-11
Thanks for all your answers.

Well I've now created a mount poit in /meda for the FAT partition, which makes this partition show up on the desktop and in the "places" sidebar of Nautilus, which is pretty nice actually. It just would be even nicer if it was possible to have /home within this fat partition. File permissions are not a problem here security-wise, because this computer is just used by my parents, and they have the same account. It just seems that Gnome doesn't like it ... :-(

Tom

---

### Post by el3ktro on 2006-02-11
Well actually when you mount the FAT partition with something like uid=1000,gid=1000,umask 027 then only uid 1000 has access to all the files ... damn I still wish it was possible. But then there's another problem: I suppose that all the hidden dot files would show up when I'm in Windows right? Could I hide them using Windows' "hidden attribute"? 

Tom

---

### Post by dcstar on 2006-02-11
[QUOTE=el3ktro]
......
File permissions are not a problem here security-wise, because this computer is just used by my parents, and they have the same account. It just seems that Gnome doesn't like it ... :-(

Tom[/QUOTE]
I told you that the Linux may need to set/use these permissions, Gnome is a Linux program.

---

### Post by ykpaiha on 2006-02-11
on a little spaced Hd I used a link with a directory on vfat (let's call it "winlin") inside my home.
but be very carefull as said above the security is not there with vfat and ntfs!!
try to keep as well this home in a separate partition as if you get trouble with linux you save your own datas.

---

### Post by el3ktro on 2006-02-12
Damn this is all not working right. I have to ask again: Is there any way to put /home/user on a FAT partition? I now have /home/user on the same ext3 partition as /, and I've mounted the user's data partition in /media/$user. Well this is okay, but it just complexifies the steps you have to do to save/open files etc. Most programs start in /home/$user when you go to the open/save dialog, and I always have to click on the "Places" button to get to the partition where I actually want to have my data. Some open/save dialogs don't offer this Places button, so I have to tell my users thats they have to browse to /media/$user first - which also sucks. Mounting the FAT partition somewhere in /home/$user/Documents also doesn't make sense, because users tend to create folders besides Documents, and those dirs/files are not stored on the FAT partition then.

So I either:

- need a way to put ~ on a FAT partition. The only problems seems to be this damn .ICEauthority file which can't be locked - is there a way around it?

- or I have to find a way to tell Gnome and all other programs that my home dir is not /home/$user but /media/$user.

Any help would be creatly appreciated!!


Tom

---

### Post by mcduck on 2006-02-12
[QUOTE=el3ktro]Damn this is all not working right. I have to ask again: Is there any way to put /home/user on a FAT partition? I now have /home/user on the same ext3 partition as /, and I've mounted the user's data partition in /media/$user. Well this is okay, but it just complexifies the steps you have to do to save/open files etc. Most programs start in /home/$user when you go to the open/save dialog, and I always have to click on the "Places" button to get to the partition where I actually want to have my data. Some open/save dialogs don't offer this Places button, so I have to tell my users thats they have to browse to /media/$user first - which also sucks. Mounting the FAT partition somewhere in /home/$user/Documents also doesn't make sense, because users tend to create folders besides Documents, and those dirs/files are not stored on the FAT partition then.

So I either:

- need a way to put ~ on a FAT partition. The only problems seems to be this damn .ICEauthority file which can't be locked - is there a way around it?

- or I have to find a way to tell Gnome and all other programs that my home dir is not /home/$user but /media/$user.

Any help would be creatly appreciated!!


Tom[/QUOTE]
No, you can't put ~ on a FAT partition. And you can't tell Gnome that you'r home dir is in /media/user, as then it _would_ be on FAT. The problem is that not only your files are stored in ~, but all your personal settings are there too. And those files need to have their permissions set correctly, and FAT doesn't support that.

What you could do is make a link from /media/$user to ~/Documents, or mount the partition directly to ~/Documents. That's pretty much as good as it gets. At least your parents wouldn't have to browse to /media as they would find everything inside their home dir. As long as all new directories are made inside Documents they are visible for both Windows and Linux.

By the way, if you have a Documents directory in your home dir, save/open dialogs seem to default to there instead of home. Also, you can enable Documents icon on desktop with Configuration Editor.

---

### Post by newuser111 on 2006-02-12
just use ext3 drivers for windows to read and write to your linux drives

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by el3ktro on 2006-02-12
[QUOTE=mcduck]No, you can't put ~ on a FAT partition. And you can't tell Gnome that you'r home dir is in /media/user, as then it _would_ be on FAT. The problem is that not only your files are stored in ~, but all your personal settings are there too. And those files need to have their permissions set correctly, and FAT doesn't support that.

What you could do is make a link from /media/$user to ~/Documents, or mount the partition directly to ~/Documents. That's pretty much as good as it gets. At least your parents wouldn't have to browse to /media as they would find everything inside their home dir. As long as all new directories are made inside Documents they are visible for both Windows and Linux.

By the way, if you have a Documents directory in your home dir, save/open dialogs seem to default to there instead of home. Also, you can enable Documents icon on desktop with Configuration Editor.[/QUOTE]

Hello,
thanks a lot again. I now did it very much as you proposed, I have the user dirs on the same ext3 partition as /, called /home/dad, /home/mum, /home/sister. Then I've mounted the three seperate FAT partitions to ~/Documents. The only problem was that Nautilus would show all three mounted FAT partitions on the desktop, called Documents, Documents[2] and so forth. I got around this by putting an entry in the Gnome autostart that umounts the two partitions of the two other users. So when "dad" logs in, the FAT partitions for "mum" & "sister" are umounted, not showing up on the desktop and - as a side effect - making it all more secure. Programs don't default to the documents folder/mount point though, but that may be because it's not called "Documents" but "Dokumente" (German) actually - but I just told my family a thousand times to store EVERYTHING within Dokumente, so that should be fine hopefully ...

Tom

---

### Post by Gvaz on 2006-02-12
i have a somewhat similar problem

i have just recently installed ubuntu 5.10, with XP Home.
the hard drive has a 130GB partition, and there was about 28.8GB that i left for linux. XP is on the big partition.
I also have a 200GB with two partitions.

this guide i used [HERE]("http://users.bigpond.net.au/hermanzone/"), told me to do it a certain way. (just read it, its faster to explain that way)

i can load up XP and Ubuntu just fine, however i cant access all my drives in Ubuntu. it says (other than the home one and the swap) that the drives are "Inaccessible" in the Disk "manager" thingy.

how can i make it so i can access my other partitions **OTHER** than formatting them. I dont have the means to back up my data completely.

also, i have already run Ubuntu's fsck, and it did not change anything.

thank you for any help you can give me.

---

### Post by RAOF on 2006-02-12
You could check out the "accessing windows drives" link in my sig.

---

