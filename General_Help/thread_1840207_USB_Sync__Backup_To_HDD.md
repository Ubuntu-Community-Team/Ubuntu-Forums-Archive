---
title: "USB Sync / Backup To HDD"
date: 2011-09-07
forum: General Help
---

### Post by 337Manni on 2011-09-07
Hi All.

I'm looking for a program for syncing my USB Flash Drive to a folder on my HDD.

Basically I use my USB Pen Drive to carry around important work files. I would like to setup a program so that when I plug in my Pen Drive in it syncs to a predefined folder without any user input.

This would stop me from having to remember to back it up. After a recent HDD failure it has brought home to me how important backups are. I had sum but lost the most recent stuff due to me not backing up in a while (forgetting grrr ](*,))

Thanks for reading,

Lee.

---

### Post by tredegar on 2011-09-07
[http://www.kevinblake.co.uk/auto-running-commands-when-plugging-in-usb-drives-with-udev-in-linux/732/](http://www.kevinblake.co.uk/auto-running-commands-when-plugging-in-usb-drives-with-udev-in-linux/732/)

---

### Post by 337Manni on 2011-09-07
Hey, thanks.

I'm just following the link now.

Quick reply BTW!:D

---

### Post by 337Manni on 2011-09-07
Have you setup and used this yourself?

Could you walk me through the setup? I'm not used to the terminal, more of a GUI man at the mo coming from XP to Ubuntu.

I entered
udevadm info -a -p  $(udevadm info -q path -n /dev/sdc)

in the terminal as it said but couldn't see any line saying something similar to
ATTR{serial}=="312581808"

---

### Post by tredegar on 2011-09-07
> Have you setup and used this yourself?
Not this *exact* rule but otherwise **udev** works as expected.
> I entered
udevadm info -a -p $(udevadm info -q path -n /dev/sdc)

in the terminal as it said but couldn't see any line saying something similar to
ATTR{serial}=="312581808"

Are you sure that **/dev/sd[COLOR="Red"]c[/COLOR]** really is the device you are referencing ?

You might try```
udevadm info -a -p $(udevadm info -q path -n /dev/sd[COLOR="Red"]c[/COLOR] [COLOR="Blue"]| grep ATTR[/COLOR])

```
sd[COLOR="Red"]c[/COLOR] = adjust for your situation

The outputs of **mount** and **fdisk -l** might help you work out where partitions have been mounted automatically

---

