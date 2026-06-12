---
title: "Disk Space"
date: 2010-03-26
forum: General Help
---

### Post by aequistas on 2010-03-26
Hello,
 
I am windows and ubuntu user on the same computer. I have loaded ubuntu in the windows on a separate drive named as G: . According to requiritments it says i need 8 GB max, My drive has 20 GB anyway. I have loaded ubuntu , i got into it and looked at the space it has , it shows a few GB but later on i got in to Windows but it shows 17 GB is filled. Both of them are showing different folders too. Different values about hard drive too. What is the problem with this? I looked at the file which gets GBs is root.disk file , it is 17 GB... Why both of them show different? and does it have any harm for my hard disk? Can this cause my hard disk to be broken or have bad sector or ETC.?
 
Thank you.

---

### Post by aequistas on 2010-03-26
Still UP...dont want my question to be gone...

---

### Post by aequistas on 2010-03-26
up..

---

### Post by garvinrick4 on 2010-03-26
> **aequistas said:**
> Hello,
 
I am windows and ubuntu user on the same computer. I have loaded ubuntu in the windows on a separate drive named as G: . According to requiritments it says i need 8 GB max, My drive has 20 GB anyway. I have loaded ubuntu , i got into it and looked at the space it has , it shows a few GB but later on i got in to Windows but it shows 17 GB is filled. Both of them are showing different folders too. Different values about hard drive too. What is the problem with this? I looked at the file which gets GBs is root.disk file , it is 17 GB... Why both of them show different? and does it have any harm for my hard disk? Can this cause my hard disk to be broken or have bad sector or ETC.?
 
Thank you. Can you boot into Ubuntu? Did you use WUBI?

---

### Post by aequistas on 2010-03-26
Whenever i start my computer, I am having 2 choices of operating system if this is what you mean by booting. One of them Ubuntu , one of them Windows. Whichever i choose i start with... And I have loaded ubuntu in windows.

---

### Post by aequistas on 2010-03-26
I really need a quick answer so I will continue using ubuntu or uninstall it

---

### Post by aequistas on 2010-03-26
Question is still up.

---

### Post by aequistas on 2010-03-26
Up..

---

### Post by 3rdalbum on 2010-03-26
You used the Windows-based installer, didn't you? The way this works is by making a file on the hard disk, and putting Ubuntu inside this file. (that's "root.disk").

This is certainly not an optimal way of using Ubuntu, especially since you're happy giving it an entire disk. I'd recommend you remove Ubuntu using Windows' "Add/Remove Programs", then set up your computer's BIOS to boot up from CD, and then use the "Install Ubuntu" option at the main menu of the CD to boot up Ubuntu and run the Ubuntu-based installer.

To answer your related question, the way Ubuntu is installed will not "cause bad blocks" or damage your disk in any way. However, if Windows stops working for whatever reason, you will probably find that you can't boot into Ubuntu either. Not good. If you use the Ubuntu-based Ubuntu installer you will not have this limitation.

EDIT: Considering that you can use Ubuntu and Windows perfectly well, this was not something where you "really needed a quick answer". If somebody who is online at the time can help, they will reply. If they can't help, they won't reply. Also, Ubuntu Forums is not the only support channel; there's also the #ubuntu IRC channel on irc.freenode.net, which you can access from the Empathy instant messenger, and the people on there may be able to give you quick suggestions.

---

### Post by bolucpap on 2010-03-26
aequistas, please realize people who post into those forums are not support staff, they are doing it to help people out using their own free time. Posting a "bump" message every hour to keep your alive is also bad etiquette. Normally people are urged to wait 24 hours if they receive no answers to their question.

Also, I think "help me or I'll uninstall Ubuntu" is a ridiculous threat, for what it's worth. Nobody here has a vested interest in you using this particular OS, other than a general wish that FOSS is more prevalent.

---

### Post by sdowney717 on 2010-03-26
Wubi installer creates a single very large file. MS Windows will see it as a single large file when running MS Windows. Wubi Ubuntu basically takes that space for itself to work with. That single file contains all the ubuntu files. When Wubi Ubuntu is running, it does not see itself as a single large file, it just sees itself as a whole bunch of smaller files.
So running like this its going to look like the drive is different running windows versus ubuntu. Depends on which perspective and which OS is looking at the drive.

It wont harm your disk. What can cause problems is if your disk truly fills up all the way. Then it has to work harder looking for free space. Disks simply do wear out just by use. Typically the platter bearings get loose, then the tracks dont line up, the disk tracks are harder to read, the drive heads have to work harder rereading sectors, it gets hotter, it slows down. If it cant read sectors, it has internal self monitoring and will start marking them as bad, locking them out. If your data is on those sectors, it is gone. Bearings are better today. They use fluid dynamic platter bearings, they are quiet and last longer. I have some older drives that just make a racket, the bearings are noisy. But my newer huge drives 500 to 750 GB are super quiet.

---

