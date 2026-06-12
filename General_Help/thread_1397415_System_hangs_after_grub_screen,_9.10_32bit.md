---
title: "System hangs after grub screen, 9.10 32bit"
date: 2010-02-03
forum: General Help
---

### Post by beastrace91 on 2010-02-03
Howdy All,

So I just did a fresh install of 9.10 32bit on my media pc, booted right up the first couple of times however it choose to stop doing so for some reason. When it boots I see the words "Grub Loading" flash on the screen and then it just goes to a black screen with the white flashing line in the upper left hand corner...

I'm open to suggestions on how I can go about resolving this issue, the system was running well and I'm not sure what exactly changed... I just went to reboot it and it wouldn't come back online.

Also worth noting is that it is also failing to boot from a LiveCD for me, I get the screen where I select how I want to boot from the disc, I select "try Ubuntu with out any changes to my computer" and then after that it hangs again.

I'm fairly certain the hardware is good as it never had any issues like this on Windows 7 and I can still boot properly from a Windows based disc.

Regards,
~Jeff

---

### Post by beastrace91 on 2010-02-03
Bump/Update - 
Alrighty so here is the status: Pressing escape at "grub loading" yields nothing, the system just moves right along to the white flashing line on the black background.

I have a giant stack of Live discs sitting in my drawer and none of them boot in the system:

Linux Mint 8:
stdin: error 0
/init: line 1: can't open /dev/sdc: No medium found...
Shadow passwords are now on.

Fedora 12:
ACPI: Expecting a [Reference] package element, found type 0
ata3: softreset failed (device not ready)

Sabayon 4.2:
Hangs at "initializing the kernel"

Knopix 5.3:
I get two tuxes in the upper left hand corner of the screen

The disc drive works however - I know this because my Vista 32bit disc loads right up on the sucker. What one earth could have happened to both cause my system to stop booting into Mint and no longer be able to boot off of a live cd at the same time? I am truly confused.

EDIT/Add:
Alrighty, so I dug an Ubuntu 9.04 alternate disc out of my distro pile and when I select "rescue a system" I get the following pile of errors on screen when it tries to load:

[IMG]http://i48.tinypic.com/21cavwk.jpg[/IMG]

Is it saying one of my hard discs is bad?...

Regards,
~Jeff

---

### Post by beastrace91 on 2010-02-03
Alrighty, at last I have pin-pointed my issue. Just not sure how to resolve it. All of the messages in the image I linked to above point to a hard drive issue... I recently inserted a new hard drive and formatted it from ntfs to ext4. I had not connected the issue occurring after this addition until now.

When I open the system up and dis-connect the second hard drive the system boots into the install operating system just fine... However I need the second drive (it is a 1.5tb disc I bought for storage purposes) What might be causing the issue and how can I resolve it?

EDIT: And lastly upon reattaching the drive the system now boots just fine as it did before... I've rebooted it twice now and it came right back online both times. I am truly confused at to what was causing/caused the issue. I am not used to these kind of random stability issues on my Linux based computers - normally they only break when the hardware goes out or I change something. If anyone has insight into what might have happened/what I did to fix it exactly please feel free to enlighten me.

~Jeff

---

