---
title: "Bochs Fails to Start in Ubuntu 11.10"
date: 2012-06-02
forum: General Help
---

### Post by linux653 on 2012-06-02
Okay, so I am following JamesM's kernel development tutorial for UNIX. I try to run bochs and this is what I get:

[FONT=Courier New]========================================================================
                       Bochs x86 Emulator 2.4.6
             Build from CVS snapshot, on February 22, 2011
                   Compiled at Jul 15 2011, 15:10:30
========================================================================
00000000000i[     ] LTDL_LIBRARY_PATH not set. using compile time default '/usr/lib/bochs/plugins'
00000000000i[     ] BXSHARE not set. using compile time default '/usr/share/bochs'
00000000000i[     ] reading configuration from october-bochs.txt
00000000000p[     ] >>PANIC<< october-bochs.txt:3: vgaromimage directive malformed.
00000000000e[CTRL ] notify called, but no bxevent_callback function is registered
00000000000i[CTRL ] quit_sim called with exit code 1[/FONT]

Okay. Here is my october-bochs.txt file:

[FONT=Courier New]megs: 32
romimage: file=/usr/share/bochs/BIOS-bochs-legacy, address=0xf0000
vgaromimage: /usr/share/bochs/VGABIOS-elpin.2.40
floppya: 1_44=/dev/loop0, status=inserted
boot: a
log: bochsout.txt
mouse: enabled=0
clock: sync=realtime
cpu: ips=500000 [/FONT]

These are the files in my /usr/share/bochs directory:

[FONT=Courier New]BIOS-bochs-latest  BIOS-qemu-latest  VGABIOS-elpin-2.40
BIOS-bochs-legacy  keymaps         VGABIOS-lgpl-latest[/FONT]

Here is the sh file I used to start bochs:

[FONT=Courier New]#!/bin/bash

# run_bochs.sh
# mounts the correct loopback device, runs bochs, then unmounts.

sudo /sbin/losetup /dev/loop0 floppy.img
sudo bochs -f october-bochs.txt
sudo /sbin/losetup -d /dev/loop0 [/FONT]

Now, I realize it is a problem with the graphics VGA BIOS. I tried VGABIOS-lgpl-latest as well. I also tried the latest kernel. What is wrong? Also, I downloaded Bochs from the software center.

Should I compile it?

---

