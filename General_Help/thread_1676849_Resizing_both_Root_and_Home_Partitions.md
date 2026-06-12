---
title: "Resizing both Root and Home Partitions"
date: 2011-01-27
forum: General Help
---

### Post by SuperFreak on 2011-01-27
I realize a lot has been discussed on this subject so forgive me if I am asking things to be repeated; I did a search but only found information on resizing one partition.
What I want to do is enlarge both my root partition by about 10 GB and also enlarge my Home partition by about 45 GB. I realize there is enough space in the root partition for expansion (see screen shot) but I want to be certain (some of the last updates have been over 100 MB). I have a dual boot 10.10 64 bit system with XP . There are two drives ; a 1 TB drive with Windows, Ubuntu and a NTFS data partition and a 2 TB drive for media which won't be touched by this operation. I have taken about 58 GB from my Windows partition and this now sits unallocated and ready to be used to expand the Ubuntu partitions. 
Any help expanding these partitions (root and home) would be appreciated. I read bodhi.zazen' excellent tutorial on partitioning ([http://ubuntuforums.org/showthread.php?t=282018&highlight=bodhi.zazen](http://ubuntuforums.org/showthread.php?t=282018&highlight=bodhi.zazen)) but I still am unsure how to go about this. I have a live Meerkat CD.

---

### Post by oldfred on 2011-01-27
Be sure to have good backups.

You have to use a liveCd so the partitions are not mounted and you may still have to do swap off on the swap partition to unmount the extended partition.

You need to first move the extended partition into the unallocated. Then you can move the root partition left. I do not like moving root partition left but it should work. Since you are just moving the UUIDs should not change, but you may have to reinstall grub. You can also expand / after moving and move or expand /home.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by SuperFreak on 2011-01-27
OK I have already backed up my files.
I rebooted with the live CD of 10.10 and went into Gparted.
I turned off swap
I then increased the size of the Extended partition and used up all of my unallocated space. Applied the change.
I received an error message immediately indicating the applied change could not be made, so I canceled the change and turned swap back on and exited the live cd.
Fortunately I am still able to boot into Ubuntu as normally and the Grub menu seems intact.
I am a little concerned about what you said about the Grub menu needing to be reinstalled. Will this affect windows or just Ubuntu?
I am going to leave this for the night, but I will try again later

---

### Post by SuperFreak on 2011-01-28
As I want to enlarge two partitions both Root and Home I am wondering if this may present a problem. My understanding is that the unallocated space must be right next to the partition that is to be enlarged. In my case (see screen shot) the unallocated space is next to Root but not Home. Will this prevent me from being able to expand home once Root is enlarged?

Can anyone clarify why my Grub may need to be installed with these operations and how I should prepare for that?

---

### Post by oldfred on 2011-01-28
To expand a partition left, you first have to move it then expand it right. Moving can be a very slow process, depending on how much data has to be moved.

If you move the root partition, grub may need to know that the partition location has changed. If you move root left,  then all the free space is between root & /home so you can then expand root into half of it and then move /home left and then expand it right. I would of course do all of this in small steps and check that system boots.

If you do not touch windows partition, it should not cause any issues with windows, but again, this is why we want to have good backups.

What was the error message?

---

### Post by SuperFreak on 2011-01-28
I am afraid I did not record the error message. I will try again tomorrow afternoon . Thank you for your help on this, I am beginning to understand. When I expand Root I expand it the entire 58 GB and apply the operation. I then expand my Home partition 45 GB into free space of the Root partition. 
I have found this discussion of reinstalling Grub [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD). I assume I am correct in thinking I have Grub 2 as my OS is 10.10.

---

### Post by Irony on 2011-01-28
I've always found it far faster and totally error proof to copy everything (including my install) to an external drive. Then format the drive to the correct sizes and then copy the back up copies back.

Resizing takes forever and seems prone to many errors.

---

### Post by oldfred on 2011-01-28
+1 on Irony's suggestion.

I prefer to just reinstall the operating system. You already have a separate /home and backups. If you export a list of installed apps you can reinstall very quickly, mounting but not reformating your existing /home.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
List packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

---

### Post by Irony on 2011-01-29
> **oldfred said:**
> +1 on Irony's suggestion.

I prefer to just reinstall the operating system.
I should point out I don't reinstall the system I just copy it back using a copy command;

```
sudo cp -ax /folder1/. /folder2/.
```

---

### Post by SuperFreak on 2011-01-29
Irony,

I was thinking that this was turning out to be a little more difficult than I anticipated. If I expand the partitions I risk errors. If I reinstall the OS and Home then I lose all my configuration settings in individual programs, my desktop icons and settings and a few programs that were installed (with some difficulty ) manually.
I am intrigued by this option of backing up everything and copying it back on a newly formatted drive. Could you either direct me to a step by step set of directions or more fully explain the copying process. What program should I use to copy my root and Home partitions to an external hd and what steps do I take to get everything back the way it was.
I am fairly new at Ubuntu, having unsucessfully installed and run previous versions of Ubuntu ; Meerkat is the first time I am able to use it without constantly booting back into windows to run programs that Ubuntu won't run. If it looks too daunting I will wait until Natty Narwal comes out and do a fresh install.
I am open to suggestions.

---

### Post by oldfred on 2011-01-29
All your user settings are in /home which also has your data unless you are storing it to another partition. If you have made any manual system configurations those would be in /etc. But do not just reinstall any files from /etc if an upgrade as the settings may be different.

You also may want to export a list of installed applications so you can just reinstall them. If an upgrade it will install the newer version.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

I use rsync to backup. It saves ownership & permissions if you copy to a linux partition. If you copy to FAT or NTFS you lose settings and have to manually reset them.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)

Some recommend these to make an image backup:
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

You should create a separate /home to make it easily to reinstall.

To move /home uses rsync  (create mount step may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

---

### Post by Irony on 2011-01-30
Simply use the copy command; [http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

Note you can test out the command locally by creating 2 folders on your desktop folder1 and folder2 and creating a text file in folder1 then do;

```
cp -ax ~/Desktop/folder1/. ~/Desktop/folder2/.
```

You will now see that folder2 has the text file.

---

### Post by SuperFreak on 2011-01-30
I was able to copy the Root Partition to my external drive with the copy command but not my Home Partition. I was on my local machine ; do I need to be doing this from the live CD?


Edit: I accidentally copied the Home partition into the same folder as Root. I started over(reformatted) again and it seems to have worked except one thing. In the Root partition on my hard drive there is a folder called proc with hundreds of folders numbered sequentially. On my external Hard drive the root folder has this folder proc but it is empty.

2nd edit: There are some other empty folders in the external hd root folder including home,dev and sys - I haven't looked at subfolders or hidden folders

I am reluctant to use these backups as there are folders/files missing

---

### Post by Irony on 2011-01-31
The command;

```
sudo cp -ax
```

works fine, don't worry about 'empty' folders such as proc it only has something in it when you are booted into it. If you look at your proc folder from a live CD you will see that it is empty - [http://www.linux.com/archive/feature/126718](http://www.linux.com/archive/feature/126718)

I've used the command hundreds, perhaps thousands of times without fail - in fact a few days ago I moved my install from sdb3 to sdb2 using it.

You can use the command either from a live CD or when booted into your install. For example to copy my install to an external disc I boot into my install and do;

```
sudo cp -ax /. /media/externaldisc/.
```

---

### Post by SuperFreak on 2011-01-31
OK Irony 
it looks straightforward but before I reformat my partitions how do I specify the partitions that Root and Home go to? Each will go into a separate partition, but I am not sure how Linux designates an empty formatted EXT4 partition in Terminal. Also do I create a folder first in those partitions or are the contents of the folders Home and Root put on the new partitions?I understand I use the sudo cp -ax command but I am not sure how I specify the specific partition it goes to. Sorry to be such a N00b but I am not overly familiar with terminal and if I make a mistake here it will be costly.

Edit: See your link to [http://shallowsky.com/blog/linux/install/upgrading-without-risk.htm](http://shallowsky.com/blog/linux/install/upgrading-without-risk.htm) which explains it in more detail.
Thanks for your help Irony

---

### Post by Irony on 2011-02-01
A mistake shouldn't be costly because you will have backed up everything to an external drive...

The command;

```
sudo cp -ax /. /media/folder/.
```

copies the *contents* of the folder, not the folder itself. As I said earlier you can practice this command on your desktop with some local folders to see how it copies the contents.

Thus once you've backed up everything to an external drive you can then use a live CD to format your drive into root and home (don't create these as folders otherwise you will have root within root and home within home).

With the live CD you can use gparted to format the partitions (you can give them a label name say ROOT and HOME to make them easy to find). Once that is done go to menu places and find those menu names and open them, they will show up as /media/ROOT and /media/HOME.

Then do;

```
sudo cp -ax /media/folder1/. /media/ROOT/.
```

```
sudo cp -ax /media/folder2/. /media/HOME/.
```

I guess if you want root and home separate you will have to separate them first then add an entry in fstab for home after copying.

---

### Post by SuperFreak on 2011-02-01
I have decided that I have enough room on my partitions to get to the next release of Ubuntu. However the thread has been very helpful; I now have a complete backup of both my Root and Home partitions and will know how to do this in the future. I also have the detailed instructions on how to reinstall my partitions and with the links Irony provided I will be able to make any changes to Grub and FSTAB that may be necessary in the reinstall.
Thanks also to oldfred who gave valuable information on backing up settings.
I will mark this as SOLVED

---

### Post by SuperFreak on 2011-02-28
Realize this may go unanswered as I marked the thread solved but one last question. If I reformat ROOT and HOME and then resize and copy everything back into those partitions what will happen to XP. Do I need to fix the MBR and if so at what point should I do this.

---

### Post by oldfred on 2011-02-28
You may have to reinstall grub2 to the MBR. It depends on what has changed. If restoring exactly the same it may still work.

---

### Post by SuperFreak on 2011-03-01
I have used the copy commands Irony recommended with some success. I had to modify the etc/fstab file to get Ubuntu to boot. Also my email program had to be rebuilt from a saved configuration, destop had to be tweaked from default appearance to the way I liked it and Firefox had to be updated to my preferences by reinstalling a FEBE profile I saved before starting this process. 
All in all I am satisfied with one issue I am not certain of how to correct. I had a dual boot with XP and now XP is not a choice in the grub menu. I don't want to hastily make any more changes without help. Is it a matter of running the xp disc and choosing repair option followed by FixMBR? If someone could explain how to get Windows back as a dual boot with Ubuntu I would appreciate it.

---

### Post by oldfred on 2011-03-03
First try this:
```

sudo update-grub
```

If that does not work post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

The fixMBR command writes the windows boot loader into the MBR overwriting grub2's boot loader. You can do that to test if windows boots, but will then have to reinstall grub2 to the MBR. Sometimes fixBoot, chkdsk or other commands are required and boot script will help in figuring out what to do.

---

### Post by SuperFreak on 2011-03-03
Thanks,

I should have posted this a few days ago as I already tried sudo update-grub and it restored XP on boot.

---

