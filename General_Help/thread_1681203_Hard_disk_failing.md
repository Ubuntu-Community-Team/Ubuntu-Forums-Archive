---
title: "Hard disk failing?"
date: 2011-02-03
forum: General Help
---

### Post by werdigo49 on 2011-02-03
This is a Kubuntu question; sorry, but the forums there have been down all day.

After a month of being away, I booted my Kubuntu 10.10 system and it could not
read or write to my primary backup SATA disk, "disk-1" (a WD 250G disk). At first I could see the folder and file names, though some Dolphin entries simply had "?" for some file properties and files could not be copied to other disks nor could disk-1 be
written to. On later reboots the Dolphin panel for disk-1 stayed blank.

I booted my old Hardy system (Klikit), and it read and wrote to that partition
perfectly. (I rsync'd it to another data disk that both Klikit and Kubuntu
mounted and handled fine.)

In Kubuntu, Gparted doesn't even see disk-1, and the blue "Kubuntu" startup
screen flashes a message that "An error occurred mounting /media/disk-1. Press S
to skip or M for manual..." and then the bootup proceeds. MountManager shows
disk-1, but can't seem to actually mount it. In Dolphin, the two partitions on disk-1 are shown in the left panel, but clicking on either of them produces simply a blank pane.

Any suggestions? I figured the disk was failing, and maybe it is, but it works perfectly under
Klikit (based on Kubuntu 8.04).

---

