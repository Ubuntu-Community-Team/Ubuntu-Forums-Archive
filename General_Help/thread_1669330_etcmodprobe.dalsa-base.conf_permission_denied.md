---
title: "/etc/modprobe.d/alsa-base.conf permission denied"
date: 2011-01-17
forum: General Help
---

### Post by haste28 on 2011-01-17
im using a mac mini and to make the sound work i need to enter this command in terminal
sudo echo 'options snd-hda-intel model=mbp55' >> /etc/modprobe.d/alsa-base.confbut when i do that it gives me this error
/etc/modprobe.d/alsa-base.conf permission denied
which is weird beacuse im the admin and have all privileges 
please help guys 

p.s i posted this in general help not the mac section beacause this is an error with
terminal

---

### Post by lithopsian on 2011-01-17
You can do everything but you might have to change the permissions on the file first ;)

Anyway, in this case I think your difficulty is caused by the sudo provileges not propagating through the >> command.  Edit it more directly or su to root.

---

### Post by haste28 on 2011-01-17
umm im a complete noob and i didnt understand half the things you said please keep that in mind i now it's annoying to describe something in long detail but bear with me guys thanks

---

### Post by lithopsian on 2011-01-17
Type:
```

sudo chmod 666 /etc/modprobe.d/alsa-base.conf
echo 'options snd-hda-intel model=mbp55' >> /etc/modprobe.d/alsa-base.conf
sudo chmod 644 /etc/modprobe.d/alsa-base.conf

```
Enter your password if requested.

As an alternative edit the file in your favourite editor (using sudo or as root) and type in "options snd-hda-intel model=mbp55" at the end.

---

### Post by haste28 on 2011-01-18
thanks guys i fixed it the sound works fine now

---

