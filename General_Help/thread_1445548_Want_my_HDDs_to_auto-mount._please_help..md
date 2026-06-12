---
title: "Want my HDDs to auto-mount. please help."
date: 2010-04-02
forum: General Help
---

### Post by kokkus on 2010-04-02
Hey. In order to mount my HDDs now I have to click on its icon and type in my password. I want them to be mounted automatically so I don't have to type in the password for every time I use the disks. How do I solve this problem.

---

### Post by ram2500 on 2010-04-02
You can edit fsck if you are comfortable editing configuration files, but it's not recommended. I have had personal disasters trying to have a partition automount, so I would recommend pysdm, which does the work for you and isn't as dangerous (and difficult). I wish I knew about pysdm sooner!:)

---

### Post by CharlesA on 2010-04-02
fsck?

You can set stuff to automount in fstab. The syntax is listed in /etc/fstab

---

### Post by ram2500 on 2010-04-02
I switched fsck and fstab around;)
The package pysdm will customize your fstab for you.

---

### Post by kokkus on 2010-04-02
thanks guys but that program destroyed my fstab file.
Why the fuuck isn't it possible to auto mount the disks without any problems.
This is one of the things I think is damn frustrating with ubuntu.
You have to be a freaking pc expert to do a simple task.
Things like this are not a problem in windows.

---

### Post by kokkus on 2010-04-03
Is it possible to do this without editing the fstab file ?
Or if not, how do I solve this problem?

---

### Post by sisco311 on 2010-04-03
> **kokkus said:**
> Is it possible to do this without editing the fstab file ?
Or if not, how do I solve this problem?

Nope, pysdm is a GUI tool for editing fstab.

What's the output of:
```
cat /etc/fstab
sudo blkid
```?

---

### Post by CharlesA on 2010-04-03
The only way you could do it without editing the fstab file is to mount the drives manually.. which isn't what you want to do.

---

### Post by kokkus on 2010-04-03
ok why won't I do that? Will it destroy stuff?
Which brings me back to what I said earlier. 
Things like this should be easier to do. Hard drivers should mount automatically from boot. You don't have problems like this with Windows. so why does it have to be so hard in Ubuntu?
This is how it should be. You know when you click on the disk icon to mount it, there should be an option there that allows you to auto mount the disk.
I mean common, is it really that hard for the ubuntu developers to fix this problem?

---

### Post by kokkus on 2010-04-03
The mount but I have to type in a password to activate them.
So how do I fix it so that the devices will be activated automatically when I boot into ubuntu?.

---

### Post by mc4man on 2010-04-03
If you're running karmic and are the admin user then it would be  easy to eliminate the need to enter a password for mounting internal filesystems (drives, partitions ect.

This was an unfortunate choice for karmic that has been rectified in lucid but not as yet in karmic.

I think it's better this way than to create fstab entries.
Let me know if so..

---

### Post by bigsmitty64 on 2010-04-03
Your sig coupled with this post made me chuckle a lil bit! :)


You have to be a  freaking pc expert to do a simple task.
Things like this are not a problem in windows.
		                   		  		  		 		 			 				______________________________
				[B][COLOR=Blue]---->PC is easy, fun and friendly when you use  Ubuntu<---------

[/COLOR][/B][COLOR=Blue]
[COLOR=Black]Its true, but can def be frustrating!!!![/COLOR][/COLOR][B][COLOR=Blue]
[/COLOR][/B]

---

### Post by mc4man on 2010-04-03
I gotta run so here - THis is for karmic only, and only grants auth for the admin user

In a terminal run this to create the proper file - use copy and paste to avoid mistakes, 

```
gksudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/org.freedesktop.DeviceKit.Disks.pkla
```

gedit will open a empty file , paste this in and save, that's it..

```
[No password required for admins]
Identity=unix-group:admin
Action=org.freedesktop.devicekit.disks.filesystem-*;org.freedesktop.devicekit.disks.change-system-internal
ResultActive=yes

```

---

### Post by kokkus on 2010-04-03
Thanks but that doesn't mount the disks. it disables the password when I click on the disk icon to mount the disk.
What I want is something that will auto mount the disks when I boot into ubuntu.
Because now I have to click on the hdd icon to mount them.

---

### Post by gadolinio on 2010-04-03
I have all my HDDs mounted automatically when i boot, with a program called disk-manager.
You can download it from [http://packages.ubuntu.com/search?disk-manager](http://packages.ubuntu.com/search?disk-manager) (the package is for intrepid, but it also works in jaunty).
Once you have installed it, it will be in system-->administration-->disk manager. (you'll be asked for your password).
It's easy to use. In the tab on the right you can tick each drive/partition to be automatically mounted since startup. You can also edit other things, such as read and write permissions for NTFS drives, if you need to do so.

---

### Post by kokkus on 2010-04-03
Thank you so much but that website you liked me to didnt have a deb installation.
But I found one.
Finally, this solved the problem and it was easy too.
Thank you very very much everybody:)

---

### Post by BrokeMahPC on 2010-04-03
Glad you got it sorted out but one reason I like Ubuntu is being able to  grab the functions of your PC by the short n curlies. Editing something  like fstab may seem an odd and difficult thing to do to a traditional  windoze user, but, windoze seems designed to keep you helpless. Have a  go at fstab and learn something new:
read this first:  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
and this:  [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
good read on PySDM  here: [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

[COLOR=MAROON][B][COLOR=Red]Before modifying any system file, it  is good  practice to make a backup copy![/COLOR]
[/B][COLOR=Black]Typing  this in a terminal will make a copy of fstab called fstab.bak01, you  can make further copies as you edit but assign them new numbers so you  can work backwards if you make a mess of things. sudo is the command  that gives you permission to run a command on protected system files, it  will ask for your password.
code:
sudo cp /etc/fstab  /etc/fstab.bak01

**Create a mount point**[/COLOR][/COLOR]
I'm  not sure this is still necessary but it does no harm to have the mount  point already in existence.
code:
sudo mkdir /media/storedb4

Call  it anything you like - I chose storedb4 but it must be in /media

**Editing  fstab**
In the newer versions - 9.10 and 10.04 it's best to use  the uuid method
Open a terminal and list your devices by uuid
code:
sudo  blkid

Record the details of the partition you want to automount,  eg:
/dev/sdb4: LABEL="sdb4"  UUID="68d769f8-9ca3-4887-815a-d3bcade89230" TYPE="ext4"

Now open  fstab in a text editor.
code:
gksu gedit /etc/fstab

Here is  the line I added to my /etc/fstab to make the partition auto mount:
#/dev/sdb4
UUID=68d769f8-9ca3-4887-815a-d3bcade89230  /media/storedb4 ext4 rw,suid,dev,exec,auto,nouser,async 0 0

The  bit after the # isn't read so you can type a note here to identify your  entry for future reference.
/media/storedb4 creates a mount point  under /media in the filesystem called storedb4 but you can call it  anything, eg: /media/data. If you created a mount point above, make sure  the two entries are the same.
When you have finished editing save  and close gedit.

**Testing your new fstab**
There is no  need to reboot to test your new fstab. In a terminal type this to mount  everything listed in the fstab.
code:
sudo mount -a

The  partition should mount and an icon appear on your desktop.

**Restoring  the old fstab:**
[COLOR=MAROON][COLOR=Black]You can  replace the new fstab  with the backup using [COLOR=Red](this will delete the new fstab  permanently!)[/COLOR], 
code:
sudo mv /etc/fstab.bak01 /etc/fstab
    
[COLOR=Red][COLOR=Black]The command[/COLOR][/COLOR] mv  (move) moves or in this case renames the file and deletes the file it  replaces. If you want a windows  like method to do the above try this in a terminal,
code:
sudo nautilus

This will allow you to navigate, delete and rename system files with the  mouse and the usual nautilus file manager. Of course be careful what  you do with this, don't delete anything you shouldn't![/COLOR][/COLOR]

---

### Post by CharlesA on 2010-04-05
Just a note: I have my mountpoints off of the root directory. Didn't have the change anything in fstab, only had to chown the folders I was using as mountpoints.

Any reason to use /media/ instead?

EDIT: You use gksu instead of sudo when running graphical apps - permissions issues can occur otherwise.

---

### Post by gadolinio on 2010-04-06
> **kokkus said:**
> Thank you so much but that website you liked me to didnt have a deb installation.


You have to click the link that says "intrepid", and in the following page, go to the bottom and there's a link that says "all" (meaning all architectures). It takes you to another page where you have a lot of places to download from; just click any of those links and a dialog will apear to download the .deb file.
Enjoy!

---

