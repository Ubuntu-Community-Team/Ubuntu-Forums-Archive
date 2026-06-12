---
title: "Problems during boot"
date: 2011-01-01
forum: General Help
---

### Post by framiss on 2011-01-01
I got stuck configuring a new screen, bad luck i guess.
After changing

[SIZE=2]/etc/initramfs-tools/modules
/etc/modprobe.d/blacklist-framebuffer.conf
 /etc/default/grub
 /etc/grub.d/00_header

and updating
[/SIZE]```
update-grub2
update-initramfs -u
```The power went off so the rest of the settings could not be made so the next boot
made me a bit sad. The screen is now black during boot but seems to flash just after the
usplash is finished and then it goes black again.

I booted the computer with a Live cd and changed everything back but i still have to
run

```
update-grub2
update-initramfs -u
```[SIZE=2]

and that i cannot do from the Live cd.

Any suggestions?
[/SIZE]

---

### Post by happyhamster on 2011-01-01
Boot into a live session, and mount your harddrive onto the live filesystem. Make a note where it is mounted at. You can take a look with:
```

df

```
It's probably something ugly like /media/UUUUID-UUID-UUID-UUID-UUUUUUIIID
Now, remount it with the dev option:
```

sudo mount -o remount,dev /media/UUUUID-UUID-UUID-UUID-UUUUUUIIID

```
Chroot into the drive's filesystem:
```

sudo mount -t none /dev /media/UUUUID-UUID-UUID-UUID-UUUUUUIIID/dev -o bind
sudo chroot /media/UUUUID-UUID-UUID-UUID-UUUUUUIIID

```
At this point, you are root, and the hard-drive's filesystem will be used as the session's filesystem. First run:
```

mount /proc
mount /sys

```
Now all required special filesystems should be mounted as well (/dev, /proc and /sys). Next, try fixing the system:
```

update-initramfs -u
update-grub2

```
Reboot. (Instead of update-initramfs -u, you might have to update all existing ones instead: update-initramfs -c -k all)

Good luck.

---

### Post by framiss on 2011-01-01
Looks resonable, i was thinking about something like that.
Did not exactly know how though.

I will give it a try as soon as i get there.

Thanks!

---

### Post by framiss on 2011-01-02
OK! I got the time to test it out and it worked just fine!

I'll have to save this rescue just in case of emergency some other time!

Many thanks!

Happy new year by the way!

---

