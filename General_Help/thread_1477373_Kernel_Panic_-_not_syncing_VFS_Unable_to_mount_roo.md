---
title: "Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"
date: 2010-05-08
forum: General Help
---

### Post by Garnett on 2010-05-08
After [Update manager left my machine utterly ruined]("http://ubuntuforums.org/showthread.php?t=1473304") upgrading from 9.10 to 10.04 I spent a good few hours (spread over the days and nights it took to repartition etc) saving my files and installing 10.04 from scratch.

It worked fine, and I spent a fair bit of time tweaking.The last thing I did was to install the Nvidia drivers.

After a restart all I get now is:-

***[   3.344669 ] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)***

So no idea how to resolve this one at all. Another 2 day reinstall? Joy :(

---

### Post by MorganJarl on 2010-05-09
I get this message after my update. I did never acctualy use the Lucide OS I can\t boot it up.

I seam to have the right Kernel - is there anything else that I might have ****ed up?

---

### Post by Garnett on 2010-05-09
I just hope there's a relatively easy solution - can't face another fresh installation, but it's looking more and more likely...

---

### Post by Ad@m on 2010-05-09
I think it could be that the kernel update did not create the initramfs image.

Can you post the contents of your /boot, in a console type 

cd /boot
dir

Then paste the output here.

---

### Post by MorganJarl on 2010-05-09
Since I am runign of a Live CD it was a bit hard to find, but here is the info I found in the boot dir on my HHD:
abi-2.6.31-14-generic          System.map-2.6.31-14-generic
abi-2.6.31-17-generic          System.map-2.6.31-17-generic
abi-2.6.31-19-generic          System.map-2.6.31-19-generic
abi-2.6.31-20-generic          System.map-2.6.31-20-generic
abi-2.6.31-21-generic          System.map-2.6.31-21-generic
abi-2.6.32-22-generic          System.map-2.6.32-22-generic
config-2.6.31-14-generic      vmcoreinfo-2.6.31-14-generic
config-2.6.31-17-generic      vmcoreinfo-2.6.31-17-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-19-generic
config-2.6.31-20-generic      vmcoreinfo-2.6.31-20-generic
config-2.6.31-21-generic      vmcoreinfo-2.6.31-21-generic
config-2.6.32-22-generic      vmcoreinfo-2.6.32-22-generic
grub                  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-17-generic
initrd.img-2.6.31-17-generic  vmlinuz-2.6.31-19-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-20-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-21-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.32-22-generic
memtest86+.bin

---

### Post by Ad@m on 2010-05-09
MorganJarl,

There should be a corresponding entry reading, [COLOR=Red]initrd.img-2.6.32-22-generic[/COLOR]

Which I cant see in your directory listing.

It is quite easy to fix, first you must boot into your installation using a previous kernel version.

Then open a terminal.

[INDENT] cd /boot
sudo update-initramfs -c -k [COLOR=Red]initrd.img-2.6.32-22-generic[/COLOR]
[COLOR=Red] [COLOR=Black]dir[/COLOR][/COLOR]
[/INDENT][COLOR=Red][COLOR=Black] 
After typing dir, you should see the initrd image for 2.6.32-22-generic

But I suspect the initramfs was also not added to the /boot/grub/grub.cfg, which means you have to edit this as well.[/COLOR][/COLOR][COLOR=Red][COLOR=Black][/COLOR][/COLOR][COLOR=Red][COLOR=Black]

[/COLOR][/COLOR][INDENT][COLOR=Red][COLOR=Black]sudo gedit /boot/grub/grub.cfg[/COLOR][/COLOR]
[/INDENT][COLOR=Red][COLOR=Black] 
Look for an entry that is similar to the below example

[/COLOR][/COLOR][INDENT]menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b624b513-7118-4374-b71f-f03920878b6b
linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
[COLOR=Red]initrd /boot/initrd.img-2.6.32-22-generic[/COLOR]
}

[/INDENT]Add the line in red (assuming it doesnt exist). You will also need to do this to the failsafe entry if you wish to use it in the future.

In a normal update, ubuntu will automatically create the initrd image and add the grub entry. I wonder why it failed on your system. Perhaps a bug?

For further reference, take a look at this blog entry, scroll down to  about half way.

[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

---

### Post by Rayneboard on 2010-05-10
I have a similar issue, but I am unable to boot into my messed up Lynx.
There was a power loss overnight during my update, when I tried to reboot I got the same Kernel Panic.

I installed a fresh copy of Karmic on a separate partition, but I'd like to salvage my old setup.

Following through your suggestions, I mounted the partition with the messed up Lynx and checked the boot folder and did not find the image file for "initrd.img-2.6.32-22-generic"  (would it be generic-pae for my set up?)

I still have a GRUB folder with all the appropriate files inside..

I checked the grub.cfg file, and I am missing the line you mentioned.

Unfortunately, in the new copy of Karmic I do not have the permissions to edit the file.

Thank you!

_Sven[COLOR=Red]
[/COLOR]

---

### Post by James78 on 2010-05-10
I had this problem once, the solution was simple. Boot into livecd, and use e2fsck /dev/sdb1 to fix the filesystem.

---

### Post by Rayneboard on 2010-05-10
> **James78 said:**
> I had this problem once, the solution was simple. Boot into livecd, and use e2fsck /dev/sdb1 to fix the filesystem.
That would from the terminal in the live version?

~ also, wouldn't sdb1 be different for my partition ?   like /dev/sda8 ?

---

### Post by Garnett on 2010-05-10
> **James78 said:**
> I had this problem once, the solution was simple. Boot into livecd, and use e2fsck /dev/sdb1 to fix the filesystem.
Gah! Couldn't wait - needed a functioning computer, so I went for a reinstall. Now the LiveCD won't work. "There is an error with the CD or with the HDD" Odd as they've both worked fine before.

5 days without a functioning machine!

---

### Post by Rayneboard on 2010-05-10
I booted into the liveCD and tried to run that line..
I keep getting messages saying that I do not have access to the partition.

Thanks for your help..

---

### Post by James78 on 2010-05-10
@ Rayneboard:

I was just being general and vague. If you want to try this, here is how to do it.

1) Go into the livecd.
2) Go to the terminal and type "sudo e2fsck /dev/sdx#"
3) Say yes to all the problems it asks to fix.

You must replace /dev/sdx# with your disk drive and partition number. Your first drive is sda, first partition sda1. You can find the devices by going to disk utility and clicking on the appropriate disk and then clicking on the partition (it says what device and partition it all is).

Note: Make sure the disk you are trying to fix is NOT mounted, otherwise it will refuse to check it or fix it, although it can be forced while it is mounted, it usually will corrupt the filesystem further.

---

### Post by katlegoHK on 2010-05-10
hello i'm new here. i need help...how do you create an initrd image in ubuntu 8.10? i have tried mkinitrd -o command but is says command not found... please help:(

---

### Post by James78 on 2010-05-10
> **katlegoHK said:**
> hello i'm new here. i need help...how do you create an initrd image in ubuntu 8.10? i have tried mkinitrd -o command but is says command not found... please help:(The command you want is mkinitramfs.
```
sudo mkinitramfs -o outfile
```
```
Usage: /usr/sbin/mkinitramfs [OPTION]... <-o outfile> [version]

Options:
  -d confdir  Specify an alternative configuration directory.
  -k          Keep temporary directory used to make the image.
  -o outfile  Write to outfile.
  -r root     Override ROOT setting in mkinitrd.conf.

See mkinitramfs(8) for further details.
```

---

### Post by katlegoHK on 2010-05-10
i have tried that as well but it says that the command is not found

---

### Post by katlegoHK on 2010-05-10
> **James78 said:**
> The command you want is mkinitramfs.
```
sudo mkinitramfs -o outfile
```
```
Usage: /usr/sbin/mkinitramfs [OPTION]... <-o outfile> [version]

Options:
  -d confdir  Specify an alternative configuration directory.
  -k          Keep temporary directory used to make the image.
  -o outfile  Write to outfile.
  -r root     Override ROOT setting in mkinitrd.conf.

See mkinitramfs(8) for further details.
```
i have trien that but it seems like that command is not installed in my ubuntu. doe4s ubuntu 8.10 have those packages pre installed?

---

### Post by MorganJarl on 2010-05-10
**James78**:
This is what I get in the terminal when I try to do that:

ubuntu@ubuntu:~$ sudo e2fschk /dev/sda
sudo: e2fschk: command not found
ubuntu@ubuntu:~$ 

**Ad@m**: 
This is what I get when I try what you said:

ubuntu@ubuntu:~$ cd /media/c90adeec-d79e-4cf7-a84c-420a70191906/boot
ubuntu@ubuntu:/media/c90adeec-d79e-4cf7-a84c-420a70191906/boot$ sudo update-initramfs -c -k initrd.img-2.6.32-22-generic
update-initramfs is disabled since running on read-only media
ubuntu@ubuntu:/media/c90adeec-d79e-4cf7-a84c-420a70191906/boot$

Same happens if I sudo it in the liveCD's /boot folder. Help?

---

### Post by MorganJarl on 2010-05-10
Ad@m: I think the install did not work on my system since I had some problem with my power. That is my theory.

---

### Post by Ad@m on 2010-05-10
Boot into your ubuntu install, not the live cd.

[https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202]("https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202")

Hold the shift key during boot, this will bring up the grub menu, then select a previous kernel version to boot from.

Then run the update-initramfs command whilst in your /boot folder and other steps described above.

---

### Post by MorganJarl on 2010-05-10
I have more problems then I thought.

When I pick another kernel version I get this message:

* Starting init crypto disks...
[22.819343] ppdev: user-space parallel port driver

and then the computer stops. I can press Esc and the systems shuts down *after a load of text I have no time to read - but it won't go on booting.

---

### Post by Ad@m on 2010-05-10
I think there comes a point where sometimes it is best to start from scratch.

How about a clean 10.04 install ?

---

### Post by lpeter on 2010-05-10
10 May 10

Am avidly following this thread; have the same error after trying to install latest kernel 2.6.33.3-candela (using Kernel Check to compile) in order to get beyond the WPA2 problem with an rt2860 wireless on my EeePC 1000HE.  Have a very recent clean install of 10.04 LTS.

Am able to boot to earlier kernels without issue.  Trying to boot to 2.6.33.3-candela brings the same problem.  Tried the live CD boot and then to Terminal as James78 recommended, but got same result as MorganJarl:
[INDENT] ubuntu@ubuntu:~$ sudo e2fschk /dev/sda
sudo: e2fschk: command not found
ubuntu@ubuntu:~$ 
[/INDENT]Thanks in advance for any further thoughts.

Take good care.

---

### Post by James78 on 2010-05-10
@ lpeter and MorganJarl: Sometimes I get the command mixed up. It's e2fsck. And as for /dev/sda, you NEED to make sure that that hard drive is the one your ext3/4 Linux installation is on, and there needs to be a partition number after it! If you're using the whole disk as the install, then it should be /dev/sda1, if the disk is slave and you have 2 disks, it's /dev/sdb1.

@ MorganJarl: It can't update-initramfs because the media was mounted as read-only. Just mount it as rw (read-write) and there should be no problem. The problem _might_ be in /etc/fstab, it might specify to mount it as read-only there, however if you're doing this on a livecd, then the problem isn't likely in /etc/fstab. You could probably just use the umount command (unmount media), then remount it using mount, and it should mount as rw.

@ katlegoHK: If the command isn't found, then you don't have the proper package installed. Go to Synaptic package manager, or whatever one you use, find and install initramfs-tools.

---

### Post by MorganJarl on 2010-05-10
James78: Doing it right now. Hope for the best.

Ad@m: Well I would be happy to. I have some important documents that I did not back up before the update (dumb Idea, I know) so I am trying to recover them. Unfortunately they are encrypted. Follow my journey here: [http://ubuntuforums.org/showthread.php?p=9273817#post9273817](http://ubuntuforums.org/showthread.php?p=9273817#post9273817)

---

### Post by lpeter on 2010-05-10
@James78 (#23):

Thank you for the corrected command.  Have used  it and there were no issues detected.

sudo e2fsck /dev/sda1
e2fsck  1.41.11 (14-Mar-2010) 
/dev/sda1: clean, 294516/9396224 files,  25041338/37568512 blocks

Thanks in advance for your continuing  interest.

Take good care.

---

### Post by James78 on 2010-05-10
Hi, please try this command now:
```
sudo e2fsck -f /dev/sda1
```
This will force it to check it regardless, sometimes the disk reports as clean when it isn't. I'm going to assume you got the disk and partition number correct. :)

Can you also return the output of 'sudo fdisk -l' for me?

---

### Post by MorganJarl on 2010-05-10
James: Did what you told me to. No change. Tried adding -f and got this result

> ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

Superblock last write time is in the future.
    (by less than a day, probably due to bad system clock last boot).  Fix<y>? yes

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 377829/4685824 files (1.1% non-contiguous), 14864740/18729774 blocks

I did unmount the filsystem when I got the warning and then pressed y.

Did the fdisk and got this:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7021df5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS


sdb is my external hard drive that I am intending to copy my stuff too.

I will now restart the computer and see if it made any difference.

---

### Post by lpeter on 2010-05-10
5-10-5

@James78,

Thank you.   I believe I have the drives correct, am not using a slave, when installing, copied everything to the primary SDA1 (I think) with two smaller partitions, one being a swap area and the other for something else (both automatically created).  Here is the result of your request:
[INDENT]ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 294335/9396224 files (0.2% non-contiguous), 25035170/37568512 blocks
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052cff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18709   150274048   83  Linux
/dev/sda2           18709       19458     6013953    5  Extended
/dev/sda5           18709       19458     6013952   82  Linux swap / Solaris

Disk /dev/sdb: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e389

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1010     1972499    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


[/INDENT]Thank you.

---

### Post by MorganJarl on 2010-05-10
No luck.

Will try to unmount and remount my disc to see if I can get it to rw.

---

### Post by MorganJarl on 2010-05-10
James78: Well, tried teh mounting stuff. No difference. It seems to me that it is to do with the fact that I am running on a LiveCD. Should I write an other command perhaps? Or add something to the one I use?

This is what I get.
> 
ubuntu@ubuntu:~$ cd /media/c90adeec-d79e-4cf7-a84c-420a70191906/boot
ubuntu@ubuntu:/media/c90adeec-d79e-4cf7-a84c-420a70191906/boot$ sudo update-initramfs -c -k initrd.img-2.6.32-22-generic
update-initramfs is disabled since running on read-only media

---

### Post by James78 on 2010-05-10
@ MorganJarl: Ok, so it doesn't see any problems with the filesystem. The only other option I can think of is that it's the kernel and/or initramfs. Lets try to remake initramfs. As stated in the other post, this one person didn't have the tool, it's located in the repository under the name of initramfs-tools. If the new image doesn't work, it could be the kernel, but sadly reinstalling the kernel to an offline installation might be a hard task. :(

Are you trying to unmount the livecd itself? If you are, that's probably the problem. I think it can't update-initramfs because it's on the livecd, but if you make the image, it should generate and go wherever the outfile is. mkinitramfs generates the image, make sure the initramfs file matches the kernel on your actual installed system. I have no idea what would happen if they didn't.
```
sudo mkinitramfs -o ~/outfile
```

@lpeter: I believe the same goes for you too. The disk has no "problem". I believe you should also try mkinitramfs, again, make sure the kernel you have matches... Making initramfs and installing a kernel onto a offline installation is actually a pretty difficult task. :(

If you're all really tired, a reinstallation would be the easiest, just make sure to backup the files you want of course.

---

### Post by Garnett on 2010-05-10
Remember me? I've been doing a fresh reinstall which proved fraught.

Anyway, in the interests of science I've buggered the machine again. It's definitely the Nvidia driver. Ubuntu tells me to try a proprietary driver, gives me two options, and the only one that works is the older one. The "recommended" driver kills the OS, this time with a new Kernel Panic - "Tried to kill init!"

Just tried sudo e2fsck -f /dev/sda5 :-


e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 150350/9011200 files (0.1% non-contiguous), 1250820/36033536 blocks

Any hope or time for reinstall 3?

---

### Post by James78 on 2010-05-10
I haven't used the new nvidia driver with 10.04 since I don't have an nvidia card right now, where I did previously, however what you're saying could be possible. Does anyone else use the nvidia driver??

@ Garnett: I'm not sure, but if what you're saying is true, then another reinstall might do absolutely nothing for you except waste time based on the sounds of it. This might help you however..
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

There is a open source nvidia driver called nouveau though..

---

### Post by Garnett on 2010-05-10
> **James78 said:**
> I haven't used the new nvidia driver with 10.04 since I don't have an nvidia card right now, where I did previously, however what you're saying could be possible. Does anyone else use the nvidia driver??

@ Garnett: I'm not sure, but if what you're saying is true, then another reinstall might do absolutely nothing for you except waste time based on the sounds of it. This might help you however..
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

There is a open source nvidia driver called nouveau though..

James. You've saved the day. Although I thought e2fsck hadn't resolved anything everything works fine now!

Thanks a lot.

---

### Post by James78 on 2010-05-11
That's good!

Did any of you other guys, by any chance use the Wubi (install under MS Windows) installer? If so, try defragmenting c:\ubuntu\disks\root.disk on Windows.

If not, I came across another person with a similar problem to this. They had /boot on another partition, and it had too little memory. They increased the partition size and it worked alright afterward, although I don't think this is the case for any of you.

---

### Post by Ad@m on 2010-05-16
> **MorganJarl said:**
> James78: Well, tried teh mounting stuff. No difference. It seems to me that it is to do with the fact that I am running on a LiveCD. Should I write an other command perhaps? Or add something to the one I use?

This is what I get.

Sorry for the long delay, I have tested and you are right. To overcome this you have to chroot into your ubuntu disk install.

This is an example, you will have to adapt it for your setup. sda2 is my ubuntu install.

Run the livecd, open a terminal and type the following.

mkdir disk
sudo mount /dev/sda2 /home/ubuntu/disk
sudo mount -t  proc none /home/ubuntu/disk/proc
sudo chroot /home/ubuntu/disk

cd boot
update-initramfs -c -k NAME_OF_KERNEL

---

### Post by MorganJarl on 2010-05-16
Thanks Ad@m. I gave up on saving my install and extracted my encrypted files and reinstalled instead. Thanks for all help.

---

### Post by psykickuk on 2010-05-20
I think this may have been the same problem I encountered. I posted my solution here:

[http://www.backports.ubuntuforums.org/showthread.php?p=9325774#post9325774](http://www.backports.ubuntuforums.org/showthread.php?p=9325774#post9325774)

---

### Post by LuckyNeo on 2010-05-22
Hi, I try few solutions, but nothing worked, so I tried to reainstall kernel (lucid) with these commands:

```
sudo apt-get remove linux-image-2.6.32-22-generic
sudo apt-get install linux-image-2.6.32-22-generic
```

version may vary, for list of available kernel images use this: 
```
apt-cache search linux-image
```

---

### Post by James78 on 2010-05-22
I came across this problem in some of my virtual machines. Reinstalling sometimes would help, but there would be filesystem problems too. I switched the device to IDE, and it worked perfectly after the first try. Might have nothing to do for you guys. However, even so, this seems like a pretty nasty bug here.

---

### Post by DeusNCarN8 on 2010-06-30
Hello fellow ubuntu-ers,  

I'm very new to linux in general and ubuntu even more so, however; I recently started using ubuntu running on VMWare Player. After signing in recently, I was greeted by an update manager that informed me that I had something like 713 updates, to which I happily clicked update and went about my business. 

Everything seemed fine, until I tried to boot the next day, at which I was greeted by the exact message that appears in this thread's Title. After reading through this thread and some others I was able to resolve this issue and I wanted to post my resolution for others that might also travel down the same road. The procedure was INCREDIBLY easy:  

I started the vm, holding shift as it booted.  I was greeted with a menu titled, "GNU GRUB" on which there were 8 boot options (3 kernel versions each with a regular and a recovery mode and two Memory test options). I choose the sixth option, titled "Ubuntu, with Linux 2.6..32-14-generic (recovery mode)"

I was then greeted with a Recovery Menu with 7 options. I choose the 3rd option, "dpkg Repair broken packages"  I then watched as a lot of text scrolled across the screen. I saw many of  the commands which were suggested in this thread. At one point I was prompted for input and I choose the default. 

When the process was done, I rebooted to (I believe) a shiny brand new kernel.  Hope this helps some other newbs. 

-DeusNCarN8

*edited because posting removed all line returns. </strange>

---

### Post by sina63 on 2010-09-14
That saved me a couple of hours. Thank you.

---

### Post by Rodart on 2010-11-10
I just installed Ubuntu in my old pc, and I get that error too, with Ubuntu 10.10,
 0.560882 Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
Pid: 1, comm: swapper not tainted 2.6.35-22-generic #33-ubuntu
call trace:
c05c6468 ? printk+0x2d/0x35
and other things like that one, it's a lot to copy here...
Do you have any ideas on how to work this one out?
Thanks!

amd k6 I belive at 700mhz
384mb ram
nvidia riva tnt2 
82gb HDD IDE
Motherboard pcchips m805lr

---

