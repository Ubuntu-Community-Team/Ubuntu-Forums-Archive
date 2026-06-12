---
title: "Ubuntu hates me and I'm begining to hate it back"
date: 2010-05-05
forum: General Help
---

### Post by Colo2 on 2010-05-05
I decided to upgrade to 10.04 today. So i left it, left the laptop open and downloading (because it takes ages)

When I returned, I had an error message, I can't quite recall what it said, something about insufficient network resources?

the ubuntu logo from the menu had disapeared, many of my system bar icons had turned white, I had gone offline and my network icon had disapeared.

So I rebooted!

Just gives me a load of writing, a screen full. And kinda keeps repeating itself. 

What happend? and how can I fix it?

---

### Post by Colo2 on 2010-05-05
is this a kernel problem?

---

### Post by Colo2 on 2010-05-05
> /etc/apparmor/initramfs: No such file or directory

That is the first error

---

### Post by philinux on 2010-05-05
It looks like the upgrade failed badly.

Have you got home on it's own partition? Did you back up your stuff before the upgrade?

---

### Post by phibit on 2010-05-05
Hi,

From my (limited) experience, I can offer the following advice, to be taken with a grain of salt.

**Preamble:**
If you're not concerned about data loss, you might want to consider reinstalling 10.04 from scratch. This will probably yield better results for you. If you are able to back up your data using the LiveCD, I invite you to do this if you have not already done so.
Again, the best solution is probably a clean install.

**Assumptions:**
[LIST]
[*]You are using GRUB as your boot-loader.
[*]You have a simple configuration. No RAID, no quad boot etc...
[*]You have a LiveCD available
[*]You understand EACH of the commands listed below.
[*]Given the mention of initramfs, it sounds like your images need to be updated.
[/LIST]

If you don't meet any of the above criteria, you should be weary of the solution I am proposing. These commands can make your situation worse, and potentially cause loss of data.

**Solution:**
[LIST=1]
[*]Boot into the LiveCD and choose "Try Ubuntu". Open a terminal.
[*]Mount your root filesystem with ```
sudo mount /dev/sdXY /mnt
``` where X and Y correspond to the drive letter and partition number of your root filesystem.
[*]Run the command ```
sudo mount --bind /dev /mnt/dev  && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
```
[*]Run ```
sudo chroot /mnt
``` to change-root to /mnt
[*]Now you have a root shell on your main hard drive, run ```
update-grub
```
[*]Run ```
grub-install /dev/sdX
``` where X is the drive you have ubuntu installed on
[/LIST]

Read and follow the above instructions carefully, and make sure you understand what each of them does. If you don't, please ask before executing them, or look it up.

Good Luck!

---

### Post by Colo2 on 2010-05-05
thank you for your posts.

> sudo mount --bind /dev /mnt/dev  && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys

> mount: mount point /mnt/dev does not exist

Am I doing something stupid?

---

### Post by phibit on 2010-05-05
No, I don't think you're doing something stupid. This could be an indication of another problem.

Did ```
sudo mount /dev/sdXY /mnt
``` run correctly? And can you explain how your hard drives are configured? Post the results of ```
sudo fdisk -l
``` and specify where Ubuntu is installed.

---

### Post by Colo2 on 2010-05-05
Hey
thanks for the reply.
The problem was I was using a 2nd ubuntu install to try and fix this problem as oposed to a livecd, I guess the 2nd install isn't working properly. I booted from my livecd and that command seems to work now, so I'll see what else happens :)

thanks

---

### Post by tgalati4 on 2010-05-05
First things first.

Do you have a Live CD of any version of Ubuntu?

If so, boot with it using the rescue kernel (root, text, console).

I presume you have only one disk drive on this laptop.

In the terminal:

fdisk -l
fsck /dev/sda1
fsck /dev/sda2
.
.
.
For all partitions listed by fdisk -l
You don't need to check swap.

Once all your drives are "clean", then try a normal boot and tell us how far you get.

Your initramfs error is troubling.  Yes, it is a kernel problem.  The initramfs is the initial RAM filesystem--a mini-kernel that resides completely in RAM and is used to bootstrap the rest of the kernel.  So it's minilinux being used to boot the rest of linux.

Whenever a new kernel is written (through a dist-upgrade) the initramfs has to be rewritten.  Apparmor flagged it because it is missing.  Apparmor keeps track of critical system files and lets you know if they have been corrupted.  Repair from this point will be tricky.

After checking your drive partitions, when booting, hit the "escape" key and that should bring up GRUB.  Choose an earlier kernel entry and hit return.  See if your system boots.

---

### Post by phibit on 2010-05-05
@tgalati4
You think it's a file system error?

@Colo2
Out of curiosity, why are you trying to rescue this installation? To save data? You would be MUCH better off to reinstall ubuntu from scratch, repartitioning and reformatting your drive with the LiveCD.

---

### Post by Colo2 on 2010-05-05
Urm.

Thanks for your help guys, I did everything advised to me, rebooted and I realised that my grub list has more in it than last time. I selected the top one and it a big purple loading screen with "ubuntu 10.04" written in the middle and 4 orange and white dots in a loading motion.

... Thing is, it's been like this for ages now...

and yeah, I want my data, and also I've spent ages configuring this install to the way I like it, it's a shame if I then have to re-install.

---

### Post by Colo2 on 2010-05-05
Alright, it failed.

Same problem as last time, just it seems very 10.04 themed this time. :(

---

### Post by Colo2 on 2010-05-05
* double post by accident *

---

### Post by phibit on 2010-05-05
I understand about wanting to keep your configurations, but sometimes a vanilla install can fix a lot of "bugs" you've had. You also generally see performance improvements, so don't feel bad about reformatting as an option. Think about it this way: with all the new things you know about Ubuntu, you'll probably be able to configure your new install much faster and sleeker than ever.

Casting aside that option for the moment, let's take a look at another option. Reinstalling 10.04 WITHOUT reformatting your root partition. I'm not sure if you know this, but you can reinstall ubuntu ON TOP of an existing installation, and it will keep your /home directory completely in tact (but you need to be very careful you are not FORMATTING your root partition).

The downside to this solution is that you lose all the programs you have installed (i.e. the /usr directory is whiped). The upside is that when you do re-install these applications, since all your settings are saved in your /home directory, you will get back your old configurations. This particular option has saved me many times.

If you need instructions for the above-mentioned solution, don't be shy to ask.

---

### Post by Niva on 2010-05-05
The cardinal rule of upgrading an operating system (any of them):

[COLOR="Red"][SIZE="5"]**DON'T DO IT!**[/SIZE][/COLOR]

The concept is grand but it rarely works w/o problems.  Just back up your data and do a clean install from scratch.

---

### Post by phibit on 2010-05-05
@Niva I tend to agree with you... That's why I've recently moved my /home directory to a seperate partition, to keep it safe from the poison of upgrading. My 9.10 -> 10.04 upgrade failed miserably so I did a clean install. Love it now <3.

---

### Post by Colo2 on 2010-05-05
thank you for your kind responses. 

I will do a clean re-install... if what I'm doing at the moment doesnt work....
Dont ask me what it's doing, I havent got a clue, but it's doing something xD

---

### Post by Colo2 on 2010-05-05
wow
I can't believe it fixed it.

It was the recovery disk, DPKG - fix broken packages. It took about 20 minutes, but it booted my system into 10.04 absolutely fine...

;D thanks for all your time guys.

---

### Post by phibit on 2010-05-05
Glad you got it working!

---

### Post by bodhi.zazen on 2010-05-05
> **Colo2 said:**
> thank you for your kind responses. 

I will do a clean re-install... if what I'm doing at the moment doesnt work....
Dont ask me what it's doing, I havent got a clue, but it's doing something xD

Failed upgrades typically leave your system very disrupted.

You may also have upgraded fine, but have run into any number of bugs, known and unknown.

I suggest you :

1. boot the Ubuntu 10.04 desktip (live CD).

2. Assuming your system boots, plug in a large flash drive and back up your data.

3. Reinstall.

You can also try to see what errors, if any, you are getting as you boot.

Re-boot, hit esc / hold the shift key to get the grub boot menu.

Edit the boot line (press e) , look for the line that starts "linux", simply edit (delete) the works "quite" and "splash" 

Boot with Ctrl-x

Post any error messages or tell us where is seems to lock up.

---

### Post by tgalati4 on 2010-05-06
Well, you beat me to it.  By booting to a root shell, you were able to use dpkg's excellent recovery system.  Now, you may have some strangeness from this installation, but it's no worse than a clean install because Lucid is kind of buggy anyway.  Over time, as package updates roll in, your system will become more stable.  Since this is an LTS, you can look forward to several years of updates.

The unattended disto-upgrade should have worked.  But I have noticed a decline in stability of Ubuntu releases.  I don't know if it's the 6-month release schedule, or all the new stuff they are trying to cram into a CD or Ubuntu craptastic, such as notify-osd.

So the lesson learned is that you can't leave upgrades unattended.  You have to treat them like windows updates--expect breakage and random reboots leaving you staring at a blank screen.

---

