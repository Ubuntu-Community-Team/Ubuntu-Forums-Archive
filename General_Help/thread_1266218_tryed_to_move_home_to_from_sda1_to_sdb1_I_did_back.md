---
title: "tryed to move home to from sda1 to sdb1 I did back up"
date: 2009-09-14
forum: General Help
---

### Post by rodh on 2009-09-14
Well, I was following directions to move /home to a different drive and now things are not working.  I booted off the Live CD. All the files are there but when you click on home ICON the only thing there is and ICON  looks like text page /sdb1.  Basically I think I have to find out how to set /home on the new drive and move the old files over.

---

### Post by rodh on 2009-09-14
Bump,  I need some help on this one,  Thanks

---

### Post by nothingspecial on 2009-09-15
Which instructions were you following?

Have you mounted your new home as home?

A little more info please.

---

### Post by Chronon on 2009-09-15
Yes, you really need to provide more details.  We don't know what you have done.  Did you update the fstab?

---

### Post by rodh on 2009-09-15
I was following directions on this site [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
 
but when I got to the part to edit /etc/fstab I got message file not found.  My back up file and home folder are intact in /old/home and I can access the files using Live CD but the Instruccction to restore the back-up also fail.

---

### Post by nothingspecial on 2009-09-15
Try ```
sudo cp /old/etc/fstab_backup /old/etc/fstab
```
from the live cd having mounted your file system again.

Then ```
gksudo gedit /old/etc/fstab
```

and add the line there.

---

### Post by rodh on 2009-09-15
Tried, and this is what I get: Attatched screenshots But  I can go find in nautalus I find both /etc/fstab and /etc/fstab.bak

---

### Post by nothingspecial on 2009-09-15
Well, you need an /etc/fstab in your file system which you`ve got and as long as you haven`t changed it things should be fine.

Your original fstab is telling ubuntu to mount /dev/sda1 as /.

You need to tell it to mount /dev/sdb1 at /home

Unfortunately the way fstab looks has changed since that tutorial was written.

Here`s mine```


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7826a305-d39c-48e2-871d-bf7452d26b8b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
[COLOR="Red"]UUID=4402fbf3-734c-4238-9b56-635ddc422741 /home           ext3    defaults        0       2[/COLOR]
# swap was on /dev/sda5 during installation
UUID=4c633c99-859a-460d-963c-e3a5f06cf4fc none            swap    sw              0       0

```

My home is on /dev/sda4 in red.

You need to make your fstab look like that.

Find your UUID by typing

```
sudo blkid
```

---

### Post by rodh on 2009-09-16
I am lost, I am able to find files in a GUI enviroment but I can't get permission in GUI to do anything. When I try to do it in Terminal with sudo it says directory not found, or media full or some other stuff, sdb1 is empty newly partitiioned with gparted and formated ext3 labled home gparted did not ask for a mount point though and I did not see anywhere to tell it the mount point. How do I at least save a copy of my home folder onto a diffferent drive. I have a 300GB USB drive that is mostly empty but I can not get it to cp /old/home_backup to it. Operation not supported or permissions issues when I try. Please somebody rescue me Vista is killing me.

---

### Post by nothingspecial on 2009-09-16
Just to get something straight, are you still trying to move your home to a seperate partition or do you just want it back to how it was before?

To get permission to move files in a gui environment type

```
gksudo nautilus
```

Don`t forget to change home_backup to home.

Trouble is after that root will own your home. To fix it.
```

chown -R *[COLOR="Red"]username[/COLOR]*:*[COLOR="Red"]username[/COLOR]* /home/[COLOR="Red"]*username*[/COLOR]
```

```
chmod 644 /home/*[COLOR="Red"]username[/COLOR]*/.dmrc
```
```

chmod 644 /home/*[COLOR="Red"]username[/COLOR]*/.ICEauthority
```

You have to do this from recovery mode or failsafe terminal or whatever it`s called at the moment. To get there restart and when you see the bit about grub loading press escape.

---

### Post by jocko on 2009-09-16
> **rodh said:**
> I am lost, I am able to find files in a GUI enviroment but I can't get permission in GUI to do anything. When I try to do it in Terminal with sudo it says directory not found, or media full or some other stuff, sdb1 is empty newly partitiioned with gparted and formated ext3 labled home gparted did not ask for a mount point though and I did not see anywhere to tell it the mount point. How do I at least save a copy of my home folder onto a diffferent drive. I have a 300GB USB drive that is mostly empty but I can not get it to cp /old/home_backup to it. Operation not supported or permissions issues when I try. Please somebody rescue me Vista is killing me.
First of all, your fstab entry for /home looks like it's not complete. Make sure it looks like this:
```
UUID=a2e85b48-30d3-4800-9fd2-29644d33c5f /home ext3 [COLOR=Red]defaults 0 2[/COLOR]
```Next, when you want to show the the contents of a text file in a forum post, just copy and paste the contents of the file in the post and put it in code brackets. That is put a "[/code]" after it and a "[code]" before it... Screenshots are not always the best way, as we may want to be able to copy/paste or see where line breaks are and such....

---

### Post by nothingspecial on 2009-09-16
Having looked at your attached thumbnails, I see where you are going wrong. You can`t move stuff to /dev/sdb1.

You have to mount those partitions. From the live cd ......

```
sudo mkdir /media/whatever
```
```

sudo mount -t ext3 /dev/sdb1 /media/whatever
```

You also have to mount sda1

```
sudo mkdir /media/anything_you_like
```
```

sudo mount -t ext3 /dev/sda1 /media/anything_you_like
```

You now move stuff between /media/whatever and /media/anything_you_like

I hope that clears it up. Untill you mount it you can`t move anything to it. Once you mount the partition, it`s location is the mount point not in /dev/.

I hope I`m explaining this propperly 

Also your mkdir command is wrong. You don`t specify the directory then it`s location like you did - "sudo mkdir home /dev/sdb1"  And as we`ve already seen you don`t make a directory on /dev/sdb1.

If you`ve mounted /dev/sdb1 to /media/whatever -SEE ABOVE

it would be ```
sudo mkdir /media/whatever/home
```

You just specify the full path.

(unless you move there first, but worry about that later)

This is probably my fault for not being clear enough, anything you don`t understand, post back

---

### Post by rodh on 2009-09-16
really would like to get /home on the other drive.  but if all I can do is get it back that will have to do.

---

### Post by nothingspecial on 2009-09-16
> **rodh said:**
> really would like to get /home on the other drive.  but if all I can do is get it back that will have to do.

Assuming your old home is on sda1

And your new drive is sdb1

Boot your live cd

```
sudo mkdir /ubuntu
```

```
sudo mount -t ext3 /dev/sda1 /ubuntu
```

```
sudo mkdir /new
```
```

sudo mount -t ext3 /dev/sdb1 /new
```

```
cd /ubuntu/home
```
```

find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

Then edit your /etc/fstab as I explained earlier.

Then change the permissions like earlier.

---

### Post by rodh on 2009-09-16
I have been using my Laptop to post,  I only have Vista on it and was not sure how to do the copy paste so that Vista would like it.  i have had many issues with Vista locking up when doing even simple copy paste in word pad.  Or opening e-mail that has an attatchment.  And while on IE I have issues with it opening in a new window when I minimize or try to close a browser window.  Sorry about the mix up I don't believe that I was very clear on my needs.  And THANK YOU for your help.  I am now in the process of making a copy of my old home file on my USB Drive says about an hour. 70 gigs to copy.  So I will probably be trying to finish this tomarrow eve.

---

### Post by rodh on 2009-09-18
OK, I did a new install,  I am back on with most functions.  Now I just need to find out how to get my /old/home_backup/rod to /home/rod  / now owns it and it is on a External USB drive. 
```
rod@rod-desktop:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2040d599-9bf0-4815-8634-fa4580347dd2" TYPE="ext3" 
/dev/sda5: UUID="53c27a89-4092-4d0d-aaf0-950474a8c2fb" TYPE="swap" 
/dev/sdb1: UUID="a2e85b48-30d3-4800-9fd2-29644d331c5f" TYPE="ext3" 
/dev/sdb2: UUID="8C81-294C" TYPE="vfat" 
rod@rod-desktop:~$ 
```I do not see it here and don't know how to ID it.   ```
 /dev/sdc1: UUID="DCCC5BD3CC5BA694" LABEL="USB" TYPE="ntfs" 
```
I did try to copy/paste and I now have /home/oldhome but root is owner.  I did try to change owner but I am not sure where I went wrong.

---

### Post by nothingspecial on 2009-09-19
sdb1 is your new home (I think).
```

UUID=a2e85b48-30d3-4800-9fd2-29644d331c5f  /home  ext3  nodev,nosuid,relatime  0  2
```

should be your fstab entry.

You should have said you were doing a fresh install as there is an option to set your home partition during the install.

Back up your fstab first in case I`ve made a mistake

---

### Post by rodh on 2009-09-19
New /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2040d599-9bf0-4815-8634-fa4580347dd2 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=a2e85b48-30d3-4800-9fd2-29644d331c5f /home           ext3    relatime        0       2
# /windows was on /dev/sdb2 during installation
UUID=8C81-294C  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=53c27a89-4092-4d0d-aaf0-950474a8c2fb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I think I decided to do fresh install between all this,  I have had a tough week at work and have not been keeping up real well with this.  I do appreciate the help.  I am not sure how to do it but I think all I need to do now is get my old home copied into my new home with ownership

---

### Post by nothingspecial on 2009-09-19
> **rodh said:**
> New /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2040d599-9bf0-4815-8634-fa4580347dd2 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=a2e85b48-30d3-4800-9fd2-29644d331c5f /home           ext3    relatime        0       2
# /windows was on /dev/sdb2 during installation
UUID=8C81-294C  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=53c27a89-4092-4d0d-aaf0-950474a8c2fb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I think I decided to do fresh install between all this,  I have had a tough week at work and have not been keeping up real well with this.  I do appreciate the help.  I am not sure how to do it but I think all I need to do now is get my old home copied into my new home with ownership

That looks alright to me. Fstab has /dev/sdb1 as home. That`s your other drive right?
When you log in, are you getting any errors?

---

### Post by rodh on 2009-09-19
No Errors on Login,  But I lost my video settings and can't seem to change them from a default 800x600.  But in browsing the old home files I did not see the xorg.conf file I use to have.  I don't know how to move my old  home/rod file to the new one and have ownership.  I am trying to study up on the xorg manual pages to see if I can get my 1680x1050 back.

---

### Post by nothingspecial on 2009-09-19
So do you have all your media and the rest of your settings?

---

### Post by rodh on 2009-09-19
I think so,  I have not dug in to deep yet.  And I have not found my notes from fixing xorg.conf the last time.  I think that was when I did 8.04 but not sure. might have been before that. Here is mtab:```
./dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-15-generic/volatile tmpfs rw,mode=755 0 0
/dev/sdb1 /home ext3 rw,relatime 0 0
/dev/sdb2 /windows vfat rw,utf8,umask=007,gid=46 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/rod/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=rod 0 0
/dev/sdc1 /media/USB fuseblk rw,nosuid,nodev,allow_other,blksize=512 0 0
```

---

### Post by nothingspecial on 2009-09-19
```
./dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-15-generic/volatile tmpfs rw,mode=755 0 0
[COLOR="Red"]/dev/sdb1 /home ext3 rw,relatime 0 0[/COLOR]
/dev/sdb2 /windows vfat rw,utf8,umask=007,gid=46 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/rod/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=rod 0 0
/dev/sdc1 /media/USB fuseblk rw,nosuid,nodev,allow_other,blksize=512 0 0
```

Again, I think you`ve ben succesfull. I may be wrong but to me it looks like you`ve got /dev/sdb1 mounted as home.

---

### Post by rodh on 2009-09-19
Yes sdb1 is now mounted as /home:  Now how do I get the home_backup restored to the new home file. I am not sure of the full path and I don't know the proper way to do it so that I am the owner of the file[IMG]file:///tmp/moz-screenshot.jpg[/IMG]  [COLOR=Red]Got it! Solved[/COLOR] [COLOR=Black]Now over to multimedia and video to get that fixed.  Thanks for all the Help!!!![/COLOR]

---

