---
title: "Black Screen?"
date: 2011-08-01
forum: General Help
---

### Post by Unpack on 2011-08-01
I'm extremely new to Ubuntu but curious about trying it out. I downloaded it (Ubuntu 11.04) and burned the iso and rebooted it to try it out before i decide to install it or dual boot it. After the reboot the 2 icons appear at the bottom of my screen and then an Ubuntu logo with several dots appear then my screen the my screen turns black and nothing happens. I changed BIOS so my CD drive is the first to boot from and still nothing. Anyone know whats happening? My laptops specs aren't the best but above the necessary amount needed to run. :confused:

---

### Post by ggeminii on 2011-08-01
Switch to virtual terminal when you reach the screen with ubuntu logo and dots by pressing alt+f2 .You can see from there where it is getting stuck.Keep switching the terminals till you get to the screen where it logs the messages.

---

### Post by Unpack on 2011-08-01
> **ggeminii said:**
> Switch to virtual terminal when you reach the screen with ubuntu logo and dots by pressing alt+f2 .You can see from there where it is getting stuck.Keep switching the terminals till you get to the screen where it logs the messages.
trying it out now. Ill try scribble down what happens and reply back here.

---

### Post by Unpack on 2011-08-01
I got  
[52.212942] Kernal Panic - Not syncing Attempted to kill init!

There was some more complex code in the middle and ended with

52.213020 Panic occured, switching back to text console

Then it just froze there. I had to reboot to post back on here.

---

### Post by varunendra on 2011-08-01
> **Unpack said:**
> After the reboot the 2 icons appear at the bottom of my screen and then an Ubuntu logo with several dots appear then my screen the my screen turns black and nothing happens. I changed BIOS so my CD drive is the first to boot from and still nothing.
Hi, and welcome to the forums :)
Getting to the above screen means you are already booting from the CD, no need to change BIOS settings for it.

Now about the problem. When the CD booting starts, press and hold 'shift' key. This will bring up advanced boot menu. After choosing your language, press F6 to pop up a menu at right bottom side. In this menu, check (by pressing 'spacebar') 'acpi=off', 'noapic', and 'nomodeset'. Then press 'Enter' to boot. Post back how it goes.

---

### Post by Unpack on 2011-08-01
> **varunendra said:**
> Hi, and welcome to the forums :smile:
Getting to the above screen means you are already booting from the CD, no need to change BIOS settings for it.

Now about the problem. When the CD booting starts, press and hold  'shift' key. This will bring up advanced boot menu. After choosing your  language, press F6 to pop up a menu at right bottom side. In this menu,  check (by pressing 'spacebar') 'acpi=off', 'noapic', and 'nomodeset'.  Then press 'Enter' to boot. Post back how it goes.

Hi! And thanks for the reply. I tried out what you said and got a little further than I normally would. But then This happened.

---

### Post by nipennem on 2011-08-01
This situation has been posted many times and the few answers I've seen are:

1. Check your RAM (using memtest)
2. Make sure the Live CD you are using does not contain errors. When downloading the ISO, verify the MD5 checksum, and also make sure to verify the contents of the disk after burning.

---

### Post by Unpack on 2011-08-01
> **nipennem said:**
> This situation has been posted many times and the few answers I've seen are:

1. Check your RAM (using memtest)
2. Make sure the Live CD you are using does not contain errors. When downloading the ISO, verify the MD5 checksum, and also make sure to verify the contents of the disk after burning.
I ran a MD5 checksum on the iso I downloaded with winMD5Sum and it says that they are different, but, I ran a checksum of other files and it says theyre all different. I'm not to sure whats happening there. I'm still trying to get memtest to boot. I just need to find another blank cd lying around.

Edit: checked MD5 checksum and everything checked out. Checked the CD for errors by pressing any key during the boot, selecting my language, and checking the "check Cd for defects" and it found 1 error. Going to buy some cheap blanks in a bit to get a working copy using the help.ubuntu.com guides and going to post what happens

---

### Post by varunendra on 2011-08-01
> **Unpack said:**
> Edit: checked MD5 checksum and everything checked out. Checked the CD for errors by pressing any key during the boot, selecting my language, and checking the "check Cd for defects" and it found 1 error. Going to buy some cheap blanks in a bit to get a working copy using the help.ubuntu.com guides and going to post what happens
If you have a USB flash drive (>=1GB) lying around it, you may try making it a Live USB and install from it.

---

### Post by Unpack on 2011-08-01
Okay, I've successfully created a working copy of ubuntu 11.04 by burning at x4 speed. I tried it out, but, WOW was it slow. I clicked firefox and waited for about 6-7 minutes (all the while the "Examples" file and the "Install Ubuntu" file were flashing periodically on the left side and all the icons that were supposed to be there were gone) for it to start and it never did. I got frustrated and just restarted.

---

### Post by varunendra on 2011-08-01
> **Unpack said:**
> Okay, I've successfully created a working copy of ubuntu 11.04 by burning at x4 speed. I tried it out, but, WOW was it slow. I clicked firefox and waited for about 6-7 minutes (all the while the "Examples" file and the "Install Ubuntu" file were flashing periodically on the left side and all the icons that were supposed to be there were gone) for it to start and it never did. I got frustrated and just restarted.
What are the specs of your laptop? Model no? Try booting into Ubuntu Classic mode (you can select it from the login screen) to see if avoiding unity gives any performance gain.

---

### Post by Unpack on 2011-08-01
> **varunendra said:**
> What are the specs of your laptop? Model no? Try booting into Ubuntu Classic mode (you can select it from the login screen) to see if avoiding unity gives any performance gain.

I have Windows XP, version 2002, sp2, 1.73ghz and 502 MB of RAM (Its actually 1gb I honestly dont know why windows xp reads it as 502) I was only trying it out on Live. I didnt want to dual boot or install it without trying it out.

---

### Post by varunendra on 2011-08-01
> **Unpack said:**
> I have Windows XP, version 2002, sp2, 1.73ghz and 502 MB of RAM (Its actually 1gb I honestly dont know why windows xp reads it as 502) I was only trying it out on Live. I didnt want to dual boot or install it without trying it out.
502 is a bit low for 11.04. Also, in live cd mode, all of the running stuff resides in the memory, so it gets even lesser. Running it from hard drive (of course after installation) will definitely improve performance, but for 11.04, 1 GB is recommended (although not officially).

As for 1GB showing up as 502 MB only, there are two possibilities:

[LIST=1]
[*]rest of the memory is shared by onboard graphics adapter. Check this in BIOS and set it to a lower value if possible
[*]if you have two 512 MB modules, maybe one of them isn't detected at all due to some problem. Confirm this.
[/LIST]

---

### Post by EkuquoL on 2011-08-01
You could have a dusty cdrom... Which would result in corrupted data on thT isO file or the cd is just not reading correctly..

---

### Post by Unpack on 2011-08-01
> **varunendra said:**
> 

[LIST=1]
[*]rest of the memory is shared by onboard graphics adapter. Check this in BIOS and set it to a lower value if possible
[*]if you have two 512 MB modules, maybe one of them isn't detected at all due to some problem. Confirm this.
[/LIST]


I ran GPU-Z and its definitely detected. Ill check my BIOS for anything being shared. What if I Dual Boot? Will it improve performance? and if im unsatisfied will i be able to uninstall it?

---

### Post by varunendra on 2011-08-02
> **Unpack said:**
> I ran GPU-Z and its definitely detected. Ill check my BIOS for anything being shared. What if I Dual Boot? Will it improve performance? and if im unsatisfied will i be able to uninstall it?
Dual boot will have exactly same performance as single boot (ubuntu-only) and will definitely be much better and faster than CD. If you later need to uninstall Ubuntu, you can do it very easily by just removing the ubuntu partition, BUT then you'll also need your XP CD to restore MBR. Although there are also workarounds, like installing lilo, if you don't have XP CD and you need to restore its MBR removing grub from there.

But I'll suggest to try it from Live USB first before installing to hard drive. USB will give faster performance than CD and using live session you can make sure whether all your hardware is supported or not. Since Live USB is a persistent install, you can also install and try proprietary drivers on it in case you need one, maybe for your graphics or wifi.

Also, if there seems no way to release more amount of RAM from BIOS and you find yourself stuck with that 502 MB only RAM, you may wish to try 10.04.3 LTS against 11.04

---

### Post by Unpack on 2011-08-02
> **varunendra said:**
> Dual boot will have exactly same performance as single boot (ubuntu-only) and will definitely be much better and faster than CD. If you later need to uninstall Ubuntu, you can do it very easily by just removing the ubuntu partition, BUT then you'll also need your XP CD to restore MBR. Although there are also workarounds, like installing lilo, if you don't have XP CD and you need to restore its MBR removing grub from there.

But I'll suggest to try it from Live USB first before installing to hard drive. USB will give faster performance than CD and using live session you can make sure whether all your hardware is supported or not. Since Live USB is a persistent install, you can also install and try proprietary drivers on it in case you need one, maybe for your graphics or wifi.

Also, if there seems no way to release more amount of RAM from BIOS and you find yourself stuck with that 502 MB only RAM, you may wish to try 10.04.3 LTS against 11.04
Yeah i tried to free up some RAM with no luck. I might just have to downgrade and try it out for a while. I just really didnt want to do that in fear of any previous bugs or anything still being in there.

---

### Post by varunendra on 2011-08-02
> **Unpack said:**
> Yeah i tried to free up some RAM with no luck. I might just have to downgrade and try it out for a while. I just really didnt want to do that in fear of any previous bugs or anything still being in there.
Actually 'LTS' (Long Term Support) means a well tested and most compatible, most stable version. Any 'latest' release is supposed to have more bugs than any previous (LTS or non-LTS) release. Although it definitely includes latest drivers and expectedly 'improved' kernel which has previous bug-fixes included, but then again it is prone to new bugs :). Thus for most people, who prefer stability, the latest 'LTS' is recommended.

---

### Post by Unpack on 2011-08-02
> **varunendra said:**
> Actually 'LTS' (Long Term Support) means a well tested and most compatible, most stable version. Any 'latest' release is supposed to have more bugs than any previous (LTS or non-LTS) release. Although it definitely includes latest drivers and expectedly 'improved' kernel which has previous bug-fixes included, but then again it is prone to new bugs :). Thus for most people, who prefer stability, the latest 'LTS' is recommended.
Gotcha. Thanks very much for your help varunendra. I appreciate it immensely. Im downloading it right now and hope to get to know ubuntu a lot more in the near future! :)

---

### Post by varunendra on 2011-08-02
> **Unpack said:**
> Gotcha. Thanks very much for your help varunendra. I appreciate it immensely. Im downloading it right now and hope to get to know ubuntu a lot more in the near future! :)
You're welcome!

Just try it in live mode to see if it supports your hardware properly. If not, you may try 11.04 with 'nomodeset', 'acpi=off' and 'noapic' options in advance boot menu of the live cd. To get the advance menu (in any ubuntu live cd) press any key (sometimes shift only) during boot up. Then after selecting language, press F6.

Hope you won't need these. :) Let us know how it goes after trying it.

---

