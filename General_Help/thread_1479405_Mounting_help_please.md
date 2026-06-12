---
title: "Mounting help please???"
date: 2010-05-10
forum: General Help
---

### Post by k1ng0fn3rds on 2010-05-10
when i powered on my computer i went to mount my second internal hard drive.  Normally it just opens right up no problem but today for some reason it says that im "Not Authorized" to do it.  same goes for flash drives.  My comp is running ubuntu 10.04 . What should i do???

---

### Post by snoopo71 on 2010-05-10
> **k1ng0fn3rds said:**
> when i powered on my computer i went to mount my second internal hard drive.  Normally it just opens right up no problem but today for some reason it says that im "Not Authorized" to do it.  same goes for flash drives.  My comp is running ubuntu 10.04 . What should i do???

Did you play with fstab? or install some disk mounting app?
Paste your fstab here please (etc/fstab)

---

### Post by rcayea on 2010-05-10
> **k1ng0fn3rds said:**
> when i powered on my computer i went to mount my second internal hard drive.  Normally it just opens right up no problem but today for some reason it says that im "Not Authorized" to do it.  same goes for flash drives.  My comp is running ubuntu 10.04 . What should i do???

I am not totally sure this will help, but maybe try changing ownership. It sounds like your permissions were messed with.

try:sudo chown yourloginnamehere /dev/where/it/is/located

I hope this helps...

---

### Post by k1ng0fn3rds on 2010-05-10
> **snoopo71 said:**
> Did you play with fstab? or install some disk mounting app?
Paste your fstab here please (etc/fstab)
i didnt do ANYTHING to it, just turned it off saturday evening (properly) and powered it up today and boom drives wont mount, and i dont have fstab or disk mounting app

---

### Post by jerome1232 on 2010-05-10
fstab is a system file that handles automatic mounting of drives at boot time, let's hope you have one!

However it sounds like your talking about removable media which fstab has nothing to do with, I'm not sure why it stopped working for you but it sounds to me like your user isn't in a group that you should be.

Try going to System-Administration-Users and Groups, click Advanced Settings, make sure "Access external storage media automatically" is checked.

Will take a logout and log back in to take affect.

---

### Post by k1ng0fn3rds on 2010-05-10
> **rcayea said:**
> I am not totally sure this will help, but maybe try changing ownership. It sounds like your permissions were messed with.

try:sudo chown yourloginnamehere /dev/where/it/is/located

I hope this helps...
tried, did not work

> **jerome1232 said:**
> fstab is a system file that handles automatic mounting of drives at boot time, let's hope you have one!

However it sounds like your talking about removable media which fstab has nothing to do with, I'm not sure why it stopped working for you but it sounds to me like your user isn't in a group that you should be.

Try going to System-Administration-Users and Groups, click Advanced Settings, make sure "Access external storage media automatically" is checked.

Will take a logout and log back in to take affect.
tried, when i got to the panel, nothing would happen when i clicked Advanced Settings 
i think more is messed up than i originally thought

---

### Post by jerome1232 on 2010-05-10
Pop open a terminal, (applications-accessories-terminal)

and post the output of the following command please

```
groups
```

ctrl+shift+c to copy text from a terminal btw.

---

### Post by k1ng0fn3rds on 2010-05-10
here it is:
> jeff@jeff-desktop:~$ groups
jeff adm dialout cdrom plugdev lpadmin admin sambashare
jeff@jeff-desktop:~$ 



---

### Post by jerome1232 on 2010-05-10
ok so it's not what I thought then, those groups are correct and fine. Hopefully some one more knowledgeable than I will drop in here and help you out.

---

### Post by drdos2006 on 2010-05-10
Open up a terminal.
type : sudo cp /etc/fstab  /etc/fstab.backup
type : sudo gedit /etc/fstab

Open a second terminal.
Type : ls -l /dev/disk/by-uuid

Compare the UUID of your drive/s and compare with fstab.

regards

---

### Post by k1ng0fn3rds on 2010-05-10
ok well i dont know what i did i was playing around with some mounting software from the software center and i got it working, ty to all who tried to help

---

