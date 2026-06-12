---
title: "Ubuntu doesn't start installation"
date: 2011-10-29
forum: General Help
---

### Post by Niggus on 2011-10-29
dear ubuntuforums,

i am having problems installing ubuntu.  i am and have been attempting at installing the latest version of ubuntu from my windows pc.

> 
manufacturer: acer
model: aspire 5336
processor: intel(r) celeron(r) cpu 900 2.20 ghz 2.19 ghz
ram: 3.00
system type: 64-bit operating system


i've already burned the os on a dvd and EVERYTHING went as planned because in fact i installed ubuntu on another computer, same cd, version, etc and i used it fine--actually i removed windows xp off of that computer and used ubuntu as the main os.

however on my laptop it wont do the same.  you see, when i put the disk in and restart, it shows the purple loading screen and then the screen just goes black...any suggestions?

edit: i must cut the power off of the lap top in order to reboot the computer and go back to windows.  if i choose ubuntu, it will do it again.

if anyone preparing to reply in regards to my problem and needs any other information not supplied in this thread, please do ask.

thanks, sincerely,


***[FONT="Comic Sans MS"]niggus[/FONT]***

---

### Post by mike555 on 2011-10-30
sounds like a graphics problem, what graphics card do you have in laptop ? 
  anyway try adding "nomodeset " to the boot , by clicking the shift key during grub and add it to line after quiet.

if that works and it starts be sure to install graphics driver .

---

