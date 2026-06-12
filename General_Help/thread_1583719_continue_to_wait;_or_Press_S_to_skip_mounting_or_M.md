---
title: "continue to wait; or Press S to skip mounting or M for manual recovery"
date: 2010-09-28
forum: General Help
---

### Post by romar_31 on 2010-09-28
ok. the scenario is i keep on getting that message every boot up and i get annoyed by hitting "s" every time i boot up. The system is fine, i think. :D

recently, i tried installing opensuse with lucid but unfortunately it screwed the partition table. It damaged my storage partition (ntfs) but luckily not the ubuntu(ext4). I had to rebuild grub 2 to be able to boot into lucid. And after reinstalling the grub via live CD and successfully booting into ubuntu, i keep on getting that message. Any idea how can i fix this? I would appreciate any suggestions. 

Actually, i really thought a hundred times if i would ask it here, for other's just look at it then leave. lol.

---

### Post by CharlesA on 2010-09-28
Check yer fstab. That error means it cannot find a device, or it has changed.

---

### Post by Quackers on 2010-09-28
I'm getting the same message on every boot now. It only lasts for about 3 or 4 seconds then the screen flashes and the message returns for a second, then the machine boots normally after that. On looking in etc/fstab it seems the partition being referred to is the swap partition. Curious.

---

### Post by CharlesA on 2010-09-28
The UUID could have been changed if another distro was installed.

Find the UUID:

```
sudo blkid /dev/sd??
```

Then replace the existing UUID for for swap in fstab.

---

### Post by Quackers on 2010-09-28
I did as you suggested CharlesA and the error message has disappeared! :-) Thank you - now what's next :-)

---

### Post by romar_31 on 2010-09-28
thanks for the reply, but how can i do that?

---

### Post by CharlesA on 2010-09-28
> **romar_31 said:**
> thanks for the reply, but how can i do that?

Hit+F2 and type this in:

```
gksu gedit /etc/fstab
```

Then run this command in a terminal:

```
sudo blkid -c /dev/null
```

Make sure that the UUIDs listed in fstab match.

---

### Post by romar_31 on 2010-09-28
> **CharlesA said:**
> Hit+F2 and type this in:

```
gksu gedit /etc/fstab
```Then run this command in a terminal:

```
sudo blkid -c /dev/null
```Make sure that the UUIDs listed in fstab match.
got it. thanks a lot. :) SOLVED.

---

### Post by Quackers on 2010-09-28
Nice one :-)

---

