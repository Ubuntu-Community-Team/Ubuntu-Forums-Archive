---
title: "I have a problem with fsck at boot"
date: 2009-10-09
forum: General Help
---

### Post by viking_maniac on 2009-10-09
Today I encrypted a whole partition (device) in TrueCrypt. But then after, every boot is interrupted by fsck that complains about an error on my file system. My other partitions (devices) are just fine and reports as *clean* by fsck, except for the encrypted partition that fsck doesn't seem to like very much.

This is very annoying, so I hope there's a way to opt out the encrypted device from checking with fsck; or any other way to make Jaunty boot as normal[COLOR=#000000][FONT=Verdana,Arial,Tahoma].

?[/FONT][/COLOR]

---

### Post by mikewhatever on 2009-10-09
You'll have to change a setting in /etc/fstab.

Backup first: sudo cp /etc/fstab /etc/fstab-backup

Now, open for editing: gksudo gedit /etc/fstab

You'll see lines similar to this:
```
UUID=c199f694-ac9c-422c-ae6d-86f442d12c0f none         swap sw              0       0

```

What determines if the device gets checked is the very last number, 0 in my case. Set it to 0 too.

---

### Post by viking_maniac on 2009-10-10
> **mikewhatever said:**
> You'll have to change a setting in /etc/fstab.

Backup first: sudo cp /etc/fstab /etc/fstab-backup

Now, open for editing: gksudo gedit /etc/fstab

You'll see lines similar to this:
```
UUID=c199f694-ac9c-422c-ae6d-86f442d12c0f none         swap sw              0       0

```What determines if the device gets checked is the very last number, 0 in my case. Set it to 0 too.

That did the trick! Thank you, mikewhatever!

---

