---
title: "Initramfs boot error"
date: 2011-02-19
forum: General Help
---

### Post by koljou on 2011-02-19
Okay, so on occasion when I boot into ubuntu I get this error

[mount: mounting /dev /root/dev failed: no such file or directory]
[mount: mounting /dev /root/sys failed: no such file or directory]
[mount: mounting /dev /root/proc failed: no such file or directory]
[Target filesystem doesn't have /sbin/init.]
[No init found. Try passing init= bootarg]

[BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)]
[Enter 'Help' for a list of built-in commands.]

(initramfs)

I have no idea why this happens, and I get the error when I open any of the kernel versions or any recovery mode. Ubuntu 10.10 Desktop is the only OS installed on the computer, which is a Lenovo S10-3. 

I can eventually get it to go away, sometimes by repeatedly unplugging it and plugging it back in, and sometimes I will boot into GParted, do nothing, then restart and it will work.

I have found some solutions online, but all of them involve the error happening as a result of dual booting with Windows.

I have made no major system changes recently, so I can't see anything like that being the problem.

If anyone know what's wrong or how to fix the issue it would be a great help. If anyone needs any more information, I can do my best to provide it.

---

### Post by kiyop on 2011-02-20
It seems like...
your kernel and initramfs were read and started, but cannot mount the correct root partition.

Boot with LiveCD and mount the partition where ubuntu was installed on, by clicking the proper partition from "Places"->"Removable media".

Open 
boot/grub/grub.cfg
or
boot/grub/menu.lst
and find the line starting with "linux" or "kernel".
Please post what comes after "root=", by openning this page with FireFox.
For example, 
root=UUID=*******************

"Application"->"Accessory"->"Terminal"
and execute the following command in the openned window.
```
sudo blkid
sudo parted -l
```Post the result, by openning this page with FireFox.

---

### Post by dentaku65 on 2011-02-23
I've did an HowTo that can fix you issue.
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)

Good luck!

---

### Post by ryman90 on 2011-07-17
> **dentaku65 said:**
> I've did an HowTo that can fix you issue.
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)

Good luck!

> **Cype said:**
> Thank you so much, was searching for a solution for about a week now and this finally solved it.

Even i had the same problem recently..I did the 
sudo fsck /dev/sda2 command in the terminal

fsck: Device or resource busy while trying to open /dev/sda2 Filesystem mounted or opened exclusively by another program?  
where sda2 is my partition number but to no avail..finally I've solved  the problem and now my Ubuntu 10.10 is running smoothly again.
Here is what I did:

[LIST=1]
[*]Download Gparted from [http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.8.1-3/gparted-live-0.8.1-3.iso/download](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.8.1-3/gparted-live-0.8.1-3.iso/download)
[*]Burn it into a CD and boot from it.
[*]Now  run the sudo fsck /dev/sdaX where X is the number of your partition in  which you have installed Ubuntu (as it was 2 in my case)
[*]Since  you have run this command from the Gparted Live CD,the Filesystem gets  mounted automatically and what follows after the fsck command is a  series of prompts that can be answered yes by pressing the Enter key
[*]Complete the steps above and then restart your system (dont forget to change the boot sequence back to your HDD from CD)
[/LIST]
Hope  this helps you out..Do post your outcome..Beg your pardon if I have bad  forum etiquette and explanation methods but I'm a complete newbie  here..Good luck..:smile:

---

### Post by roopeshmicasa on 2012-02-14
I am also facing same problem BUT haven't got any solution to it and  system is still not working. Seems like something really went wrong with  the system. Nothing is working HERE. HELP!!!

Here is the link to the thread where I have posted my problem 

[http://ubuntuforums.org/showthread.php?t=1914197](http://ubuntuforums.org/showthread.php?t=1914197)

Any help will be much appreciated

---

### Post by petalotis on 2012-03-19
i have exactly the same problem but also i cant boot from any live cd or live usb. Also when removal the hard disc from my laptop (aspire 5600) then boot normally from live cd.

i placed the hard disc as external to another pc and showed it  up but i cant get into it. i received this message "unable to mount 117 gb filesystem" 

as a result i cant access into hard disc

i don't need archives from hard disc i want just clean the disc and install again ubuntu 

any ideas ?

thank you

---

### Post by petalotis on 2012-03-19
ubuntu live cd doesn't work but finally gparted live cd works and doing my job

thanks community for previous posts!

---

### Post by ezhilRaj on 2012-04-25
Hai all,

I have compiled the kernel 2.6.25 source code from [www.kernel.org.After]("http://www.kernel.org.after/") compilation ,when i am trying to boot my image(kernel image),i got below errors.

Please let me know the solution for this problem ......

Note:I followed grub.cfg and initrams steps. 

**************************************************  ***********
Decompressing Linux ....done
Booting the kernel.
[8.326933]Cpufreq:No nForce2 chipset
mount :Mounting none on /dev Failed:No such device
udevd[62]:error getting socket:Invalid argument error initializing netlink socket
udevd[62]:error initializing netlink socket.

libudev:udev_Monitor_new_from_netlink:error gettingsocket:Invalid   argument Segmentation fault.Gave up waiting for root device,common   problems:
         -Boot args(cat /proc/cmdline)
                -check   root delay =(did the system wait long enough ?)
                -check root =(did the system wait for the right device ?)
        -missing modules (cat /proc/modules: ls /dev)
ALERT ! /dev/disk/by_uuid/33e3e/e4-131c-4e47-84ca-633a80bbec87 does not exist.Dropping to shell !

BusyBox v1.13.3(ubuntu 1:1.13.3-1ubuntu11)built-in shell(ash)
Enter 'F' help for a list of builtin commands
(initramfs)

**************************************************  ***************

---

### Post by kiyop on 2012-04-29
> **ezhilRaj said:**
> ALERT ! /dev/disk/by_uuid/33e3e/e4-131c-4e47-84ca-633a80bbec87 does not exist.Dropping to shell !
"by[COLOR=red]_[/COLOR]uuid" and "33e3e[COLOR=red]/[/COLOR]e4" are typo, are not they?

If they are not typo, correct the line in /boot/grub/grub.cfg or /boot/grub/menu.lst, so that root partition is correctly mounted at boot time. 

As is written in above #3 and #4, file system check (and repair) by "fsck" may solve your problem.

Or you may need some modules to mount your root partition. If so, incorporate them into initramfs (initrd).
You can boot with Ubuntu live cd and "chroot" and add the necessary module names in /etc/initramfs-tools/modules and execute "update-initramfs".
For details, execute
```
man chroot
man update-initramfs
```

---

### Post by omshankar on 2013-02-23
thank u ryman.
for your useful post.

---

### Post by codemaniac on 2013-02-23
Old thread is closed now.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

