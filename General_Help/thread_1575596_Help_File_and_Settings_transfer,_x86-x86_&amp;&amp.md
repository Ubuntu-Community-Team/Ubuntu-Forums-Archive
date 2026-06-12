---
title: "Help: File and Settings transfer, x86-x86 &amp;&amp; x86-x64"
date: 2010-09-16
forum: General Help
---

### Post by v1ad on 2010-09-16
Okay i got a question on how i can transfer my files, programs, username, settings, and all. so it would mimic my install onto a different computer. passwords and all.

if there is a way to go from x86 to x64 or x86 to x86. i know about keeping the home partition separate but it still does not keep your programs in there. 

there where a few programs that where out there but i forgot about them and need help remembering.

---

### Post by Ocxic on 2010-09-16
Step 1: backup home folder / home on separate partition.
Step 2: Create a list of all installed packages using synaptic package manager.
Step 3: Format root partition and install Ubuntu 64-bit (don't format home partition!!).
Step 4: Re-Install all packages using list created with synaptic package manager.
Step 5: Reboot computer, and your done.

Backup your home folder anyway just in case!!

---

### Post by JBAlaska on 2010-09-16
I assume (Always dangerous for me:p) that you know how to move your data files and settings, and you just want to install the same programs in a computer with different architecture?

If so, just copy a list of all current packages to a file in you home directory:
```
sudo dpkg --get-selections > myPackages.new
```

Then restore them on the new computer:
```
sudo dpkg --set-selections < myPackages.new && sudo apt-get dselect-upgrade
```

[COLOR="Blue"]Edit: beat me to it Ocxic lol.[/COLOR]

---

### Post by v1ad on 2010-09-16
ahh the code is easier thanks every1 :], now if i open connect that hard drive through usb(usb adapter) it says i do not have access to the drive. is there a way i can connect it and access the home directory, even though its not booted off that drive. what happened is i had a hard drive in my laptop and i swapped it out to a SSD. 
i can't use clonezilla because i don't want to have windows on this SSD, and i can't copy a partition to a drive(a lot of extra hassle also) so i just went and installed fresh and want to copy it all over.

so now the question is, how can i access a restricted drive to copy my settings over without having to boot.

---

