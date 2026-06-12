---
title: "Usb, umount, unplug and plug again"
date: 2011-05-02
forum: General Help
---

### Post by vcrpcant on 2011-05-02
Hi,

When I insert an usb pendrive, it mounts ok and the icon appears on the desktop.
Then I umount it, ok again.
But, when I want to mount it a second time, I have to unplug it and plug it again.

This also happens with an 2.5" external usb drive I have and is very annoying :(

However, this doesn't happen when I mount and umount several times in a row a second sata hard drive I keep only for some data.

Is there a workaround?..

---

### Post by vcrpcant on 2011-05-03
mini-bump..

---

### Post by vcrpcant on 2011-05-05
bump...

---

### Post by vcrpcant on 2011-05-06
Well, I finally managed to work around this issue and I share my thoughts hopping they will be useful for someone else facing this issue.
Feel free to make positive critics :)

It's seems to be a bug regarding the new usb3 drives and the way ubuntu deals with it, but I'm only guessing; just google: ubuntu bug usb3 and choose at will.
This doesn't mean ubuntu don't work with usb3, as you can see below, I think it's just a kind of gui bug, but I'm a newbye :)

My way of dealing with this was adding a launcher to panel, then choosing "application in terminal" and pasting this command:

sudo umount /dev/mapper/udisks-luks-[your disk uuid here] && sudo cryptsetup luksClose /dev/mapper/udisks-luks-udisks-luks-[your disk uuid here]

This way, the 2.5" usb drive is unmounted and locked up.
Notice that the second command (after the "&&") is only needed if you want to LUKS lock the drive, meaning you'll have to insert the password when trying to access it again; if you only want to unmount it, use only the first command, but your data in that drive will be available to anyone using your computer while not locked up again.

This way, after unmounting and locking, the drive keeps visible on the menu "Places" (I'm using Gnome).
If not using this, the computer would have to restart, because unplugging and plugging it again won't work. And that's the reason why I think the right-click menu in the usb drive icon, besides "safely remove drive", should have also "umount" (which has not; only for sata hard drives, not usb) and after that, "LUKS lock" or something similar.

---

