---
title: "Laptop Won't Boot From CD MD5Sum Error"
date: 2010-07-17
forum: General Help
---

### Post by mkw87 on 2010-07-17
I am trying to install Ubuntu/Xubuntu on an older HP Pavilion zt1230 laptop with 256mb of memory (243 using 1mb=1024....) and I can't get it to boot ANY disc I have burned.  I have burned that latest Ubuntu and Xubuntu 10.04 live cd's and the alternate cd using good quality Memorex cd's at the lowest speed my burner supports, 4x.  The laptop will read the cd's in windows, but will not boot from them throwing a MD5Sum error.  

I gave up on booting from the cd's and figured I would try network booting since the laptop does not support booting from a thumb drive.  I got it to finally recognize my computer during the network boot, see the boot file, but it fails with an ARP timeout and I couldn't solve that issue.

My last attempt was to use Wubi to see how this thing will even run on Xubuntu.  However, I cannot launch Wubi in windows, it says there is a configuration error.  

After reading here, I downloaded older versions of Wubi and got the 8.10 rev507 to launch, but it fails to connect to the server.  I am currently downloading the 8.10 iso and hoping wubi will recognize it and use it to install from, but I have little hope.

Summary: 
-Tried to boot from cd, but all fail with bad md5sum (I know the burn is good though)
-Burns were made on good media at slow speeds
-Booting from thumb drive is not an option
-Can't network boot for some reason
-Newer versions of Wubi won't launch, 8.10 version launches but can't connect to servers to install

At some point I got one of the cd's to install Grub, and I can get to it but am not sure if using it's command line could even help me.  Does anyone have any tips on getting the laptop to read the cd's?  It has a DVD-ROM drive in it if that helps.....

---

### Post by bobcollard on 2010-07-17
I am not sure of your brand, but, my Dell uses F12 to change the BIOS to startup with different media such as USB or CD/DVD.  Check you Computer Company for advice.

---

### Post by Lucradia on 2010-07-17
Have you "accidentally" **_*restart*_** your computer ever while the liveCD was still operating?

Linux disallows the liveCD to be ejected if you do this, and a full shutdown (power off) is required when it happens to return control of the drive.

This "can" damage your drive if you do it continuously (seeing as the drive won't work correctly still even if you force eject using paperclip.)

---

### Post by Rubi1200 on 2010-07-17
Are these the specs. for the laptop?

> Laptop: Intel Centrino Duo T2300 | 2 GB Ram | Intel 945GM Graphics | Intel 3945ABG Wireless             The issue may well be to do with the graphics card rather than how you burnt the CD etc.

Try this and see what happens:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards using the arrow key and remove quiet splash;

Add the following parameter:

i915.modeset=1

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04

---

### Post by gordintoronto on 2010-07-17
The computer does not have enough memory for what you are trying to do. Try Lubuntu.

---

### Post by JC Cheloven on 2010-07-18
> **Rubi1200 said:**
> Are these the specs. for the laptop?

The issue may well be to do with the graphics card rather than how you burnt the CD etc. Try this and see what happens:
Put the LiveCD in and boot up;
when you see the Ubuntu logo hit Enter;
Choose language and leave the default Try as a live cd or whatever it says again;
Important: hit F6 and then Esc to see the boot line
**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**
Now, again this is important, move the cursor backwards using the arrow key and remove quiet splash;
Add the following parameter:
i915.modeset=1

In other words, the boot should look like this:
**file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04

I wish to send you [SIZE="5"]my warmests thanks[/SIZE] for that. I've a crappy Toshiba A50 laptop with intel 82852/855GM integrated graphics. It had installation problems since gutsy (at least managed to boot with some options), and which hasn't accepted anything newer than jaunty. The best I succeded to do with a "current" version was installing LUbuntu (lucid) in safe graphics mode. I was pretty sure that there should be a boot option which would circunvent the problem, but I didn't find it after long digging in Ubuntu & Debian's documentation. And here it is. Lucid installed with compiz effects working, he he :D

Just to make it more complete:
The outlined procedure works for booting from live cd, but the kernel modesetting isn't inherited by the installation in hd. You should edit the grub command line at each boot, OR, to make it permanent, still from live cd:
- Navigate to the recently installed Ubuntu in hard disk
- Edit the file /etc/default/grub  as superuser
- Look for the line GRUB_CMDLINE_LINUX_DEFAULT=&#8220;quiet splash&#8221;
- Edit it so that: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;i915.modeset=1&#8221;

If it worked live, it should work from hd (does for me)
Greetings
JC
________________

---

