---
title: "Hard-drive crash - repeat with error sign"
date: 2011-01-31
forum: General Help
---

### Post by jsacks on 2011-01-31
Hi can any help with this? This is the second time my hard-drive has been corrupted.  I am pretty newbie so need full instructions. thanks!
- jared

OS: Ubuntu 10.04
Laptop: Dell M1330 

Issue in December 2010:
My laptop running 10.04 will no longer boot.  The day before, it wouldn't mount my USB flash but I figured it was the flash that was not working.  But now when I boot I get this weird error which seems its unable to bood my hard-drive either.  Super worried that i'm gonna loose my data (good thing i backed it up before I left Cape Town a week ago but there's still some stuff i don't want to loose).  Anyways, here's what the screen says....its missing the top-bit because I can't figure out how to scroll up....


    [     1.690987] CR2: 0000000001bc0000
    [     1.695492] --- [ end trace bc60efd5eaab7b65 ]---
    Killed
    mount: mounting /dev on /root/dev failed: No such file or directory
    mount: mounting /sys on /root/sys failed: No such file or directory
    mount: mounting /proc on /root/proc failed: No such file or directory
    Target file system doesn't have /sbin/init.
    No init found. Try passing init= bootarg.

    BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
    Enter 'help' for a list of built-in commands.

    (initramfs) [     1.796220] usb 7-1: new full speed USB device using uhci_hcd and address 2
    [     1.968404] usb 7-1: configuration #1 chosen from  choice
    [     2.045395] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
    [     2.173494] usb 3-2.1: configuration #1 chosen from  choice
    [     2.249403] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
    [     2.379486] usb 3-2.2: configuration #1 chosen from  choice
    [     2.457414] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
    [     2.587497] usb 3-2.3: configuration #1 chosen from  choice
    [     2.652716] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc00020d71dc1]



After this, a friend suggested first try to boot from a usb or live CD.  This did not work because it went to the loading screen and got stuck loading seemingly forever. Then i removed the HD and tried it on another computer.  I loaded it into a cady and booted from the HD on another computer.  The result being that I received the same error code.  He said that my HD was corrupted.  He ended up suggesting I just buy a new HD b/c it was not worth the hassle to restore.  I lost about 30 hours of work that was not backed up but the new HD seemed to fix the problem

Current problem as of this morning:

All of a sudden today my computer was running slow so I decided to reboot.  When I rebooted, i received almost the same error sign as previously.  The only difference is the bit at the bottom in brackets (the actual numbers are slightly different:

old:

(initramfs) [     1.796220] usb 7-1: new full speed USB device using uhci_hcd and address 2
[     1.968404] usb 7-1: configuration #1 chosen from  choice
[     2.045395] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[     2.173494] usb 3-2.1: configuration #1 chosen from  choice
[     2.249403] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[     2.379486] usb 3-2.2: configuration #1 chosen from  choice
[     2.457414] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[     2.587497] usb 3-2.3: configuration #1 chosen from  choice
[     2.652716] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc00020d71dc1]

new:
(initramfs) [     1.880261] usb 7-1: new full speed USB device using uhci_hcd and address 2
[     2.056397] usb 7-1: configuration #1 chosen from  choice
[     2.133389] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[     2.261484] usb 3-2.1: configuration #1 chosen from  choice
[     2.337390] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[     2.467482] usb 3-2.2: configuration #1 chosen from  choice
[     2.545402] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[     2.661739] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc00020d71dc1]
[     2.675486] usb 3-2.3: configuration #1 chosen from  choice


Otherwise its the same problem as previously.  But the issue is this:
1) This can't keep happening.  It seems unlikely to me that two different HD could fail out of nowhere.  So there must be something causing this issue
2) I need to recover the current info on my HD because I can't loose this work.  Theres about 100 hrs of work on there.

Let me know if you can help.

---

