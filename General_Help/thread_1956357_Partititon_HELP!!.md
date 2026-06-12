---
title: "Partititon HELP!!"
date: 2012-04-10
forum: General Help
---

### Post by benj23673 on 2012-04-10
[http://i42.tinypic.com/xmlxtc.png](http://i42.tinypic.com/xmlxtc.png)

I dual boot windows and ubuntu recently I had to fresh restart my ubuntu and it says I have like 9gigs of hard drive space but when I did it the first time I gave 100gigs of drive space above is picture of my gparted can someone explain why it says that I have 9gigs or if I really do only have 9gigs how to make it so I can access the rest

---

### Post by PhantomTurtle on 2012-04-10
What did you do with /dev/sda5? It has all of that extra space. It is even partitioned with ext4, what do you do with that?

---

### Post by bashphoenux on 2012-04-10
looking at the screenshot you do have 100gigs allocated for ext4 but only 15 gig for '/'
you might have to reinstall ubuntu and allocate all of the 100gig etx4 that you partitioned to '/'

---

### Post by Ishimaru Chiaki on 2012-04-10
Hello,

Next time you reinstall ubuntu, I suggest you to separate you home from the system partition, for if the system partition crashes, your home won't be messed up.
It happened to me once, thanks God I had thought about putting my home on a separate partition, for I could backup it before reinstalling ubuntu.

Actually, if you separate the home partition, 10 GB would be largely enough for the system partition for it is your personal data (music, vids, photos) that is likely to take many bytes.

---

### Post by benj23673 on 2012-04-11
Ok so what happened was, I had the 100 gigs to the first install of ubuntu but then after messing with the unity launcher I was no longer able to log in to my "main" account so I reinstalled following the directions from a previous thread I made ([http://ubuntuforums.org/showthread.php?t=1953578](http://ubuntuforums.org/showthread.php?t=1953578)) but now I see I really goofed up. Is there any advice on how to go about this can I make the partition larger after deleting the sda 5 via windows and if not can I save all the files/apps/settings from my ubuntu (sda 3) then reinstall them later? 

Basically what I need is to make the 100 gig partition for the sda 3 with out losing all the apps/files of ubuntu can it be done?

I am kinda new to all of this

---

### Post by benj23673 on 2012-04-11
I thought I used the sda 5 for ubuntu. Now it is just sitting there anyway I can make ubuntu run off it again? or at least use it to store files in?

---

### Post by jadtech on 2012-04-11
if the partition is there you should be able to mount it and do what ever you  
like with it I would think . i beleive you will have to be comfortable working in term  thought and commands

---

### Post by benj23673 on 2012-04-11
If I delete that partition via windows can I make the partition I currently use larger?

---

### Post by oldfred on 2012-04-11
Do not use Windows to delete Linux partitions. Use Windows tools for Windows and Linux tools for Linux. Although sometimes Linux tools will work better on Windows but not always.

You cannot use gparted to modify mounted partitions or any partition in the extended partition if any other logical partition is mounted. Use gparted from a gparted liveCD or your Ubuntu liveCD. Sometime you have to also swapoff, but it looks like you encrypted your /home so swap is encrypted.

You need to backup /home which will have all your user settings,  and export a list of installed applications if you have installed lot to make it easier to reinstall. Setting for the apps will still be in /home.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings) including keys in ~/.gnupg
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

If reinstalling this is my suggestion (amoung many), everyone has different ideas on partitioning and none are wrong as everyone has different needs.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by benj23673 on 2012-04-11
Ok, so I don't mess anything up further which seems to be what I am excellent at. I will back up all my files and applications, then I will use gparted from a live CD to delete /sda4 and sda3 then I will reinstall all my apps/settings and pretend like this whole thing never happened?

---

### Post by hal8000 on 2012-04-11
Your partitions are in the wrong order.
Follow old Fred's advice and his suggestions for partioning are a good idea as well (although no-one is wrong as we all have different needs).

The only thing I will add is that you can only have 4 primary partitions,
sda1,sda2,sda3,sda4.

If you require more partitions, then one of the primary partitions must be made an extended partition (which will act as a container for all logical drives e.g. sda5 onwards). 

Certain OS must be installed on primary partitions, e.g. Windows, FreeBSD and MacOSX.

Backup all your data as mentioned in the other posts, then delete the partitions and start again.

In my experience, I only save my own work, documents, config files, images etc.
I always find that a fresh install is much quicker than an upgrade
and typically less than 30 minutes with Ubuntu.

---

