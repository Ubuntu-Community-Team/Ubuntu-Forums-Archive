---
title: "Booting from Grub after partition move"
date: 2011-05-23
forum: General Help
---

### Post by carderne on 2011-05-23
I just moved mu Ubuntu install partition and am now having a bit of trouble booting from GRUB.

After selecting Ubuntu, I get a black commad-line kind of thing (I can type, but can't actually run commands) and then after a few seconds it carries on to the Ubuntu desktop...

It's not the hugest problem in the world but I'd like to fix it if I can... I've reinstalled grub and run update-grub but that didn't change it. Any ideas?

I assume it's something to do with GRUB, not recognising where the beginning of the partition is any more, is there some way that I can manually force it to use the new position? Or would the reinstall/update-grub have done that already?

---

### Post by ratcheer on 2011-05-23
If you moved the partition, the UUID almost certainly changed. In this case, your file system is not being mounted, thus it cannot be booted from.

 If you cannot boot at all, you may need to boot to a live cd and chroot to your system. Once you get into your system, run "sudo blkid" to find the current UUID of your partition.

Edit /etc/fstab. If the UUID found above differs, that is the problem. Edit fstab to specify the current uuid found above.

If the UUID matches, this is not your problem and you need more help.

Then, to be safe, you may need to grub-install and update-grub, again.

Tim

---

### Post by carderne on 2011-05-23
The UUID from blkid matches /etc/fstab and the one in /boot/grub/grub.cfg...

So I'm getting into Ubuntu fine, it just takes a bit longer and gives me this weird CLI type thing for a few seconds first...

---

### Post by ratcheer on 2011-05-23
Ok. Well, at least that is not messed up.

Tim

---

### Post by dragonfly41 on 2011-05-23
> 
After selecting Ubuntu, I get a black commad-line kind of thing (I can  type, but can't actually run commands) and then after a few seconds it  carries on to the Ubuntu desktop...

It's not the hugest problem in the world ...

I'm seeing that same quirk on one of two separate dual boot installations.

The black screen with blinking cursor (tty style) is seen for a couple of minutes .. then into ubuntu splash.

It is an annoyance.   Don't know where to look to speed up the boot process. fstab shows correct UUID's for two ext4 partitions.

---

### Post by carderne on 2011-05-26
bump...

---

