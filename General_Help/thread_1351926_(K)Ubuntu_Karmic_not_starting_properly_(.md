---
title: "(K)Ubuntu Karmic not starting properly ("
date: 2009-12-11
forum: General Help
---

### Post by Makistos on 2009-12-11
I have a very weird and serious looking problem with 64-bit (K)Ubuntu Karmic. Please note that I have a dual-boot machine with XP and XP has worked all through this.

It all started last week when KDE wouldn't start properly. If I chose gdm as the default manager, it would start and then I could switch over to KDE. 

What I got when I started KDE directly was something along the lines of "Ubuntu is now running in low-graphics mode" and "your keyboard, screen and mouse could not be detected, you have to configure them manually".

I then got my new video card (NVidia GTX250) and eager as I was I put that in. XP still booted ok, but now Ubuntu is even worse. 

I can't even start it in console! I get the same error as before, but if I try to go to console it gets stuck in "setting up console font and keymaps" and then nothing happens.

There is also "I/O resource piix4 smbus [0xb00-0xb07} conflicts with ACPI region SOR1 [0xb00 - 0xb0f] in the log shown prior to the boot getting stuck.

In the logs the only thing I could found was this warning three times (keyboard, mouse and... maybe screen, can't remember):

The XKEYBOARD keymap compiler (xkbcomp) reports: Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols. Ignoring extra symbols.

So I tried to boot with my Jaunty installation disk. In the "normal" mode ("Try Ubuntu without changing the system") I only get the mouse cursor on the screen. When I turned ACPI off and selected safe graphics mode, I got the brownish default background and the mouse cursor, but after twenty or thirty minutes of waiting, that was all I got.

Now I'm quite clueless. I'll try chapter 8.1 from [this page]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html") so I could at least see the rest of the logs (dmesg etc) but apart from that I'm quite clueless. What can it be that causes a-non start for Linux (even the installation CD that used to work) but still lets XP to start? I would have suspected a faulty hard-drive (since the systems are on different drives) but for the fact it doesn't even start from the CD.

EDIT: The old card was also from NVidia, 7600GT.

---

