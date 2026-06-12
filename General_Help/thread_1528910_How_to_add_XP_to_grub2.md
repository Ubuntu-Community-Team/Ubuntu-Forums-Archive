---
title: "How to add XP to grub2?"
date: 2010-07-11
forum: General Help
---

### Post by Ninamori on 2010-07-11
Heres what I got going:

hd0,0 = Ubuntu 10.4
hd1,0 = Windows XP Pro

I installed Ubuntu first, then XP - however my system only boots into Ubuntu on startup, and there is no grub menu that shows up. Even though I installed XP after (albiet on another drive) Ubuntu boot wasnt modified.

My question is, what strings should I add to the grub.cfg file found in root to add Windows XP as an option in grub menu?

Hope someone can help, this has been getting on my nerves all day! Thanks in advance.

---

### Post by oldfred on 2010-07-11
When you has hd0,0 that is grub legacy numbering of partitions (starts at 0) Grub2 starts partitions at 1 so sda1 is (hd0,1)

If you have grub2 & this almost always works:
sudo update-grub

With grub legacy it often does not find other installs, you can try the same.
sudo update-grub

But we often had to manually add windows stanzas to grub legacy's menu.lst.

---

### Post by Ninamori on 2010-07-11
Thanks for the reply man, I ran sudo update-grub and it did add it to the grub2 menu list, however I get an error on a black screen when choosing XP that:

Error: No such device on xxxxxxxx
Error: No such partition

So close... any other ideas mate? :)

---

### Post by Ninamori on 2010-07-11
Just thought I'd post what sudo update-grub give out to grub.cfg:

```
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set e22c4fb52c4f838f
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

---

### Post by Ninamori on 2010-07-11
Tried manually typing this in at the command-line (pressing c at grub menu)

```
insmod ntfs
set root='(hd1,1)'
drivemap -s (hd0) ${root}
chainloader +1
```

But returns the error "error: no such partition." just as if I choose the XP menu item. Why wont it see the partition?

Man i dunno what to do, what else can I try? :o

---

### Post by Ninamori on 2010-07-11
To add further, the second hdd that windows is installled on (sdb1) has partitioning as master boot record, and the ubuntu partition (sda1) is GUID table, could this be the problem?

Still hope someone out there can help, I really wana use ubuntu but if this goes on I aint got the time to mess. :(

---

### Post by oldfred on 2010-07-11
I have gpt on one drive and windows XP on another without a problem.
Do you have the windows boot loader in its drive and have you tried directly booting it from BIOS?

Post this to see if anything looks out of place.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Ninamori on 2010-07-11
Yeah bootloader is in drive, if I boot with sdb it will run windows like normal, no problems, vice versa for sda for ubuntu.

its not practical to keep going into the boot priority manager each time I need to switch though.

I'll try the other stuff you suggested asap, thanks.

---

### Post by oldfred on 2010-07-11
I would try editing the boot entry from the grub menu. At the menu type e to get edit mode.

Try alternative drive numbers, 0, 1, 2 
Try totally removing the search line.

The search line is supposed to override the set root with UUID if set root is not correct. See next paragraph on why drive number may change.
I found on my system the boot drive is drive 0 even when I boot sdc and then to chainboot to sda I have to use hd1 not hd0 that I would think sda would be. So grub renumbers drives depending on which is booted.

---

### Post by Ninamori on 2010-07-12
Cheers guys, managed to get it working, the problem was the drive that Ubuntu was installed on was formatted as GUID, whereas the Win Xp drive was formatted as MBR, so I reformatted and installed Ubuntu onto a MBR drive, now the GRUB bootloader will load both OS, and can each read eachothers partitions.

Man, feel so stupid for not noticing that, I even mentioned it in an earlier post, I knew 32bit windows doesnt support GUID but I didn't think it would matter.

One big fat DOH. :P

---

### Post by oldfred on 2010-07-12
It turns out gpt is a problem. My gpt drive sdb boots ok but I went back to try booting my other Ubuntu installs in sdc and my windows in sda from the grub2 in sdb and all of them give the same errors.

I will file a bug report since you confirmed the problem I now have even though you went back to BIOS partitions.

---

### Post by oldfred on 2010-07-12
I filed bug report & already have a solution. They have it in Maverick.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

at:
grub> insmod part_msdos

---

