---
title: "difference in files size when copy paste"
date: 2011-02-25
forum: General Help
---

### Post by moh2010 on 2011-02-25
Hi,

I am trying to copy my home folder to other drive for backup,when I rigtclick it to see the file size of the folder, it shows 11.3 gb and stops there.But when i am  pasting it to the other drive  which has 15 gb free ,it is saying that the file size is 20.6 gb ,so not enough space.

Why is that?

Do I have a trojan?

How can I scan for spywares in Ubuntu 9.10 apart from clamav and wireshark

thanks

---

### Post by ragtag on 2011-02-25
Try opening a terminal and running:

```
du -sh /home/username
```

Where username is your username. This should give you the correct size of your home folder. 

Also note that your home folder contains lots of hidden folders used by various programs. Do Ctrl-H in the file browser (Nautilus) to see them. Some of these can actually be quite big.

---

