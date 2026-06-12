---
title: "I want my bootloader back!"
date: 2010-12-01
forum: General Help
---

### Post by ninjaaron on 2010-12-01
I installed Jolicloud in a new partition to give it a try. It's pretty nice. Anyway, it took over my bootloader, which didn't really bother me.

Now my kernel has automatically been updated to 2.6.35-22.41 or something. The option to boot from the new kernel does not appear. As you might imagine, I want to do that. My old bootloader updated this stuff automatically.

What to do?

---

### Post by carl4926 on 2010-12-01
Are you able to boot an older kernel and run

```
sudo update-grub
```

---

### Post by ninjaaron on 2010-12-01
I tired to do that in Jolicloud and in Ubuntu. It ran apparently without errors in both cases. There is no change in my boot menu.

To be a little more specific, what was updated were linux-headers for Linux kernel 2.6.35. I should have something different in my boot menu, right?

---

### Post by WorMzy on 2010-12-01
If it was just linux-headers, then no. Only linux-image updates warrant a new grub entry. The most recent kernel for Ubuntu is 2.6.35-23.41, is that what you're seeing in grub? What do you get if you open a terminal and run ```
uname -a
```

---

### Post by ninjaaron on 2010-12-01
No. I ran the command, and it says I'm running 2.6.32-25-generic, which is exactly what the bootloader says.

---

### Post by matt_symes on 2010-12-01
Hi

To list your kernels open a terminal and type

ls /boot

Your kernels will be of the type vmlinuz-2.6..... To find your newest kernel, find the one with the highest numbers.

If this is the same as your bootloader then you are using the newest kernel.

Kind regards

---

### Post by WorMzy on 2010-12-01
That's the kernel that Lucid came with, so I guess you're not using Maverick? Are you sure you have the latest kernel (2.6.32.26.28 for Lucid) installed? You can check dpkg if you're not sure

```
dpkg -l 'linux-image*'
```

"uu" on the left means the package is not installed, "ii" means that it is.

---

### Post by stinkeye on 2010-12-01
> **ninjaaron said:**
> I tired to do that in Jolicloud and in Ubuntu. It ran apparently without errors in both cases. There is no change in my boot menu.

To be a little more specific, what was updated were linux-headers for Linux kernel 2.6.35. I should have something different in my boot menu, right?

I wondered this too. Why the kernel number didn't change sometimes when I got kernel updates.

I don't understand kernel numbering but it appears the actual version of the
kernel is not shown in grub.

eg **uname -a** gives```
Linux MavMusic 2.6.35-23-generic #[COLOR="Magenta"]41[/COLOR]-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux
```


Where grub only shows
```
2.6.35-23-generic
```
 

And I suppose the full kernel number is ```
2.6.35-23.[COLOR="#ff00ff"]41[/COLOR]
```

---

### Post by ninjaaron on 2010-12-01
I am using 10.10, but for some reason I didn't have the kernel updater checked. I checked it, got it, updated grub, rebooted... and... it's not in the boot menu. Back to square one.

The reason for this, as I've been saying from the beginning, apparently is that the /boot folder on Jolicloud is controlling the booting, not /boot in Ubuntu... or at least I think that's the problem. It even looks totally different than Ubuntu's.

I know how to go in and enter the new kernel manually, but I want it to do it itself so I don't have to bother with it every time.

---

### Post by matt_symes on 2010-12-01
Hi

Sound like you need to reinstall Grubs Stage 1 bootloader to the MBR.

You can do that from the LiveCD. Boot into the live CD Open up a terminal and mount Ubuntus partition and reinstall grub. At the terminal type 

sudo mount /dev/sd**XY** /mnt[FONT=monospace]

[/FONT]sudo grub-install --root-directory=/mnt /dev/sd**X**

Where X is your drive and Y is the partition. Notice the second command only uses the drive.

I.E sda and sda5. Change to suit your setup.

Then you may need to update grub

Kind regards

---

### Post by ninjaaron on 2010-12-01
trying now... be back in a few.

---

### Post by ninjaaron on 2010-12-01
Didn't seem to work. I installed grub from a Live USB as per your directions, and it worked. When I booted, it was still the Jolicloud bootloader. Ran update-grub, which is clearly recognizing the new kernel, restarted, and got the Jolicloud bootloader again.

---

### Post by ninjaaron on 2010-12-01
Hmmm... could this have anything to do with the fact the the original window's boot partition is still there, or is that ok?

---

### Post by matt_symes on 2010-12-01
Hi

Run this script. The instructions are on the main page. Post the results back between code tags.
It will show exactly what is going on with your system.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Kind regards

---

### Post by ninjaaron on 2010-12-01
> **matt_symes said:**
> Hi

Sound like you need to reinstall Grubs Stage 1 bootloader to the MBR.

You can do that from the LiveCD. Boot into the live CD Open up a terminal and mount Ubuntus partition and reinstall grub. At the terminal type 

sudo mount /dev/sd**XY** /mnt[FONT=monospace]

[/FONT]sudo grub-install --root-directory=/mnt /dev/sd**X**

Where X is your drive and Y is the partition. Notice the second command only uses the drive.

I.E sda and sda5. Change to suit your setup.

Then you may need to update grub

Kind regards

I went back and gave this a second shot, and I realised that it didn't actually work the first time, I just didn't read the prompt carefully enough.

I got this output:
install_device not specified.

and then a print out of the --help page. It says the syntax is "grub-install [OPTION] install_device"

the line you specifies the option, but not the device. I don't even know what a device is in this context. This becomes all the more relevant because I was playing with the Chrome OS RC Live CD, trying to install it on a USB stick, and somehow it managed to completely wreck the bootloader... so I'm typing this off my live Ubuntu USB... so the whole thing has become a bit more pressing. All my files and partitions are still there, so no big deal, but I can't boot them... but now I'm desperately interested in getting this command to work. I'll check the man and do some searching. If you know something, I'll be glad to hear it.

---

### Post by oldfred on 2010-12-01
the boot script will clarify things. matt_symes instructions will work if you are using the correct partition for Ubuntu and do not have a separate /boot partition.

If you can boot into your Ubuntu install, you can just install grub2 to the MBR from that (it in effect knows where is it mounted itself so you do not need that step, just grub-install):

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda

sudo update-grub

---

### Post by ninjaaron on 2010-12-02
ok, it turns out I just entered the command that matt_symes gave me incorrectly. I didn't see the space between "/mnt" and "/dev/sda". I figured it out after I did a search for "grub-install" on Google.

I reran the command with the space and it worked. Grub is Back, and the new kernel is in my boot menu.

Thanks for the help guys.

just one problem now... when I try to boot that new kernel, I get a message that it cant find "/lib/modules/2.6.35-23-generic/modules.dep"

I checked the harddrive manually, and I can find it. I don't know what the bootloader's problem is.

I just want to use the latest supported kernel damnit! Is that so much to ask!?

---

### Post by matt_symes on 2010-12-02
Hi

Glad you got the dual boot up.

Have a look at these....

[https://bugs.launchpad.net/linux/+bug/668045](https://bugs.launchpad.net/linux/+bug/668045)
[http://ubuntuforums.org/showthread.php?t=1622166](http://ubuntuforums.org/showthread.php?t=1622166)

What happens when you boot into an older kernel?

Can you boot into the new kernel at all?

 > I don't know what the bootloader's problem is.

Yes. That's not an issue with the bootloader.

Kind regards

---

### Post by ninjaaron on 2010-12-02
So that's that, huh. Looks like the kernel still booted for most of these guys despite the error. Not for me.

Oh well, I guess I'll just wait for the next kernel or something.

Thanks again for all your help

---

