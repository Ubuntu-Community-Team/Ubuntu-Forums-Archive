---
title: "Get rid of HDD icon on desktop"
date: 2009-11-11
forum: General Help
---

### Post by stieg on 2009-11-11
So this should be a pretty a pretty simple task, yet I can't seem to solve it to save my own life.

I have Karmic installed.  I installed a new HDD (sata2 internal drive).  I created a mount point for it in /etc/fstab so it mounts to a directory in my home directory. It mount properly every time and works great.  Here is the line from my fstab file...
```
UUID=868fed20-43e8-42d2-a2bf-dea4f58dc60e /home/foobar/space ext4 defaults	  0	  0
```  
The problem is that this new drive also shows up on the desktop.  While that is nice, I don't want that because its already mounted under my home directory.  So I want to get it off of my desktop.

I have seen the solution (in about 40 different places) where I can make all volumes invisible by changing the configuration in 
```
gconf-editor, uncheck /apps/nautilus/desktop/volumes_visible
```  However I don't want to disable that because I like having temporary drives (like thumb drives) pop up on the desktop.

So is there a way to prevent my new HDD from appearing on my desktop without disabling volumes_visible in gconf-editor?

---

### Post by ninjapirate89 on 2009-11-11
As far as I know that isn't possible. It's an all or none kinda thing.

---

### Post by stieg on 2009-11-11
> **ninjapirate89 said:**
> As far as I know that isn't possible. It's an all or none kinda thing.

Hrmm... then how do they keep the drive where root is mounted (or any other set of partitions) off of the desktop.  I know when I installed the system I had 3 drives setup in a RAID 5.  None of those drives appear on the desktop.  There must be some way to achieve this.

---

### Post by ninjapirate89 on 2009-11-11
I'm not entirely sure. On my computer I have 1 internal and 1 external hard drive. The internal is partitioned into three (Ubuntu, Win 7, and some reserve partition for win7) and the external is unpartitioned. If I mount any of these they show up on my desktop.

---

### Post by PrarieD0G on 2009-11-11
> 
[**update**]
 Want to keep shortcuts to some partitions but not others? Follow the other directions, and then and can create your own launchers for the partitions you want. 
 Right click on the desktop and click *Create Launcher*. In the *Type* drop down box, select location. Then you can give the launcher a name and the location you want to link to. You can find the hard drive icon in *usr/share/icons/gnome/scalable/devices/* if you want to use it. The resulting launcher will act just like the ones that you removed in this post.
   Source: [http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/](http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/)

Pretty much just a workaround, not an exact solution. But it should get you what you want.

Another idea is to add the icons to one of your panels (assuming you use panels). Right click on one of them. Choose "Add to Panel" then click "Disk Mounter." That will show all your mounted disks in the panel.

EDIT: nvm, I guess the first option isn't quite what you want, because the shortcuts stay on the desktop even when you disconnect the device(s). Sorry I couldn't really help.

---

### Post by ErwinC on 2009-11-11
Look for Ubuntu tweak in de repos....

Or visit [http://ubuntu-tweak.com/about](http://ubuntu-tweak.com/about)

---

### Post by Primefalcon on 2009-11-11
alt+f2

```
gconf-editor
```

aps -> nautilus -> desktop

unticking volumes visible will remove the drives from your desktop, but you'll still be able to see them in your places menu and in your computer location.

Hope that is what you were looking for

---

### Post by PrarieD0G on 2009-11-11
> **Primefalcon said:**
> alt+f2

```
gconf-editor
```aps -> nautilus -> desktop

unticking volumes visible will remove the drives from your desktop, but you'll still be able to see them in your places menu and in your computer location.

Hope that is what you were looking for
  If you're not sure, it always helps to read the OP, hehe. He mentioned that he already knew of that fix, but wanted something slightly different. Just saying...

---

### Post by Ozzman on 2009-11-11
EDIT: After searching around for some time I was able to find this solution to both our problems.

[http://georgia.ubuntuforums.org/showpost.php?p=7231762&postcount=8](http://georgia.ubuntuforums.org/showpost.php?p=7231762&postcount=8)

also find and replace in gedit worked very well for editing my many fstab entries (make sure to leave cdrom as media).

Clean elegant perfect solution :-) goodluck

EDIT2: as Stieg pointed out, the drives must be mounted to /mnt to not show up on the desktop..

---

### Post by stieg on 2009-11-11
> **Ozzman said:**
> EDIT: After searching around for some time I was able to find this solution to both our problems.

[http://georgia.ubuntuforums.org/showpost.php?p=7231762&postcount=8](http://georgia.ubuntuforums.org/showpost.php?p=7231762&postcount=8)

also find and replace in gedit worked very well for editing my many fstab entries (make sure to leave cdrom as media).

Clean elegant perfect solution :-) goodluck

Ozzman, thanks for the post.  I came across that too in my searching and tried it.  Unfortunately it did not solve the problem.

And just to clarify again, I am NOT looking to disable volumes_visible (as pointed out in primefalcon's post).  I still want that.  I just don't want my internal HDDs to show up on the desktop.

There has to be a way to do this.  I tried looking in the udev rules but did not see anything.  *sigh*

EDIT:  
   I screwed up and Ozzman nailed it.  You HAVE to mount the drive under /mnt (and no where else) for it not to show up.  If you mount it anywhere else, the drive will still appear on the desktop.  Thanks Ozzman!  That fix is much better than disabling all the volume icons.  :D

---

### Post by Ozzman on 2009-12-12
> **stieg said:**
> 
EDIT:  
   I screwed up and Ozzman nailed it.  You HAVE to mount the drive under /mnt (and no where else) for it not to show up.  If you mount it anywhere else, the drive will still appear on the desktop.  Thanks Ozzman!  That fix is much better than disabling all the volume icons.  :D

Glad my searching was able to help more than just myself.

---

