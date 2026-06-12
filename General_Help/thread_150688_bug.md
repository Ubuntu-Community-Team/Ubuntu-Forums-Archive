---
title: "bug?"
date: 2006-03-26
forum: General Help
---

### Post by Viorus on 2006-03-26
Well, I havnt played attention for this that much. But now its getting a bit annoying. Everytime i have a cdrom/dvd in my cdplayer/dvdplayer it won't release my disc, unlease I choose unmount by clicking rightclick on that media. Is this a bug or just a problem with my comp?

---

### Post by eriefisher on 2006-03-26
That's just how it is in Linux. Mount->Unmount.

eriefisher

---

### Post by arnieboy on 2006-03-26
[QUOTE=Viorus]Well, I havnt played attention for this that much. But now its getting a bit annoying. Everytime i have a cdrom/dvd in my cdplayer/dvdplayer it won't release my disc, unlease I choose unmount by clicking rightclick on that media. Is this a bug or just a problem with my comp?[/QUOTE]
its a feature not a bug. since u find it annoying do the following from terminal:
```
sudo sysctl dev.cdrom.lock=0
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'
```
now reboot.

---

### Post by Viorus on 2006-03-26
[QUOTE=eriefisher]That's just how it is in Linux. Mount->Unmount.

eriefisher[/QUOTE]

lol guess I missed something then^^ thx anyway;)

---

### Post by eriefisher on 2006-03-26
If it bothers you then run Arnieboy's script to change it.

eriefisher

---

### Post by Viorus on 2006-03-26
yupp, working fine. thx for the help both=)

---

