---
title: "Some general questions ( need answers )"
date: 2010-10-28
forum: General Help
---

### Post by jokes_finder on 2010-10-28
Hello,

 I'm using Ubuntu for a while now.. but I have some questions:

1- Do I have to mount each partition after each boot? Is there an automated mounting the partitions?

2- Can I have a "My computer" icon on the Desktop?

3-  There's a problem that occurred just now.. Yesterday I connected to  another monitor, Today, after logging in - using the laptop display -,  the icons on the task bar are shifted to the left.. Here's a snap shot.
[[IMG]http://h3sonline.com/forums/up/uploads/ac9dcd8e63.bmp[/IMG]]("http://h3sonline.com/forums/up/")

---

### Post by matt_symes on 2010-10-28
Hi

1. Read up on fstab. /etc/fstab to mount at startup
2. You can drag and drop folders from under places onto your desktop.
3. No idea about your third issue

EDIT: When you say "My documents" do you mean your home folder?

Kind regards

---

### Post by jokes_finder on 2010-10-28
Thanks for ur response...
But still can't adjust the fstab file configuration ( after reading the official ubuntu documentation ) to auto mount the partitions.

Regards

---

### Post by endotherm on 2010-10-28
post back 
```
cat /etc/fstab
sudo fdisk -l
ls -l /dev/disk/by-uuid
```
and we can see what we can do about your fstab

for #2, no but you could replicate it, by creating a folder in your home called "Computer". then within that folder create links to each of your disks. finally, create a link on your desktop that points to "computer" and that should do you. there are also lots of options in the gconf editor for controlling your desktop, including an option to put a link to each mounted volume on the desktop as it is mounted.

for 3, I'm not sure what the issue is, since those icons always align left anyway. can you expound?

---

### Post by linuxpyro on 2010-10-28
1. Do you have a couple hard drives in your computer, or just one with a few partitions?  Post your /etc/fstab, and tell us what exactly you're trying to do.  (Also, when you edit it, you need to use sudo.  Also, be sure to make a backup of it first :)).

2. Drag and drop, like matt_symes said.  You could go into the Places menu and drag the Computer menu choice onto your desktop.  It's the closest analog to the My Computer icon on Windows.  It'll let you look at the filesystem and media in your computer, but you can't right-click on it to manage your machine like you do on Windows.

3. I've seen this too when doing dual monitors, I'm honestly not sure what causes it, but there must be a solution somewhere...  Wish I could tell you more :(.

---

### Post by ivarn on 2010-10-28
if you install ubuntu tweak you can enable the home, computer, trash and network icons on your desktop. they are hidden by default.
EDIT: I also wanna know how to auto mount disks. this is really something that should be added during the installation as an option, or from right-clicking on the partitions in the Computer folder.

---

### Post by jokes_finder on 2010-10-28
@ [COLOR=Red]**endotherm**[/COLOR]:
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

``````
~$ sudo fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb3767bbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          52      409600   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2              52       19478   156043264    7  HPFS/NTFS
/dev/sda3           19478       38914   156116312    7  HPFS/NTFS

``````
~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 11 2010-10-28 20:48 07f83e19-8cff-468f-999e-ce6b4e715383 -> ../../loop0
lrwxrwxrwx 1 root root 10 2010-10-28 20:48 305C04295C03E884 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-10-28 20:48 6C50084650081A0A -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-10-28 20:48 B6E00B0DE00AD391 -> ../../sda3
```>  then within that folder create links to each of your disksHow can I do that?
I made the "computer" folder using
```
cd /home
sudo mkdir computer
```> for 3, I'm not sure what the issue is, since those icons always align left anyway. can you expound?     Well, Yesterday I had a presentation. I used the laptop ( Toshiba Satellite L650-10M ) in my presentation. 
I connected the PC to a projector. When I returned home and had my computer on, I found the applets and the icons shifted..

@ **[COLOR=Red]linuxpyro[/COLOR]**:
>          1. Do you have a couple hard drives in your computer, or just one with  a few partitions?  Post your /etc/fstab, and tell us what exactly  you're trying to do.As u can see from the posted code-output, I have only one HDD. And I'm trying to have my partitions mounted as I boot.

> 2. Drag and drop, like matt_symes saidIt worked just great. Thanks ;)

@ [COLOR=Red]**ivarn**[/COLOR]:

How can I install Ubuntu tweak? I searched for it on Ubutnu Software Center but didn't find any.. :(

---------------------
And Thanks for ur responses..
- sry 4 my bad English. It's not my first language. -

---

### Post by cgroza on 2010-10-28
Install NTFS-config and use that to configure your partitions to mount at startup.

---

### Post by linuxpyro on 2010-10-28
> **jokes_finder said:**
> @ **[COLOR=Red]linuxpyro[/COLOR]**:
As u can see from the posted code-output, I have only one HDD. And I'm trying to have my partitions mounted as I boot.


So is your system booting properly (aside from the icons)?  If you're using the system normally, chances are things are mounting properly as you boot.  Just for a little more information, try doing ls -l /host/ubuntu/disks/.

---

### Post by Mark Phelps on 2010-10-28
Sigh ... ALL these suggestions ... and no-one even took the time to notice that this is a Wubi-installation?? That's right -- a Wubi installation!!

First thing you need to do when using Ubuntu is FORGET ABOUT WINDOWS.

If you're going to go down the road of asking how to make everything you had in WINDOWS work the same way in Ubuntu, you're wasting your time and you're setting yourself up for some real dissapointments -- when you find out that some things in Ubuntu are designed NOT to work like WINDOWS.

So, as to the My Computer thing ... basically, if you're looking for the same thing you had in WINDOWS, the answer is no -- you don't have that here.  The architecture and layout of Linux distros is very different -- and you need to become familiar with that, not trying to get your old WINDOWS look-and-feel back.

As to mounting, once again, if anyone had actually bothered to READ what you posted, they would have told you, since you're running a Wubi install, the filesystem is located under /host.

As to your third question, did your default screen resolution changed when you were hooked up to the other display? Asking because that's more often than not the case.  When that happens, the desktop manager autopositions the items on the top and bottom of the screen for the new display resolution.  When you went back to the old one, it looks like it failed to make the adjustment back.

---

### Post by jokes_finder on 2010-10-29
> First thing you need to do when using Ubuntu is FORGET ABOUT WINDOWS.
1- Thanks for ur response.. :)
2- I'm not one of Windows fans. What I wanna say is that the thing I love in linux generally is "FOSS". I like linux because of that. I also heard about LFS (Linux From Scratch ). What I learned from the programming world - although I'm still new to that world - is I can do what  I want to.

 So, I like to have a "Computer" icon on the desktop. And I'd like to have my Ubuntu auto-mount paritions..

> since you're running a Wubi install
How did u know that? I mean what in my posts tells that I installed using wubi.. ( I did install using wubi.exe )

> did your default screen resolution changed when you were hooked up to the other display?
Yes, The resolution did change.
I think there should be a manual way to have my things back.
-------------
Regards...

---

### Post by jokes_finder on 2010-10-29
By the way, I wanna know how to manage the battery power consumption. The battery lasts for an hour with Ubuntu, and lasts for 2 hours with Windows 7. I don't like Ubuntu to be far away from Windows.

---

### Post by Omnomnom on 2010-10-29
Well for the battery, chances are that you have Windows set to battery saving mode, so go to System > Preferences > Power Management and put the display brightness down if you want to save battery.

---

### Post by Verbeck on 2010-10-29
> **jokes_finder said:**
> 
 How did u know that? I mean what in my posts tells that I installed using wubi.. ( I did install using wubi.exe )

> **jokes_finder said:**
> @ [COLOR=Red]**endotherm**[/COLOR]:
```

**/host/ubuntu/disks/root.disk / **              ext4    loop,errors=remount-ro 0       1
**/host/ubuntu/disks/swap.disk none   **         swap    loop,sw         0       0

```
 thats how

> **jokes_finder said:**
> 
How can I install Ubuntu tweak? I searched for it on Ubutnu Software Center but didn't find any.. :sad:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
just download the .deb and double click it. 

> **jokes_finder said:**
> 
Yes, The resolution did change.
I think there should be a manual way to have my things back.

right click on the object you want to move and uncheck lock to panel. then right click again and then select move. or just click and drag


for adjusting power, goto system>preferences>power management

___________
hope this helps

---

### Post by jokes_finder on 2010-10-29
Thanks, Verbeck. U solved the case :)

---

