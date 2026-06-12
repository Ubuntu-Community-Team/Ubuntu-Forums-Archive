---
title: "Automount samba shares and offline working"
date: 2010-04-14
forum: General Help
---

### Post by seangee on 2010-04-14
I have an Ubuntu NAS which is working really well. At home I am able to automount the shares automatically. I am trying to create a transparent method for enabling offline working on a laptop / netbook. I have been experimenting with Unison for file synchronisation and that is also looking good so far. My question is really to do with bash.  What I am trying to achieve at startup in pseudo code:

```
mount mysambashare into /home/documents // I know how to do this :) 
If mount was successful // where I need help
  do some stuff - e.g. synchronise localcachedir
Else // i.e. sambashare not available because I'm not at home
  mount localcachedir into /home/documents

```Obviously synchronisation is my own problem but what I am trying to achieve is that /home/documents is always available with current content and is synched back when I have been offline and get back onto my home network. Any ideas?

---

### Post by seangee on 2010-04-14
Well this is crude but works for me.

Continue to mount via fstab

Then in my startup script
```
sleep 5
ONLINE=`mount |grep -c "192.168.20"`
if [ $ONLINE -gt 0 ]; then
  echo "Online"
else
  echo "Offline"
fi
```

---

