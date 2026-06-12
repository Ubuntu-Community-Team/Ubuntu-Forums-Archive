---
title: "Shell Emulator"
date: 2010-01-11
forum: General Help
---

### Post by lrcaballero on 2010-01-11
Hi everyone,

I am currently taking Unix System Fundamentals at school and I will like to know if there is a Shell Emulator for Linux that I can install so that I can practice at home. I am currently running Karmic Koala 9.10. Thank you in advance for your help.

Luis

---

### Post by dcstar on 2010-01-12
> **lrcaballero said:**
> Hi everyone,

I am currently taking Unix System Fundamentals at school and I will like to know if there is a Shell Emulator for Linux that I can install so that I can practice at home. I am currently running Karmic Koala 9.10. Thank you in advance for your help.

Luis

Ubuntu already has multiple shells built in or available for installation.

They are accessed by a terminal session (which is a shell).

---

### Post by lrcaballero on 2010-01-12
dcstar, thank you for your response! ;)this shells that are available in my current OS Karmic Koala, will let me pratice without affecting my current folder and directories???

Thank you

Luis

---

### Post by wirelessmonkey on 2010-01-12
Answering for dcstar, yes, the primary shell is Bash, you can also use KSH, ZSH, CSH, TCSH and more.

---

### Post by mihamil on 2010-01-13
Using the terminal in your current installation can affect your directories, files, etc.  Meaning if you are practicing with commands you can potentially break things.  When I was in my Linux Systems Administration class we used live cds.  I would suggest you do the same.  While not impossible to break things on your installed OS, it is much less likely to do so from a live cd.  And if you run a command that stops the Live session from working you can simply reboot and everything is good.  

Remember, it IS STILL POSSIBLE to break something on your current local installation with a live cd.  Be especially careful if any commands are referencing device identifiers such as "/dev/sda1". These commands could potentially point to your hard drive where your installation lies and depending on the command can format,delete,etc information from that drive.

MH

---

