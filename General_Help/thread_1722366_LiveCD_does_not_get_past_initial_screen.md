---
title: "LiveCD does not get past initial screen"
date: 2011-04-05
forum: General Help
---

### Post by Acedrew89 on 2011-04-05
Hello all,

My laptop recently died and I have invested in a new desktop. The specs are as follows;

AMD II x4 3.0GHz
Biostar 880A Motherboard
Radeon HD 4670
Western Digital 500gig HDD
and other minor peripherals (Wireless keyboard and mouse, monitor,etc.)

Anyhow, I had been running 10.10 on that laptop. Everything ran swimmingly (until the internal components died of course). I am currently running XP on the desktop and am looking to run 10.10 again as a dual boot. I already partitioned off 200gigs for Ubuntu upon set up of XP. I have tried using the USB LiveCD I used for my first install on the laptop, as well as a LiveCD CD I had created for the laptop. Neither one worked. The LiveCD came up with an error and the USB got to the point where there was the purple screen with white dots and it never got past that point.

I downloaded a brand new 10.10 disc earlier today and I got to the point where the white line blinks on the black screen. Unfortunately that is as far as the boot got. It has some initial writing at the top of the screen saying it was loading a process, and then it produced an error of a int file of some sort. I'll go back and try it again and get a better grasp on the error. Also, after the error message I was given the ability to type commands (it actually told me to type 'help' for a list of the commands available to me), but I had no clue what to do with them.

I'm currently downloading 10.04 to see if the more stable version will load. I'll let you know if it works.

Thanks in advance for any help.

---

### Post by drs305 on 2011-04-05
The blinking white cursor may indicate a video problem. Even with the LiveCD, you may need to turn off some of the kernel options. In this case I'd start with "nomodeset", but it could be one of the others. 

You use the F6 key to get to the options early in the LiveCD boot process. Here's a link to a community doc I created with more explanations:
[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by Acedrew89 on 2011-04-05
Thank you so much for the link. I already came across that and I don't actually get to any of those screens in the boot process. It is only black and no menu icons like all of the screen captures show in the document. I'll still give F6 a try and let you know though. Thanks for the quick response and the help.

---

### Post by Acedrew89 on 2011-04-05
Also if this indeed turns out to be the case, does that mean I will have to make these changes every time I boot Ubuntu?

---

### Post by drs305 on 2011-04-06
> **Acedrew89 said:**
> Also if this indeed turns out to be the case, does that mean I will have to make these changes every time I boot Ubuntu?

No. The options available on boot are kernel options which can be placed in the Grub2 menu entries so they are automatically entered. And they may not be necessary once drivers or other packages are installed.

For example, often the 'nomodeset' option is no longer necessary once a proprietary video card is installed after the Ubuntu installation is completed.

---

### Post by Acedrew89 on 2011-04-06
Okay, so I retried the initial boot with the LiveCD. I hit F6 and got pressed enter at the 'nomodeset' and an 'X' appeared next to it. I rebooted and the same error message came up from the last time. This time I wrote it down on paper so here it is;

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on filesystem.squashfs


I'm unsure as to what to do, but apparently there are options since it gives me the ability to perform a list of commands.

---

### Post by Quackers on 2011-04-06
Use the usb stick to boot from.
At the first purple screen (the one with the little man icon at the bottom) press any key. Choose your language and at the next screen press F6.
The nomodeset option will appear. Choose that and see if the live desktop will then load.

---

### Post by drs305 on 2011-04-06
You can select more than one of the options. Since we don't know where the problem lies you might try selecting more (or all) of them. In addition to the preset options, you can add your own, such as "i915.modeset=0 xforcevesa" or any other valid options, should you or someone else recommend additional options.

Also, have you checked the disk integrity? You mentioned a previous installation so I'm assuming the CD has worked in the past. Here is a link to a bug report that, while not necessarily relating to your issue, has a good list of things to check regarding the CD reliability:
[https://answers.launchpad.net/ubuntu/+question/122179]("https://answers.launchpad.net/ubuntu/+question/122179")

---

### Post by techunit on 2011-04-06
I'll bet the CD is bad or missing components. I want to assume that he actually burned the image to the CD instead of just putting the unextracted image file in the drive.
From what he has said it sounds like he burned it correctly.

However I don't think he made sure to run MD5SUM check on the disk. What did you burn the disk with. 

If you have had Ubuntu on the computer in the past you probably don't have a video problem.

I hope this helps. It could be as simple as reburning the disk slower and run a MD5SUM check on it at the end.

---

### Post by Acedrew89 on 2011-04-06
Okay, so I downloaded 10.04.2 instead of redownloading 10.10 just to be safe. I also remembered that since my XP version is a 32bit system it doesn't read all of my 4gigs of RAM properly. I also noticed that at some point in the error message it mentioned RAM. So, I downloaded the 64bit version of 10.04.2. When I burned that .ISO to a cd via the program the Ubuntu website suggests and attempted to boot from that cd it worked fine. The only issue was the fact that it was running really slowly. I am up and running and really the only snag I've met so far is that my wireless adapter isn't supported by Linux. Other than that its running smoothly now that its installed and I'm currently upgrading to 10.10. I'm not sure what the true problem was but it appears to have settled out for now. I think it was the RAM thing but I could definitely be wrong. Thank you all for your help and quick responses.

---

### Post by drs305 on 2011-04-06
:-)

Would you please mark this thread 'Solved' via the 'Thread Tools' link at the top right of the first post if you don't have any other issues? If you want help with the wireless you will probably get a better response by opening a new thread. 

Happy Ubuntu-ing !

---

