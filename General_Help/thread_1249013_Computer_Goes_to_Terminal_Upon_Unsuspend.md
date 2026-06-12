---
title: "Computer Goes to Terminal Upon Unsuspend"
date: 2009-08-24
forum: General Help
---

### Post by Joseph Schwenker on 2009-08-24
Hi everyone!  I have been having a problem with Ubuntu's suspend command.  My computer is in a small room, and so, I would always put my computer on standby so my room would not become a furnace.  When I click on the suspend command in Ubuntu 9.04, my computer goes into suspend mode just fine, but when I press my computer's power button to unsuspend, my computer and monitor become active again, but my screen just has a blinking terminal.  When I try to type into the terminal, no text appears.  Could someone please help me with this?  Right now, the only way to return to Ubuntu is to manually restart my computer.  Thanks in advance!

---

### Post by Joseph Schwenker on 2009-08-31
Why is no one answering my question???:confused:

---

### Post by SoftwareExplorer on 2009-08-31
Suspend might not be working properly. But try this: Ctrl + Alt + <function key>     In place of <functionkey> try F7, F8, F9 and see if you can get to a login screen.

---

### Post by Joseph Schwenker on 2009-09-01
> **SoftwareExplorer said:**
> Suspend might not be working properly. But try this: Ctrl + Alt + <function key>     In place of <functionkey> try F7, F8, F9 and see if you can get to a login screen.

I just tried what you said.  First, I pressed ctrl+alt+F7.  Nothing happened.  Next, I pressed ctrl+alt+F8.  My computer went to a terminal that had a whole bunch of text on it.  I had to reboot my computer.  Next, I pressed ctrl+alt+F9, which brought my computer to a giant, blank terminal.  I then discovered that I could switch back and forth between the blank terminal (F9), the text terminal (F8), and my desktop (F7).  I put my computer into suspend mode, then unsuspended it, and my computer was brought to a big blinking blank terminal.  I pressed ctrl+alt+F8, and nothing happened.  Nothing happened for ctrl+alt+F7, either.

---

### Post by SoftwareExplorer on 2009-09-01
Definitely sounds like suspend isn't working. You could file a bug if you feel comfortable doing that. Does hibernate work? Would it fit your needs? Also, suspend might be fixable, it's just that I wouldn't know how to.

---

### Post by Joseph Schwenker on 2009-09-09
> **SoftwareExplorer said:**
> Definitely sounds like suspend isn't working. You could file a bug if you feel comfortable doing that. Does hibernate work? Would it fit your needs? Also, suspend might be fixable, it's just that I wouldn't know how to.

Thanks for the reply.  Hibernate does not work either.  Where can I file a bug report?  I remember that this problem has been existent even before I used Ubuntu as my primary operating system.

---

### Post by SoftwareExplorer on 2009-09-09
You can file bugs at bugs.launchpad.net. If you need help, I would recommend a new thread that links to this one. that way you will get more responses (hopefully).

---

### Post by Joseph Schwenker on 2009-10-08
> **SoftwareExplorer said:**
> You can file bugs at bugs.launchpad.net. If you need help, I would recommend a new thread that links to this one. that way you will get more responses (hopefully).

Yeah, I might need a bit of help with this.  Thanks!

---

### Post by Joseph Schwenker on 2009-10-12
Bump

---

### Post by P4man on 2009-10-12
can you give some details what sort of computer it is?

Also, control + alt + F7 (/8/9) bring you back to the gui if all is right, but try control alt F1 or F2, and let us know if you get a terminal there or not.

BTW, not really a solution to your problem, but rather than just doing a hard power down, you could try the magic "reisub" to do at least a neat shut down if the resume fails -> less chance of corrupting your filesystem. Press and hold Alt and "SysRq" key (usually same key as printscreen). While holding those two, press R, then E, then I .. etc, R-E-I-S-U-B. Allow a few seconds between each keypress. It will (probably) power your machine down and restart it if the kernel is still responding. more info here:
[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

---

### Post by SoftwareExplorer on 2009-10-12
I would recommend starting a new thread asking for help filing the bug if you need it, filing a bug on suspend/resume failures is not something I've done before and someone with more experience in that area is more likely to see it if you start a new thread.

---

### Post by Joseph Schwenker on 2009-10-17
> **P4man said:**
> can you give some details what sort of computer it is?

Also, control + alt + F7 (/8/9) bring you back to the gui if all is right, but try control alt F1 or F2, and let us know if you get a terminal there or not.

BTW, not really a solution to your problem, but rather than just doing a hard power down, you could try the magic "reisub" to do at least a neat shut down if the resume fails -> less chance of corrupting your filesystem. Press and hold Alt and "SysRq" key (usually same key as printscreen). While holding those two, press R, then E, then I .. etc, R-E-I-S-U-B. Allow a few seconds between each keypress. It will (probably) power your machine down and restart it if the kernel is still responding. more info here:
[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

My computer is an eMachines T5212 with 2 GB of RAM, and the amazing nVidia GeForce 8800 GT with 512 MB of Graphical Memory.  When I press control alt f1, I get a terminal (yay for UNIX!), and I get the same for F2.  I am able to type and log into both terminals.  Thanks for your reply.

---

### Post by SoftwareExplorer on 2009-10-19
> **Joseph Schwenker said:**
> My computer is an eMachines T5212 with 2 GB of RAM, and the amazing nVidia GeForce 8800 GT with 512 MB of Graphical Memory.  When I press control alt f1, I get a terminal (yay for UNIX!), and I get the same for F2.  I am able to type and log into both terminals.  Thanks for your reply.

From there you could run 'sudo /etc/init.d/gdm restart' and see if it gets you a login, but that defeats the purpose of suspend over shutdown.

---

### Post by P4man on 2009-10-20
> **Joseph Schwenker said:**
> My computer is an eMachines T5212 with 2 GB of RAM, and the amazing nVidia GeForce 8800 GT with 512 MB of Graphical Memory.  When I press control alt f1, I get a terminal (yay for UNIX!), and I get the same for F2.  I am able to type and log into both terminals.  Thanks for your reply.

So it looks like there is a problem reinitializing the videocard. , But does control alt F7 (or 8 or 9) get you back to a gui or not ?

---

### Post by Joseph Schwenker on 2009-10-27
> **P4man said:**
> So it looks like there is a problem reinitializing the videocard. , But does control alt F7 (or 8 or 9) get you back to a gui or not ?

Yes, Control alt F7 returns me to GNOME.

---

### Post by Joseph Schwenker on 2009-10-29
Oh, DARN!  The problem still persists in Ubuntu 9.10!  Ah, but Ubuntu 9.10 is wonderful, anyway.

---

### Post by P4man on 2009-10-30
Have a look in your bios, there might be an option to reinitialize the videocard on resume.

---

