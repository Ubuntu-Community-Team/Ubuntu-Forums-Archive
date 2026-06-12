---
title: "Auto-mount luks encrypted partition at boot"
date: 2010-05-27
forum: General Help
---

### Post by ctothej on 2010-05-27
I'm having a problem auto-mounting a new luks partition. I have crypttab and fstab entries. I already have my primary encrypted partition (root) mounting at boot (from the install), but after creating this one manually, it does not open on boot. It auto-mounts when I run the following command manually after boot: [FONT="Courier New"]sudo luksOpen /dev/disk/by-uuid/<uuid> mycrypt[/FONT]

/etc/crypttab entry:
[FONT="Courier New"]personalcrypt /dev/disk/by-uuid/a1af5b7b-db58-4690-b586-b74407795e2c none luks[/FONT]

/etc/fstab entry:
[FONT="Courier New"]/dev/mapper/personalcrypt /media/personalcrypt  ext4    auto,rw,user,exec,dev,suid   0       0[/FONT]

How can I get it to automatically mount at startup with the other?

Lucid x64

---

### Post by ctothej on 2010-06-02
bump

---

