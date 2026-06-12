---
title: "Will not boot after update manager"
date: 2010-11-25
forum: General Help
---

### Post by drewhops on 2010-11-25
I'm a Ubuntu newbie, and I have a major problem. I ran the update manager this morning on both a Lemur Ultrathin and the Meerkat Ion Nettop. In both cases, the update manager returned the message that GRUB could not find the proper boot volume to install to. In both cases, I chose to install to the two available options since the help message suggested that might be a good idea if I didn't know which one was the boot volume.

The Lemur notebook boots just fine. Unfortunately, the Meerkat desktop will not boot. There's a blinking cursor about five lines down the screen and it will not accept any key commands. Any advice is appreciated.

---

### Post by Hippytaff on 2010-11-25
hi and welcome :-)

With a liveCD can you boot into you 10.10 box and post the results.txt to this script - [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

it will help everone who knows more about thiis than me diagnose and fix the problem :-)

---

### Post by drs305 on 2010-11-25
> **drewhops said:**
> ... the Meerkat desktop will not boot. There's a blinking cursor about five lines down the screen and it will not accept any key commands. Any advice is appreciated.

This doesn't sound like a grub problem, since there is no "grub" or "grub rescue" prompt. So the most likely issue is a video problem. 

If you don't see the Grub menu as you boot, hold down the SHIFT key early on and see if it appears.

Once you get to the Grub2 menu, highlight the first item (or the one you boot) and press "e" to get to the edit mode.

At the end of the line beginning with "linux", remove "quiet splash" and add "nomodeset" (no quotes). Press CTRL-x and see if it now boots. If it does, then go to System, Administration, Additional Drivers/Hardware Drivers and try adding your video card.

Another option is to boot to the recovery mode. If you don't see that option, remove "quiet splash" as above and add "single". Press CTRL-x and see if any of the recovery items fixes your system.

---

### Post by drewhops on 2010-11-25
Thanks for the quick response. I found (too late I guess) the system76 forum that had the instructions for what not to do (which I did).

I have a usb memory stick available, how do I download a Ubuntu image to it that I can use to reboot the desktop? I'm running 10.4LTS

I'll happily post my results in the link you provided.

---

### Post by Hippytaff on 2010-11-25
> **drs305 said:**
> This doesn't sound like a grub problem, since there is no "grub" or "grub rescue" prompt. So the most likely issue is a video problem. 

If you don't see the Grub menu as you boot, hold down the SHIFT key early on and see if it appears.

Once you get to the Grub2 menu, highlight the first item (or the one you boot) and press "e" to get to the edit mode.

At the end of the line beginning with "linux", remove "quiet splash" and add "nomodeset" (no quotes). Press CTRL-x and see if it now boots. If it does, then go to System, Administration, Additional Drivers/Hardware Drivers and try adding your video card.

Another option is to boot to the recovery mode. If you don't see that option, remove "quiet splash" as above and add "single". Press CTRL-x and see if any of the recovery items fixes your system.

wow..I was going to wait for the results.txt before going for nomodset...just goes to show...experience is everything :-)

---

### Post by drewhops on 2010-11-25
@drs305

I'll try what you suggested.

---

### Post by drs305 on 2010-11-25
> **Hippytaff said:**
> wow..I was going to wait for the results.txt before going for nomodset...just goes to show...experience is everything :-)

We posted at the same time (sometimes it takes me a while to actually hit the send button). I would have waited for a response to your post had I seen it first.

In most cases if there isn't a grub or grub rescue prompt the issue is something other than Grub2. If the MBR is messed up, it will probably be a "grub rescue" prompt. With a "grub" prompt, there's a good chance it's an incorrect path or missing/corrupted file.

The "nomodeset" is just a guess, but there have been a lot of these the past week or so.

---

### Post by drewhops on 2010-11-25
I held down the Shift key while powering up and it still has the same screen, blinking cursor that will not accept text. How do I download a bootable image do a USB drive?

---

### Post by drs305 on 2010-11-25
> **Hippytaff said:**
> wow..I was going to wait for the results.txt before going for nomodset...just goes to show...experience is everything :-)

We posted at the same time (sometimes it takes me a while to actually hit the send button). I would have waited for a response to your post had I seen it first.

In most cases if there isn't a grub or grub rescue prompt the issue is something other than Grub2. If the MBR is messed up, it will probably be a "grub rescue" prompt. With a "grub" prompt, there's a good chance it's an incorrect path or missing/corrupted file.

The "nomodeset" is just a guess, but there have been a lot of these the past week or so.

---

### Post by Hippytaff on 2010-11-25
> **drs305 said:**
> We posted at the same time (sometimes it takes me a while to actually hit the send button). I would have waited for a response to your post had I seen it first.

In most cases if there isn't a grub or grub rescue prompt the issue is something other than Grub2. If the MBR is messed up, it will probably be a "grub rescue" prompt. With a "grub" prompt, there's a good chance it's an incorrect path or missing/corrupted file.

The "nomodeset" is just a guess, but there have been a lot of these the past week or so.

No...I respect your knowledge, so wouldn't expect you to wait for a response to my post. You know far much more than me.

I've noticed a lot of nomodset/Nvidia issues recently too, it was ralink wireless issues for a while :-)

---

### Post by Hippytaff on 2010-11-25
> **drewhops said:**
> I held down the Shift key while powering up and it still has the same screen, blinking cursor that will not accept text. How do I download a bootable image do a USB drive?

You can use unetbootin to use the iso you already have (if you have one) to make a liveUSB drive
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

or download one here - [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by drewhops on 2010-11-25
Thanks for responding to my post. I installed Ubuntu 10.04 to a USB drive and plugged it into the desktop. How do I boot the computer from the USB drive?

---

### Post by Hippytaff on 2010-11-25
You need to get into the bios...it is different for every pc but I have to press F8 straight after starting the pc...on your pc it might say change boot order at the bottom of the screen for a while, which will tell you which (usually F key you need to press)...you can also search your 'pc name bios' or 'your pc boot order'  in google which might return a link to a page which tells you how to change the boot order :-)

so you get into the bios and navigate to a menu to do with boot order, and change the usb option to the top

---

### Post by drewhops on 2010-11-25
Thank you for the tip. A google search returned F11 as the key to press during startup. Apparently there's something different about the Zotac motherboard in that it does not recognize the USB drive. I had the options of the installed hard drive, a booting agent for the Nvidia graphics card, and the CD/DVD drive. I guess I'll have to burn a CD and try again.

---

### Post by drewhops on 2010-11-25
OK. Burned 10.04LTS 64 bit LiveCD and am running it on the box with the broken bootloader. I'll move all of my files to an external hard drive so that, worst case, I can reinstall the operating system from the LiveCD. How should I proceed so that I can diagnose the boot issue and maintain the current system configuration?

---

### Post by drewhops on 2010-11-25
Just found out that I do not have the necessary permissions to backup those files on the hard drive. How can I access those files and/or reinstall the operating system without erasing them?

---

### Post by drewhops on 2010-11-25
Thanks for the help. I followed the very helpful instructions here [http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader) and everything works again. :)

---

### Post by Hippytaff on 2010-11-26
Excellent, glad you got it sorted - Remeber to mark the thread as solved so others who encounter the same issues as you can benefit from what you did to sort it :-)

---

