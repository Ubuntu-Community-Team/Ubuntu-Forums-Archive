---
title: "Grub Customizer issue"
date: 2011-10-23
forum: General Help
---

### Post by kakashi_12 on 2011-10-23
I have this installed. The part that fails to work is changing colors and putting in a background. I click Save and also click Install to MBR. But the color stays white and black with no background.

---

### Post by kakashi_12 on 2011-10-27
:confused:

---

### Post by woodyg on 2011-10-28
I also have a problem with grub customizer... **since installing 11.10.** I have installed three linux OS, so I had a whole bunch of booting options, some of which I wanted to remove and some of which I just wanted to tidy up (e.g. Ubuntu 11.10 rather than linux-image-2.6.32-21-generic or whatever they may be called).

I used grub customizer to do this, some were removed (unticked) and some were re-labeled. I saved it, rebooted... and no change at all. I have done this several times, and it never works, so is it not working with 11.10 or do I have to do something else as well in order to make the changes take place? :confused:

---

### Post by kakashi_12 on 2011-10-28
I've done it on my laptop and it works just fine (with Lubuntu 11.10).
But on my Desktop, it does not work. Not the background anyway. Eveything else works for me (with Ubuntu 10 Lucid Lynx 64 bit version).

---

### Post by Rubi1200 on 2011-10-28
Take a look here and see if there are any pointers as to how to get this to work:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by drs305 on 2011-10-28
> **woodyg said:**
> I also have a problem with grub customizer... **since installing 11.10.** I have installed three linux OS, so I had a whole bunch of booting options, some of which I wanted to remove and some of which I just wanted to tidy up (e.g. Ubuntu 11.10 rather than linux-image-2.6.32-21-generic or whatever they may be called).

I used grub customizer to do this, some were removed (unticked) and some were re-labeled. I saved it, rebooted... and no change at all. I have done this several times, and it never works, so is it not working with 11.10 or do I have to do something else as well in order to make the changes take place? :confused:

One thing to check is *which* Grub is controlling your boot menu. If you have 3 OS's on your computer and they all use Grub 2, unless you take steps to prevent it the last one you install will control Grub - even if you set another one to be the default OS.

The easiest way to check is to look at the Grub menu the next time you boot. Unless you have reordered the menu, the top entry belongs to the OS controlling Grub.

The easiest way to get Grub controlled by the OS you want is to boot into that (Linux) OS, and then run:
```
sudo grub-install /dev/sdX
sudo update-grub
```
with X being the boot drive (a, b, etc).

This will cause the MBR to point to the Grub files of the currently-running OS.

---

### Post by kakashi_12 on 2011-10-28
> **drs305 said:**
> One thing to check is **[COLOR=Red]*which* Grub[/COLOR]** is controlling your boot menu. If you have 3 OS's on your computer and they all use Grub 2, unless you take steps to prevent it the last one you install will control Grub - even if you set another one to be the default OS.

  
Huh? Which? So you're saying if it's GRUB 1 or GRUB 2? I thought there could only be one boot loader in place.

---

### Post by kakashi_12 on 2011-10-28
> **drs305 said:**
> One thing to check is **[COLOR=Red]*which* Grub[/COLOR]** is controlling your boot menu. If you have 3 OS's on your computer and they all use Grub 2, unless you take steps to prevent it the last one you install will control Grub - even if you set another one to be the default OS.

  
Huh? Which? So you're saying if it's GRUB 1 or GRUB 2? I thought there could only be one boot loader in place at a time.

---

### Post by drs305 on 2011-10-28
> **kakashi_12 said:**
> Huh? Which? So you're saying if it's GRUB 1 or GRUB 2? I thought there could only be one boot loader in place.

Each OS by default will have its own Grub folders - i.e. each OS using Grub 2 will have its own configuration files and will use their settings to boot *if the MBR points to that folder*.

When you install a Linux OS that uses Grub 2, the installation normally will direct the MBR to point to that OS's Grub files and that OS will become the default selection in the boot process.

But say you select the third option in the menu and boot to another OS (example Mint). Now while in that OS (Mint) you make changes to its Grub files and run 'update-grub'. The Kubuntu Grub files for that OS are updated. However, when you reboot the MBR still uses the Ubuntu Grub files. Your changes won't be seen in the Grub menu. The reason is that you made the changes to the Mint files but the MBR is using the unchanged Ubuntu files to display the menu to boot.

Now let's say you have booted into Mint and run "sudo grub-install /dev/sda". When you execute this command while in Mint, the MBR is rewritten and will now look for Mint's Grub files. The next time you boot, it will use the Mint menu as defined by its Grub files.

---

### Post by kakashi_12 on 2011-10-28
That makes sense. Too bad that does not apply to me though. I only use one Linux Distro on this PC.
The other two OS's are Windows based.

---

### Post by drs305 on 2011-10-28
Well, in a case of Wubi you don't want to install Grub to the MBR with the "grub-install /dev/sdX" command or you will lose your Windows bootloader.

I wrote a guide on fonts and images in Grub 1.99. I believe the material would apply to Grub 2 in Wubi, although I haven't tried it. You could see if there is anything in the thread that might help you:
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by Bobhuber on 2011-10-28
> **kakashi_12 said:**
> I have this installed. The part that fails to work is changing colors and putting in a background. I click Save and also click Install to MBR. But the color stays white and black with no background.
Put your image file in /boot/grub/
sudo update-grub
You will now have a pretty background image.

---

### Post by kakashi_12 on 2011-10-28
> **drs305 said:**
> Well, in a case of Wubi you don't want to install Grub to the MBR with the "grub-install /dev/sdX" command or you will lose your Windows bootloader.

I wrote a guide on fonts and images in Grub 1.99. I believe the material would apply to Grub 2 in Wubi, although I haven't tried it. You could see if there is anything in the thread that might help you:
[http://ubuntuforums.org/showthread.php?t=1739412](http://ubuntuforums.org/showthread.php?t=1739412)

I don't use wubi either.

> **Bobhuber said:**
> Put your image file in /boot/grub/
sudo update-grub
You will now have a pretty background image.

That did not work, but good idea.

---

### Post by woodyg on 2011-11-03
> **woodyg said:**
> I also have a problem with grub customizer... **since installing 11.10.** I have installed three linux OS, so I had a whole bunch of booting options, some of which I wanted to remove and some of which I just wanted to tidy up (e.g. Ubuntu 11.10 rather than linux-image-2.6.32-21-generic or whatever they may be called).

I used grub customizer to do this, some were removed (unticked) and some were re-labeled. I saved it, rebooted... and no change at all. I have done this several times, and it never works, so is it not working with 11.10 or do I have to do something else as well in order to make the changes take place? :confused:

Strange as it may sound, it all works now. Ditched Ubuntu (for unrelated reasons) and made clean install of Xubuntu 11.10. Grub Customizer works. Don't know why...

---

### Post by foresthill on 2012-08-07
Does not work in 12.04, at least for me. I can't get rid of the program now, have lost all my previous boot entires (Windows 7, 12.04) and can only boot into 12.04, even after the program is supposedly completely uninstalled as per instructions.

I have been having some other strange problems with my browser that may or may not be related. Either I am a complete idiot or this is one of the worst pieces of software I have ever used. 

Or maybe it's just not compatible with 12.04. Whatever problems I thought I was having before are nothing compared to the havoc this thing has wreaked on my system. Considering a format and complete re-install. :(

---

### Post by drs305 on 2012-08-07
> **foresthill said:**
> Does not work in 12.04, at least for me. I can't get rid of the program now, have lost all my previous boot entires (Windows 7, 12.04) and can only boot into 12.04, even after the program is supposedly completely uninstalled as per instructions.

I have been having some other strange problems with my browser that may or may not be related. Either I am a complete idiot or this is one of the worst pieces of software I have ever used. 

Or maybe it's just not compatible with 12.04. Whatever problems I thought I was having before are nothing compared to the havoc this thing has wreaked on my system. Considering a format and complete re-install. :(


Sorry your system is not working. Your best chance for getting a proper solution would be to start your own thread and detail your specific problems. 

You might try installing Boot Repair (even if on the LiveCD). If it can't fix things, it can run a boot info script whose RESULTS.txt can tell us a lot about your system. (Link in my sig line)

---

### Post by foresthill on 2012-08-08
Ran Boot Repair. It errored out and did nothing but waste 15-20 minutes of my day trying unsuccessfully to purge and reinstall GRUB. I could have formatted and re-installed in that amount of time.

Are you sure these programs actually work in 12.04?

Sorry, but I have been here before, and messing with GRUB is one of the most horribly frustrating, confusing, and unrewarding things I have ever attempted to do in Linux. Gonna reformat and re-install. 

Thanks!

---

### Post by drs305 on 2012-08-08
> **foresthill said:**
> Ran Boot Repair. It errored out and did nothing but waste 15-20 minutes of my day trying unsuccessfully to purge and reinstall GRUB. I could have formatted and re-installed in that amount of time.

Are you sure these programs actually work in 12.04?

Sorry, but I have been here before, and messing with GRUB is one of the most horribly frustrating, confusing, and unrewarding things I have ever attempted to do in Linux. Gonna reformat and re-install. 

Thanks!

Yes, Boot Repair works in 12.04 for most users - of course if it doesn't work for you that doesn't matter. 

Usually if the recommended repair doesn't work we ask that you run the boot info script from within Boot Repair and provide the contents of the file it generates. This provides us with a great deal of information that may help us analyze what has happened. 

Sometimes reinstalling is a quicker solution than troubleshooting but we usually don't recommend that initially for a variety of reasons (including possible loss of data or configuration files, etc). We leave it to the user to decide when it's time to reinstall, although we may make recommendations.

It appears that you have reinstalled your OS by now, so I hope it went smoothly and everything is running well.

---

