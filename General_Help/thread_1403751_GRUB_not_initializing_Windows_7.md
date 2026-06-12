---
title: "GRUB not initializing Windows 7"
date: 2010-02-10
forum: General Help
---

### Post by Palartzski on 2010-02-10
I am having a very serious problem! GRUB won't allow me to start up windows 7. Each time I select it from the prompt, I am given a blank screen with only the cursor blinking and mocking me. Ubuntu works perfectly fine, but when I try to mount the windows 7 volume, it tells me that it is unable
to mount the location because of an input/output error. I havnt done anything to make me believe I have caused this abd I am in complete shock that this has even happened. Both operating systems were running completely fine and then suddenly, windows won't boot up. ANY HELP would be greatly appreciated! Please and thank you!

---

### Post by Palartzski on 2010-02-10
i should also add that when i select windows 7 from the GRUB prompt, the light for my hdd stops blinking. before any of this happened, i just recently finished completely reinstalling windows 7 and ubuntu. this involved a really nasty and long process, and i had to completely clean out my hdd before i reinstalled either OS. this same situation had occurred also when both OS's were running fine. all I had to do was restart my PC, select windows 7 from the prompt again, and it booted up without a problem.
 
 all of this is making me wonder whether this is just simply both OS's not liking each other (most likely something about the file systems) or could it be something more serious and be a hardware issue and i would need to replace my hdd? what would be the best way for me to determine whether this is a hardware issue? remember, i am not able to access windows at all whatsoever. if its a software issue, is there any way i could do something with GRUB to be able to boot up windows again? if not, is my only option left just to reinstall both OS's?
 
all of this really makes me wonder whether it's really worth having both windows and ubuntu installed on a single hdd. do most people just install one and then virtualize the other? maybe do a wubi install? i know that this may be a very lengthy post, but just one more aspect about all of this is making me wonder about something. if the hdd doesnt seem to lock up when i run ubuntu, only windows, then would this really be a hardware problem? 
 
if you cant tell, im very..........aggravated by all of this. i have spent countless amounts of hours cleaning out my hdd, backing up all of my data, reinstalling both OS's and getting everything set back to the way it was before, only to find out it was gonna backfire on me all over again. again, any help would be immensely appreciated!!

---

### Post by john newbuntu on 2010-02-11
I would try scanning my disks for any errors.  The software will generally be available as a free download from the HDD manufacturer.  The I/O error tells me that there is a hardward (possibly disk) problem.

Also see if you run the advanced boot option and repair your boot sector: [http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

---

