---
title: "Reinstalation Failed - 10.10"
date: 2010-11-16
forum: General Help
---

### Post by pockets08 on 2010-11-16
Hi people. I recently installed Ubuntu and eveyrhtign worked fine but a few minor thigns here and there. however, i uninstalled it and Installed windows XP - but when i did that , none of my drivers worked. All my files were there - and even a backup folder with drivers. but none of the drivers setup.exe files woudl ruin. i believe it was an older version or windows xp i may have downloaded. I dont have the original OS discs for my laptop, so i had to try what i coudl find. anyway - I tried to go back to ubuntu. and it loads form the Drive, and just has the ubuntu loading screen. i left for 3 hours and still nothing. I cant install ubuntu with windows - it says an error has occured. Any suggestions?

---

### Post by Sven6210 on 2010-11-16
Stupid question:

Did you boot Ubuntu from USB stick or CD? And did you see the Windows XP Logo or even the Windows XP scree before you saw the Ubuntu screen?

---

### Post by pockets08 on 2010-11-17
Disc - 

and no logo seen, it boots straights into the disk drive to start Ubuntu. but it just sits on teh ubuntu loading page - it doesnt even go to the option to try demo or install. it just sits there with the ubuntu logo - loading up. For hours...lol and still nothing.

---

### Post by sikander3786 on 2010-11-17
Did you check the disc for defects? You need to press any key when the CD starts booting and then you'll see the options to try or install Ubuntu and also to check the disc for defects.

And to check the integrity of downloaded image, see here.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that doesn't work, please post your hardware specs. And before this, were you running 10.10 or some other version on the same machine?

---

### Post by pockets08 on 2010-11-17
mk, so when its booting, u mean before or after the ubuntu logo pops up? because both do nothing. I just get a beeping sound, before the ubuntu logo - and it ignores me and carries on. and after i see the ubuntu logo starts, i never get past the ubuntu logo... so, i never get the option, to try or install of check disc.

Also the intergrity thing - the sums come out the same on the MD5Sum

I was running 10.10 before this. and im nto 100% on my hardware specs, because i was given the computer  in its previous condition - when it DID work on ubuntu.

---

### Post by sikander3786 on 2010-11-17
As soon as the computer gets past Bios screen, keep on hitting any key until you see the boot options. That should come before the Ubuntu logo.

> As the CD boots, the user can gain access to the main page and its options by pressing any key. The language selection screen is displayed and will remain until a selection is made or the ESC key is pressed. 

You might also try some other options like acpi=off, noapic etc by pressing F6 on the same screen.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by pockets08 on 2010-11-17
Okay, got ahold of that menu - hit f6, hit the two selected configurations you suggested - still not booting. been about 10 minutes.

do you knwo anythign about windows XP pro? because there seems to be two of them on my cvomputer. one is the original the laptop came with, on a partition. and the other is the windows i tried to install after ubuntu. When i go into disk management, the only drive i see is C but there is another hardrive in the computer - nto listed. there is three listings in the disk management area, the only one active is C - the others have no volume name. and ones 100g free, and the other is only 2.. so i think somethign went wrong. is there anything i can do to maybe remove one, or reset something. 

if i wipe a hardisk - will the INTERNAL Drives, automatically install themselves with a new OS? - thats the issue im having mainly. I loved Ubuntu, but i had to switch because i need Adobe Flash Cs-4 for work purposes, and windows was my only shot. That i could figure out - in the needed time. If i can wipe the disk and all files on it (reformat) and reinstall with ubuntu - would my drivers be in tact? - if so why would they not appear on the new windows isntallation? Out of date windows xp? all my drivers worked for ubuntu. well - the important ones.

---

### Post by sikander3786 on 2010-11-17
Did you check the disc for defects?

You might need to try all those options one by one.

Can you list your hardware specs?

---

### Post by pockets08 on 2010-11-17
When i go to check for defects - it never loads up.

Where can i view a list of my specs - if i cant get into the computer ?

and do u knwo the answer to my previous question containing reformating?

---

### Post by sikander3786 on 2010-11-18
> When i go to check for defects - it never loads up.

Then the disc might be defected. You mentioned that you've checked the integrity of downloaded image and it is OK? If so, please burn a new disc and that at the lowest possible speed. I burn at 4X.

> if i wipe a hardisk - will the INTERNAL Drives, automatically install themselves with a new OS? - thats the issue im having mainly. I loved Ubuntu, but i had to switch because i need Adobe Flash Cs-4 for work purposes, and windows was my only shot. That i could figure out - in the needed time. If i can wipe the disk and all files on it (reformat) and reinstall with ubuntu - would my drivers be in tact? - if so why would they not appear on the new windows isntallation? Out of date windows xp? all my drivers worked for ubuntu. well - the important ones.

I couldn't understand what you want to accomplish here.

If you want to mount your existing partitions in Ubuntu, Yes they can be mounted.

I couldn't understand the drivers bit? Please explain a bit.

---

### Post by pockets08 on 2010-11-18
> **vince25 said:**
> One thing I got problem also is that when I download it. My internet come's in so slow in connecting in surfing some net.

What's went wrong?:popcorn:
Hey man - make a new thread - this is my question, a bit rude if u gt ur question answered in my thread, and i was stuck with none.

---

### Post by pockets08 on 2010-11-20
> **sikander3786 said:**
> Then the disc might be defected. You mentioned that you've checked the integrity of downloaded image and it is OK? If so, please burn a new disc and that at the lowest possible speed. I burn at 4X.



I couldn't understand what you want to accomplish here.

If you want to mount your existing partitions in Ubuntu, Yes they can be mounted.

I couldn't understand the drivers bit? Please explain a bit.


Okay. I want to take the hardrive. and clean it. with like - WipeDrive or something. So it would have no OS or anything on it or whatever. Then i'd want to mount the Ubuntu 10.10 as its ONLY OS.  but when i do that - reformat the hardrive. will it remove the drivers in the computer?

---

### Post by pockets08 on 2010-11-20
> **sikander3786 said:**
> Then the disc might be defected. You mentioned that you've checked the integrity of downloaded image and it is OK? If so, please burn a new disc and that at the lowest possible speed. I burn at 4X.



I couldn't understand what you want to accomplish here.

If you want to mount your existing partitions in Ubuntu, Yes they can be mounted.

I couldn't understand the drivers bit? Please explain a bit.


Okay. I want to take the hardrive. and clean it. with like - WipeDrive or something. So it would have no OS or anything on it or whatever. Then i'd want to mount the Ubuntu 10.10 as its ONLY OS.  but when i do that - reformat the hardrive. will it remove the drivers in the computer?

---

### Post by pockets08 on 2010-11-21
I use Infra recorder and Power ISO - both icantget lower than x10 speeds. or "maximum"

---

### Post by QLee on 2010-11-21
[QUOTE=pockets08]Okay. I want to take the hardrive. and clean it. with like - WipeDrive or something. So it would have no OS or anything on it or whatever. Then i'd want to mount the Ubuntu 10.10 as its ONLY OS.  but when i do that - reformat the hardrive. will it remove the drivers in the computer?[/QUOTE]

The "drivers" are part of the OS. In Windows they are called drivers, in GNU/Linux they are often called modules but it is not really incorrect to call them drivers, that is the function they serve, making a piece of hardware work. If you wipe everything on the hard drive, naturally all "drivers" are gone. They never existed in the "computer" at all.

It appears from your description that you want to "install" Ubuntu as the only OS (not "mount"). When you install Ubuntu it will install the "drivers" necessary for the kernel version of the OS. There may be one or two that will have to be installed separately (just the same as in Windows).

I hope this helps to clear the issue up for you.

---

### Post by sikander3786 on 2010-11-21
Removing any operating system will surely remove the drivers also. And in addition it would remove all the data you've on your HDD even personal :-)

But you might not need to install any extra drivers for 10.10 and even if you need, you can install them from the Ubuntu repositoires.

---

