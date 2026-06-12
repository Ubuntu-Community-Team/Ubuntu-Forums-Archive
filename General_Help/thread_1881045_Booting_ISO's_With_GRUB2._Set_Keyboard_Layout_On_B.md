---
title: "Booting ISO's With GRUB2. Set Keyboard Layout On Boot Up?"
date: 2011-11-14
forum: General Help
---

### Post by dniMretsaM on 2011-11-14
Ok, so I have a USB stick with some ISO's on it and I would like to have it set the keyboard layout to Dvorak (US English) on boot up. I've googled (for literally over an hour) and I've tried lots of different combinations of [FONT=Courier New]keyboard-layout=[/FONT] and [FONT=Courier New]keyboard-variant=[/FONT] but I haven't gotten anything to work. Any help would be appreciated.

Example menu entry:
```
menuentry "Ubuntu 11.10" {
 loopback loop /ubuntu-oneiric.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-oneiric.iso noeject noprompt splash  --
 initrd (loop)/casper/initrd.lz
}
```

---

### Post by oldfred on 2011-11-14
It looks like a bug.
[FONT=Arial]
[/FONT]                                                       **[FONT=Arial][SIZE=1]Grub doesn't recognize alternative keyboard layouts[/SIZE][/FONT]**

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/782199](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/782199)

---

### Post by dniMretsaM on 2011-11-14
> **oldfred said:**
> It looks like a bug.
[FONT=Arial]
[/FONT]                                                       **[FONT=Arial][SIZE=1]Grub doesn't recognize alternative keyboard layouts[/SIZE][/FONT]**

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/782199](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/782199)

As far as I know, that bug only affects GRUB itself (i.e. the rescue prompt, editing menu entries, etc.). Not what GRUB is booting. Could be wrong though.

---

### Post by dniMretsaM on 2011-11-15
Bump.

---

### Post by dniMretsaM on 2011-11-17
Bump.

---

### Post by drs305 on 2011-11-17
I spent about half an hour trying to find a solution but came up empty. 

You might try asking the devs directly on IRC. They hang out on the #grub channel of Freenode or Ubuntu Server. Sometimes they will answer questions, sometimes not. Just depends on who is logged on and how busy they are when you ask.

---

### Post by dniMretsaM on 2011-11-17
> **drs305 said:**
> I spent about half an hour trying to find a solution but came up empty. 

You might try asking the devs directly on IRC. They hang out on the #grub channel of Freenode or Ubuntu Server. Sometimes they will answer questions, sometimes not. Just depends on who is logged on and how busy they are when you ask.

Will try that. Thanks for searching (apparently it's not a common question).

---

