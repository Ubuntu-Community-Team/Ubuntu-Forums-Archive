---
title: "prefix not set problem"
date: 2011-07-23
forum: General Help
---

### Post by ayushgoyal09 on 2011-07-23
I installed Ubuntu 11.04 alongside Windows XP using the Wubi installer that i downloaded from ubuntu website. It worked fine for a month but today when i started my laptop and choose Ubuntu....it gave me error
[U][B]
NTFS5 : prefix is not set[/B][/U]

i have installed Ubuntu in D drive while windows XP is in C.
I am new to Linux/Ubuntu.....please help me sort out this problem. Any kind of help will be appreciated.

---

### Post by bcbc on 2011-07-23
That error message is always shown on 11.04 wubi installs. It doesn't indicate a problem. So there is some other problem.

1. Have you been manually shutting down the computer?
2. Does the D:\ubuntu\disks directory exist and is there a root.disk and a swap.disk in there?

---

### Post by ayushgoyal09 on 2011-07-23
1. Yes, I have been shutting down my lappy properly.
2. root.disk and swap.disk are present

---

### Post by bcbc on 2011-07-24
So... after the error message is displayed, what happens? A grub prompt? Any other symptoms?

---

### Post by ayushgoyal09 on 2011-07-24
yes i do get the grub prompt. I dont know what to do henceforth....!!

---

### Post by bcbc on 2011-07-24
Probably the easiest way to resolve this is for you to create an Ubuntu CD or USB and boot it in "live cd" mode - in other words, boot from the CD or USB and select "Try it" without installing. Then download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here.

Also refer to [this]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") in the Wubi guide, which refers to "fsck"ing your root.disk (do this if it cannot be mounted)

You might also want to take a backup of the root.disk if you have unsaved data on it (do this prior to running fsck). Or try to access it from Windows to recover it e.g. with [this]("http://ext2read.blogspot.com/") or other tools mentioned in the wubi guide.

I'm going offline but I'll check the results of your bootinfoscript tomorrow.

---

### Post by ayushgoyal09 on 2011-07-25
hey, today i tried to boot Ubuntu and guess what, I got booted successfully as usual. i have no idea what is it with Ubuntu. Thanks anyways, really appreciate your help.

---

### Post by bcbc on 2011-07-25
Interesting... glad it's working again... a little strange though. Maybe there was a little ntfs corruption ?!

PS if Wubi appears to hang, use [this guide]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen") to safely reboot. Don't power the machine off as this can result in corruption.

---

