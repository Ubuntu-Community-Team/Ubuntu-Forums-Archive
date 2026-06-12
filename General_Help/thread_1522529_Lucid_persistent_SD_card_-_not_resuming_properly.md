---
title: "Lucid persistent SD card - not resuming properly"
date: 2010-07-02
forum: General Help
---

### Post by maestrobwh1 on 2010-07-02
Odd issue - I have an ASUS 1201T eee with an SD reader

I set up an SD card with two partitions, one for the system and one casper-rw (using grub2 to boot the iso)

It boots and works well except when I go to resume from suspend, I get errors such that the filesystem is no longer mounted.  The desktop comes up and things that are functional give errors that the home directory is not writable.  Where/what can I look at? 

**[edit] If the same SD card is inserted into an external usb reader, it resumes correctly.**

[B][edit2] Installed the uswsusp utility, moved /usr/sbin/pm-suspend /usr/sbin/pm-suspend.bak
I then created a new pm-suspend executable with simply #!/bin/bash at the top and s2ram -f as a second line.  It isn't "pretty" but it works.  It is just my persistent-usb inserted into the particular card reader in this machine.  I would not say this is solved... this is a somewhat ugly workaround.[/B]

---

