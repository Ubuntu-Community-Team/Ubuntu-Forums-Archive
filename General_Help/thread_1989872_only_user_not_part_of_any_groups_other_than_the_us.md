---
title: "only user not part of any groups other than the username itself"
date: 2012-05-28
forum: General Help
---

### Post by kindrudekid on 2012-05-28
i was trying something on my ubuntu 12.04 ... basically trying to get my PLex mediaserver to detect movies from network shares and i thought to add my user and root to group plex that the server creaates and add plex to the group of USERNAME and root...

and i rebooted now i cannot sudo run tasks

cannot even unlock users and groups

when i check groups USERNAME it shows only USERNAME and plex

for groups root it shows root and plex

how can i fix and remove root and USERNAME from plex group

EDIT:

i rebooted into recovery

tried adding my USERNAME to group admin but it says group doesnt exists when i try to create admin it says it already exists when i try to add USERNAME to gid 120 it says USERNAME exists...

PS: the file /etc/group is read only

---

### Post by matt_symes on 2012-05-28
Hi

Add yourself to the sudo group from a liveCD or the recovery mode from the grub screen.

These are my groups.

```
matthew@matthew-Aspire-7540 ~ % groups
matthew adm cdrom sudo dip plugdev fuse lpadmin sambashare
matthew@matthew-Aspire-7540 ~ %
```

```
sudo usermod -aG sudo username
```

Kind regards

---

### Post by kindrudekid on 2012-05-28
i cannot even sudo

---

### Post by matt_symes on 2012-05-28
Hi

Can you boot into recovery mode from the grub screen. If you can, drop to a root terminal and then you wont require sudo.

Kind regards

---

### Post by kindrudekid on 2012-05-28
> **matt_symes said:**
> Hi

Can you boot into recovery mode from the grub screen. If you can, drop to a root terminal and then you wont require sudo.

Kind regards

lemme do that now

---

### Post by kindrudekid on 2012-05-28
Cannot lock /etc/passwd try again later


here is another thing

[IMG]http://i.imgur.com/IZGZZ.jpg[/IMG]

---

### Post by matt_symes on 2012-05-28
Hi

Are you sure you're at the root console ?

Kind regards

---

### Post by kindrudekid on 2012-05-28
yesss cant you see root@USERNAME-Laptop

---

### Post by matt_symes on 2012-05-28
Hi

I think we were cross posting as you posted that screenshot after i asked that question about the root console.

Is your root partition mounted read only ?

```
mount | grep ^/dev
```

If it says ro then remount it rw.

```
mount -o remount,rw /
```

Kind regards

---

### Post by kindrudekid on 2012-05-28
nope i dont think so how can i check that?

---

### Post by matt_symes on 2012-05-28
Hi

Type the mount comand i posted in the last post. Look for a line like this

```
/dev/sda1 on / type ext4 (**[COLOR="Red"]ro[/COLOR]**,errors=remount-ro)
```

If you see a line that says ro (like i highlighted above) then run the second comand i posted above.

If it say rw then it is mounted read write.

Kind regards

---

