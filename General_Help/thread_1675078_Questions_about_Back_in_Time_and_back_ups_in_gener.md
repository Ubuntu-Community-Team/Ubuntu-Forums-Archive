---
title: "Questions about Back in Time and back ups in general"
date: 2011-01-24
forum: General Help
---

### Post by sudoer541 on 2011-01-24
Is it possible to backup my OS (OS state) using Back in Time? 
I am using Acronis True Image Home 2010 to back up my Windows xp installation (OS state) and it worked perfectly. 
Can [Back in time]("http://backintime.le-web.org/") do that for Ubuntu? :o
If not, is there any other GUI based and easy to use software like Acronis for Ubuntu? 

PS: Silly question:P... can I backup Ubuntu using Acronis in Windows? 
Did anyone tried this before?

---

### Post by armyofgayunicorns on 2011-01-24
the only reason you need special software like acronis to make a backup image of windows is that microsoft have made it deliberately difficult to copy windows from one hard drive, or one partition, to another, by putting files deep in the OS that are deliberately set up to be corrupted if you try to copy them from one place to another.  
This is because some (insert suitable profanity here) at microsoft thought it would somehow prevent people from putting one copy of windows on multiple computers. it doesn't, it only makes it pointlessly difficult to upgrade to a new harddrive without reinstalling everything.
ubuntu will happily just copy and paste from one hard drive to another, i've done this and it worked fine. i'd think all you need to do to create a backup image of ubuntu is create a compressed archive of your current ubuntu partition with something like 7zip.
Acronis will create backups of any OS as far as i know, as it just creates an image of the hardrive or the partition regardless of what's installed on it. unfortunately, when you want to restore that image, you can't restore it to a partition you've created to restore it to, it wants to wipe the entire hard drive then restore it, which is no use if you've got a dual boot setup.
 if you've got a compressed archive of your ubuntu partition, all you'd need to do is boot with the live disk, reformat your partition as ext4 with Gparted, then unzip/unrar the archive into that partition.

---

### Post by sudoer541 on 2011-01-25
So I guess there is no easy way to recover and restore and image of my Ubuntu hard disk? :o

---

### Post by bodhi.zazen on 2011-01-25
> **sudoer541 said:**
> Is it possible to backup my OS (OS state) using Back in Time? 
I am using Acronis True Image Home 2010 to back up my Windows xp installation (OS state) and it worked perfectly. 
Can [Back in time]("http://backintime.le-web.org/") do that for Ubuntu? :o
If not, is there any other GUI based and easy to use software like Acronis for Ubuntu? 

PS: Silly question:P... can I backup Ubuntu using Acronis in Windows? 
Did anyone tried this before?

Honestly, this concept is a hold over from your Windows days.

In Linux it is trivial to re-install the OS, so, IMO, you are far better off either backing up home or keeping a separate data partition.

Personally I keep a data partition with any data I value on it (it is actually a nfs share with autofs, so very convenient).

Other then that you only need a few config files (.bashrc, .zshrc, .vimrc and everything in .ssh and .gpg) and any system files you edit.

Want a fresh copy of Ubuntu 10.04 or 10.10 ? It is on the Desktop CD =)

---

### Post by djeikyb on 2011-01-25
> **armyofgayunicorns said:**
> the only reason you need special software like acronis to make a backup image of windows is that microsoft have made it deliberately difficult to copy windows from one hard drive, or one partition, to another, by putting files deep in the OS that are deliberately set up to be corrupted if you try to copy them from one place to another.  
This is because some (insert suitable profanity here) at microsoft thought it would somehow prevent people from putting one copy of windows on multiple computers.No, this is wrong. You can run a file system backup on windows just as easily as linux. The differences lie in how windows and linux treat open files. This is highly simplified, but when a file is open on windows, it's locked, and that's that. No other program can access that file. Leave a word doc open during a simple backup, it ain't getting backed up. Linux leaves the file alone until it's time to write to the file; you work with a temporary version of the file in memory.

Windows system state is a bunch of open files. So when you try and backup windows while its running, these files error, and you don't get a good system backup. Windows backup programs have a number of ways to solve this problem, but probably the best and most common solution is VSS. You can google this if you like.

Afaik, Ubuntu doesn't have any weird issues with live backups. Now, if you have a database running with constant writes, it'll get backed up, but in the state it was when the backup run. It may not (read, probably not) get an accurate picture of what the database is supposed to look like. Generally the database program will have a script or command that should execute before and after the backup that puts the database in a proper state to be backed up.

Full system backups and restores of an offline system should always work. Ie, turn off your computer, boot into a livecd, run a backup/restore of whatever OS you have on the hard drive.

EDIT:
Furthermore, the windows license may legally prevent you from moving the windows install from system to system, but practically speaking, the base windows install does not include drivers for every single system out there. Throw in some special raid equipment and you have the windows license coincidentally enforced.

---

### Post by djeikyb on 2011-01-25
**@bodhi.zazen**, I have to disagree. I understand how it could be trivial for some, even many people. And it is easy to reinstall the base Ubuntu OS. But what about all the programs you've installed beyond the base OS? It's a lot of bandwidth to apt-get all those programs. Furthermore, how do you get *all* the programs you had? I'd remember vim and screen off the top of my head, but the rest I wouldn't remember until I needed them, and then I'd have a delay for apt-get.

And sure, this may be annoying but acceptable in a home environment. But for a production environment? Hell no. You want to replace the hard disks, restore the backup, reboot, and continue with business as usual.

Personally, I backup /home, /etc, and /var (data, custom system configurations, important logs and website data; respectively). I'd back up /usr/local if I had space, but as with all the other directories, it falls in the "annoying but acceptable" category, because it's just my home computer.

---

### Post by bodhi.zazen on 2011-01-26
See this link:

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

---

### Post by sudoer541 on 2011-01-27
So, there is no easy way to backup ubuntu + its not worth it. I got it!:P

---

### Post by bodhi.zazen on 2011-01-27
> **sudoer541 said:**
> So, there is no easy way to backup ubuntu + its not worth it. I got it!:P

I would not go that far , lol

There are several methods to back up, "easy" is highly subjective.

Options include everything from dd to tar to rsync to partimage to clonezilla.

"not worth it", IMO, applies to the vast majority of system files, but again that is up to you.

Any personal data you have that you do not want to loose should be backed up. All hardware will eventually fail, the questions are when and do you have a working backup ?

When I started using Linux many years ago, I made backups as you are suggesting. Some of the backups are several Gb in size. Guess what those system files are worth today ? Nothing. All the packages are old, outdated, and unsupported.

The data on the other hand, family pictures and such, invaluable. That data fits on a few DVD.

---

### Post by dhysk on 2011-01-27
Depending on free time and avialable space, I'm not sure how big of an image you're currently making with your windows backup but you could back up both OS's at the same time into an image.

prepare a seperate partition external drive whatever than use something like clonzila to make an image of your drive.  This can take an houre or two but depending on how often you make a backup it may be doable.  However if you made an image of the whole drive with something like clonzilla than you would be backing up both/all OS's on that drive including grub and all.  This will take up quit alot of space depending on how big your drive is though.

---

### Post by djeikyb on 2011-01-27
Bacula is one program I've been hearing quite a bit of. Haven't used it myself.
[http://www.bacula.org/en/](http://www.bacula.org/en/)

Here's a list of free (speech/beer) linux backup programs:
[http://www.junauza.com/2009/01/7-best-freeopen-source-backup-software.html](http://www.junauza.com/2009/01/7-best-freeopen-source-backup-software.html)

There's always non-free commercial software, like Symantec, Yosemite Backup..

---

### Post by armyofgayunicorns on 2011-01-28
> **djeikyb said:**
> No, this is wrong. You can run a file system backup on windows just as easily as linux. The differences lie in how windows and linux treat open files. This is highly simplified, but when a file is open on windows, it's locked, and that's that. No other program can access that file. Leave a word doc open during a simple backup, it ain't getting backed up. Linux leaves the file alone until it's time to write to the file; you work with a temporary version of the file in memory.

Windows system state is a bunch of open files. So when you try and backup windows while its running, these files error, and you don't get a good system backup. Windows backup programs have a number of ways to solve this problem, but probably the best and most common solution is VSS. You can google this if you like.

Afaik, Ubuntu doesn't have any weird issues with live backups. Now, if you have a database running with constant writes, it'll get backed up, but in the state it was when the backup run. It may not (read, probably not) get an accurate picture of what the database is supposed to look like. Generally the database program will have a script or command that should execute before and after the backup that puts the database in a proper state to be backed up.

Full system backups and restores of an offline system should always work. Ie, turn off your computer, boot into a livecd, run a backup/restore of whatever OS you have on the hard drive.

EDIT:
Furthermore, the windows license may legally prevent you from moving the windows install from system to system, but practically speaking, the base windows install does not include drivers for every single system out there. Throw in some special raid equipment and you have the windows license coincidentally enforced.

I've only tried it from a live cd, tried it from a xubuntu live cd, tried it from my ubuntu installation on a separate harddrive, and tried various methods from various other rescue cds.

Whenever i've tried to copy a windows installation to another drive, unless i've used disk imaging software like acronis, the copied windows installation (XP) has been unbootable because of missing or corrupted files. perhaps this is no longer the case with vista or windows 7, but it is definitely the case with XP

---

### Post by sudoer541 on 2011-01-28
> **bodhi.zazen said:**
> I would not go that far , lol

There are several methods to back up, "easy" is highly subjective.

Options include everything from dd to tar to rsync to partimage to clonezilla.

"not worth it", IMO, applies to the vast majority of system files, but again that is up to you.

Any personal data you have that you do not want to loose should be backed up. All hardware will eventually fail, the questions are when and do you have a working backup ?

When I started using Linux many years ago, I made backups as you are suggesting. Some of the backups are several Gb in size. Guess what those system files are worth today ? Nothing. All the packages are old, outdated, and unsupported.

The data on the other hand, family pictures and such, invaluable. That data fits on a few DVD.


I guess you're right. 
I upgrade my Ubuntu OS every six months anyway. 
I am using Windows most of my time now, and am kinda got used to it. 
I used Acronis to backup my OS state along with all the tweaks that help to make the OS faster and I am very glad I did it! :P
My files are backup also backed up.

---

### Post by djeikyb on 2011-01-28
> **armyofgayunicorns said:**
> I've only tried it from a live cd, tried it from a xubuntu live cd, tried it from my ubuntu installation on a separate harddrive, and tried various methods from various other rescue cds.The Master Boot Record (MBR) is not part of the file system. You need to back it up and restore it separately. This is the same, whether it be Linux, Netware, Windows, BSD.. The easiest diy way with Windows, imo, is to restore the file system, then boot with your Windows disk and "fix" the MBR following the gui instructions. With Ubuntu, once you've got the file system restored, use a livecd to boot into your restored Ubuntu system, then reinstall grub.

And to clarify, the thing that is most wrong about your post is attributing malice to Microsoft. In this case, it's more about the system architecture they chose rather than intentionally blocking full system backups.

EDIT: A disk imaging program like dd or Acronis or Clonezilla works for a full system backup because they aren't concerned as much with backing up individual files as they are with each and every sector of the hard disk. Thus, they get the MBR backed up because they started the backup at sector zero of the hard drive instead of file one of partition one.


**@bodhi.zazen** - Sweet. Getting a list of installed packages that apt-get can use later makes things suck a lot less.

---

### Post by armyofgayunicorns on 2011-01-30
fair enough, cheers for clarifying, though that is still just one thing that can be ticked off a very long list of deliberately crap things microsoft have done:p

---

### Post by djeikyb on 2011-01-30
Haha, yeah..I have my own long list of reasons I don't like using Microsoft. This topic caught my eye because I have a little professional experience with backups in general. No coding experience, just some basic knowledge of the structure of backups on various platforms. But I agree, MS does a lot of wonky things, and they restrict rather than free their users in many cases.

All in all, I'd rather use Linux. I love [the mutt mail program's motto]("http://www.mutt.org/"): "All mail clients suck. This one just sucks less." Applies nicely to operating systems too.

---

