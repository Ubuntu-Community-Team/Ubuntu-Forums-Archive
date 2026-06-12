---
title: "GParted Problem"
date: 2010-07-24
forum: General Help
---

### Post by emily22 on 2010-07-24
I have both Vista and Ubuntu on my laptop, and I am trying to shrink the Vista partitions and enlarge the Linux ones. I already shrined the Vista ones and I freed 150 Gb of space, but now when I try to resize the Linux partitions with GParted, it doesn't work. Please see the attachment. I am trying to resize "LinuxData", but when I do that it appears as if it already has the maximum possible space. I can shrink it, but I can't enlarge it using the unallocated 150 Gb. :( Also, I would like to enlarge sda6 but I don't know how. I can't resize mounted partitions, but I can't just unmount that one...

Please help?

---

### Post by arpanaut on 2010-07-24
You will need to enlarge the extended partition first, then you will be able to enlarge the partitions within the extended. To be able to work on your Ubuntu parts. you will need to use a live-cd or usb, as you cannot do the adjustments while the partitions are in use.

Looks like you may have issues with your Win parts. too check out the warning triangles and do what is advised there. After adjusting Win-parts. it is wise to boot into those partitions a few times to allow the OS to adjust to the changes.

---

### Post by emily22 on 2010-07-24
Ah, ok, thanks a lot. So I really have to go buy a cd then... I was hoping I can get around without doing that since the shops are closed now :(.

About the Win parts: strangely now that I opened GParted again there are no triangles. It seems that the problem fixed itself. :D

---

### Post by arpanaut on 2010-07-24
You can use the live-cd or usb that you used to do your original install. There is a partitioner on there if you boot to "try without changes to your HD"

---

### Post by drs305 on 2010-07-24
> **emily22 said:**
> Ah, ok, thanks a lot. So I really have to go buy a cd then... I was hoping I can get around without doing that since the shops are closed now :(.

**Added:** Actually, reviewing your current partition setup, you would have to do some work on your partitions before we will be able to set this up to be able to do what you want. Provide the information if you wish and maybe we can find a way to do what I propose anyway. Do you have a USB drive we could put the ISO on, or another drive on your system? **End Add**

If you have the ISO but not a LiveCD, we can turn that :-( around!  Of course, if you already have a LiveCD you just have to boot that and won't have to do the following.

If you are using Grub2 and karmic or lucid we can build a Grub menu that will allow you to boot an iso of either the LiveCD, systemrescue CD, or gparted CD.

What you will need is a downloaded image of one of these iso files. You may already have the LiveCD iso on your computer. You can download the Gparted or SystemRescue CD online.

What we will need is the exact name of the ISO and where it is located - the path and partition.  Example:  /media/my_iso/ubuntu-10.04-desktop-i386.iso  on sda5.  The location of the ISO cannot be on your / partition, so put it elsewhere.

With that information, we can give you an option to boot to one of those files and gain full access to your system without mounting the partitions needed to be moved around.

Also here is a post I made a while back on expanding a / partition. The tips start about half way down the original post:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by emily22 on 2010-07-24
Well, I'm fairly new to linux so I'm not sure I know what grub2 or lucid is... :D 
Also, I don't know if I have the LiveCD iso or not, so I will try to get the stuff you are saying.
I am using gnome.

---

### Post by drs305 on 2010-07-24
It may be a bit advanced for you and it might be simpler to wait until you can make a LiveCD, if you don't have one already. How did you install Ubuntu? If you inserted a disk and followed the install instructions, that is what we call the LiveCD.

Grub 2 is the current bootloader for Ubuntu's later releases. It creates the menu you see when you start your computer and let's you pick which operating system you want to use.

Lucid is the codename of the latest (non-testing) release of Ubuntu. You can see which one you are running with this command in a terminal. You can open a terminal via Applications, Accessories, Terminal.
```
lsb_release -a
```

---

### Post by emily22 on 2010-07-24
Thanks. The output is:

 lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

I found this: [http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

So I am just taking gparted-live-0.6.1-2.iso. Is that correct so far?

---

### Post by drs305 on 2010-07-24
Yes, that one would work. But as I added to the original post - because of your partition setup you will need a second drive or a usb drive to put it on.

Without going into a lot of detail, the iso can't be in the extended partition, and that is the only place I see for you to put it unless you have a second hard drive or a flash drive. If you have a flash/thumb drive, you should be able to put the ISO on the thumb drive (using Ubuntu apps to write it there in the correct format), tell your BIOS to boot from that drive first, and it should launch gparted from there.

---

### Post by emily22 on 2010-07-24
Ok, I put it in /media/my_iso/gparted-live-0.6.1-2.iso, but I also have a flash drive which I just formatted as FAT. So how do I put it on the flash drive? I assume it's not just copy-paste, right?

---

### Post by drs305 on 2010-07-24
Here is a link to the gparted install instructions. This actually extracts the files and makes the thumb drive a bootable gparted device:
[http://gparted.sourceforge.net/liveusb.php]("http://gparted.sourceforge.net/liveusb.php")

Choice 1 in the second half (GNU/Linux).
[http://gparted.sourceforge.net/liveusb.php]("http://gparted.sourceforge.net/liveusb.php")

This should create a bootable gparted thumb drive. Once you have accomplished the setup, go into your BIOS and make sure your system will boot the thumb drive first. Then restart your machine and it should boot to GParted. Since you booted from an external drives, you should be able to unmount all your normal system partitions and complete your partition resizing.

---

### Post by emily22 on 2010-07-24
P.s. I know how to change the booting sequence and boot from the USB, but I don't know how to properly put the iso on the USB.

---

### Post by emily22 on 2010-07-24
A, ok, I saw your last post after I replied.

---

### Post by drs305 on 2010-07-24
> **emily22 said:**
> P.s. I know how to change the booting sequence and boot from the USB, but I don't know how to properly put the iso on the USB.

That is what the previous link was for. The second half provides instructions on how to install the files on a USB drive.

We could also do all this via Grub2, if that is what you are using. You tell the Grub version with this command. With Karmic, you could be using either Grub legacy or Grub 2. Grub 2 is version 1.96 or later.
```
grub-install -v
```
If you have version 0.97, that is grub legacy.

---

### Post by emily22 on 2010-07-24
It worked! Thank you!! :D

One last question: somehow, ever since I shrined the partitions in Windows it somehow isn't mounting LinuxData automatically when I start the computer. So I am mounting it with sudo mount /dev/sda5 /media/linux_data from the command line. How can I make it mount automatically again?

---

### Post by drs305 on 2010-07-24
> **emily22 said:**
> It worked! Thank you!! :D

One last question: somehow, ever since I shrined the partitions in Windows it somehow isn't mounting LinuxData automatically when I start the computer. So I am mounting it with sudo mount /dev/sda5 /media/linux_data from the command line. How can I make it mount automatically again?


Glad you got your partitions rearranged.  :=)

Your partition designation for that partition may have changed. The partitions in Linux are mounted by instructions in /etc/fstab.

Open a terminal, then run this command to see information on your data partition:
```

sudo blkid | grep sda5

```
This should give you the UUID and LABEL (if it has one).
Next open fstab and take a look at your data partition.
```
gksu gedit /etc/fstab
```
You will probably see a line such as this for your data partition:
> 
UUID=ba83d184-705e-4115-9d42-0823c698a757 /media/linux_data ext3 defaults  0 2


In fstab, you will be changing the UUID or LABEL. The mount point and options should probably be left as they are (if it's ext4 and not ext3, leave it as it is).

Option 1:
If it has a UUID in the line:
See if the UUID in fstab matches the UUID from the terminal command. If they do not match, copy the terminal UUID and replace the fstab one. (In linux, you copy from a terminal with CTRL-SHIFT-C, paste outside a terminal just like Windows with CTRL-V)

Option 2:
If it has a UUID that is incorrect, but the terminal command also gave you a LABEL for your data partition, you can make this kind of entry:
> 
LABEL=linux_data  /media/linux_data ext3 defaults 0 2


Once you have made the change, save the file. You can test your fstab settings by running these commands. The first will umount your data partition (so make sure you have saved any open files), and the second will attempt to mount the partition according to your new fstab entry. 

If it works, you will see nothing happen when you press ENTER. If it's wrong, you will get an error message.

```
sudo umount /dev/sda5
sudo mount -a
```

If any of this isn't clear, just post the results of the first command you ran in the terminal and the fstab line and we can construct one for you.

---

### Post by emily22 on 2010-07-24
This is what is in fstab:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=ce81455d-5746-4003-8af0-ebbf20cc2c78 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=0ed3f953-f4b5-4025-a133-ffcc267c2886 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0       /media/cdrom0   defaults 0       0
#/dev/sda9    /home/andreea/LinuxData    ext4    udf,iso9660 user,noauto,exec,utf8    0    0
/dev/sda9    /home/andreea/LinuxData    ext4    defaults    0    0


And this is what I get from the command line:
sudo blkid | grep sda5
/dev/sda5: LABEL="LinuxData" UUID="36101d19-626f-4b21-9450-d0132d42b7ac" TYPE="ext4"

So the UUID from the command line is not found in fstab, and It's not clear for me where I should modify stuff...

---

### Post by drs305 on 2010-07-24
> **emily22 said:**
> This is what is in fstab:


#/dev/sda9    /home/andreea/LinuxData    ext4    udf,iso9660 user,noauto,exec,utf8    0    0
/dev/sda9    /home/andreea/LinuxData    ext4    defaults    0    0


And this is what I get from the command line:
sudo blkid | grep sda5
/dev/sda5: LABEL="LinuxData" UUID="36101d19-626f-4b21-9450-d0132d42b7ac" TYPE="ext4"

So the UUID from the command line is not found in fstab, and It's not clear for me where I should modify stuff...

Assuming your old sda9 is now sda5, you can replace the **exisiting** entry with **[COLOR="DarkRed"]EITHER of these[/COLOR]**:
Replace this (by deleting the lines or placing a # symbol at the start of each line):
> [B]#/dev/sda9    /home/andreea/LinuxData    ext4    udf,iso9660 user,noauto,exec,utf8    0    0
/dev/sda9    /home/andreea/LinuxData    ext4    defaults    0    0[/B]
With this:
> 
[B][COLOR="DarkRed"]LABEL=LinuxData  /media/LinuxData    ext4    defaults    0   2

or:
UUID=36101d19-626f-4b21-9450-d0132d42b7ac  /media/LinuxData    ext4    defaults    0   2
[/COLOR][/B]

If you want to mount it elsewhere, change "/media/LinuxData" to the wherever you wish. Make sure the mount point exists and is owned by you. Here are the commands to make a new mount point and make yourself the owner, should you need to do so:
```
sudo mkdir <path>/<mountpoint> && sudo chown <yourusername>: <path/mountpoint>
```
Example:
sudo mkdir /media/data && sudo chown emily22: /media/data

---

### Post by emily22 on 2010-07-24
It works! Thank you so much! :D

---

### Post by drs305 on 2010-07-24
Well, you've now learned a bit about gparted and fstab. You are well on your way to becoming a seasoned linux user.  ;-)

Marking your thread SOLVED helps users looking for threads with known solutions and allows those offering assistance to concentrate on unresolved posts. You can mark a thread solved with the "Thread Tools" link at the top right of the original post.

---

