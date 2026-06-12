---
title: "Quick question regarding grub"
date: 2011-06-02
forum: General Help
---

### Post by Setarkos on 2011-06-02
Can I restore grub1 with a ubuntu 11.04 live cd?
if yes how, cause "sudo grub" doesn't work
or can i use grub 2 for fedora 12 and windows 7? i think i recall that fedora would need a chainloader and it's own grub1 but that's the one that's broken

---

### Post by Setarkos on 2011-06-02
I tried ```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda

```but after the last command it returns:
```
/usr/sbin/grub-setup: error: will not proceed with blocklists.
```

tried this also but this was grub1 i think and it doesn't know the command:
```
sudo grub
```

---

### Post by Setarkos on 2011-06-02
Downloaded an old Ubuntu live cd and followed the old instructions - fixed it
thanks to anyone who was going to help me...

---

