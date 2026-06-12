---
title: "error 22"
date: 2009-08-07
forum: General Help
---

### Post by glennnf on 2009-08-07
Hi, i installed jaunty next to my existing jaunty(hda2)(yes,you read correctly)to do this i deleted hda1 &  hda3 partitions & installed 2nd jaunty to that partition (confused yet)all should have been fine except for error 22 on reboot.Problem2-cannot upload menu list, i recieve invalid file message,the menu list properties say's that it is a plain txts file ,what is the problem?.Thanks,Glennnf.

---

### Post by zvacet on 2009-08-07
Hope [this]("http://members.iinet.net.au/~herman546/p15.html#22") will help.If you are tryinf to edit menu list then do it in terminal

```
sudo gedit /etc/boot/grub/menu.lst
```

---

### Post by glennnf on 2009-08-08
Thanks Zvacet,that didn't work unfortunately,tried to locate where stage1 was & got 2 partitions that came up with 'unreconized device string'.I originally installed jaunty to dev/hda 2 but got hda/dev1 & 2 as stage 1 choices. I can access jaunty from live cd but need to get it to boot as ive spent a lot of time with desktop mods & conky scripts,would hate to have to start again.Any help would be really appreciated.Glennnf.

---

### Post by glennnf on 2009-08-08
I re burnt supergrub ,gave it a whirl & hey presto ,jaunt'y is back. All hail supergrub.Thanks, Glennnf.

---

