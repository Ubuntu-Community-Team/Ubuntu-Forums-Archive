---
title: "Ubuntu freezes while booting up"
date: 2011-10-01
forum: General Help
---

### Post by Chamwiz on 2011-10-01
I have Ubuntu 11.04 running on a sony VGN-FZ240E.  Everything has worked great with this PC while running Ubuntu, until last night.  I was using my PC yesterday, and all was well.  Until, I packed it, drove home from school.  I was doing some work on my desktop because my mobo had died.  When to turn the laptop on to google something, when it didn't fully boot.

What happens is when I press the power button, I get the bios load screen.  Then the purple Ubuntu screen (not the load screen, just a flash of a purple screen).  The computer then goes to a black screen. (Note: the screen is still on, but just solid black) I can do only one thing while it is like this.  If I simply press the power button once, then the computer will go to the Ubuntu shutdown load screen, and shut down.  I'm at a complete loss as to what is wrong with this.

PC Specs:
Core 2 T7250 (2GHz)
2GB RAM
250GB HHD
Integrated CD/DVD Drive
Integrated Wireless N
Intel Moblie Graphics Media Accelerator X3100

---

### Post by realstarman on 2011-10-14
Do any of the recovery mode options work?
I mean booting in recovery mode, checking whether just the root shell works, boot into file system check, etc.
I would do the following:
- boot in recovery mode
- then check whether the shell works 
- repair broken packages
- clean
- boot into file system check
- see whether it works again
- if it doesn't, try some of the boot options such as acpi=off

---

