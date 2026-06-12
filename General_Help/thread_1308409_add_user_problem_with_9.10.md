---
title: "add user problem with 9.10"
date: 2009-10-31
forum: General Help
---

### Post by mrpeachy on 2009-10-31
This is what just happened

I added a user for my son, an unprivalidged account.

I went to switch user and just got a black screen (monitor powered down)
so i rebooted and logged into my sons account.

then i switched user to my main account and it switched but then docky wasnt running and when i tried to start it it said it needed compiz (previously everything had been running fine)

so i went to the apperances, clicked on normal desktop effetcs, a box appeared that said it was checking avaialable drivers and then told me that it couldnt enable effects!

i restarted and logged into main account and was then able to enable the effects.

i already had a bad experience upgrading from 9.04 to 9.10... so this was not a pleasant experience!

has this happened to anyone? or a know bug?

---

### Post by emigrant on 2009-10-31
compiz seems unable to run on two users simultaneously.
i have that problem.

---

### Post by mrpeachy on 2009-10-31
good to know that its not just me!
i had horrible visions of having to reinstall AGAIN

---

### Post by roel46 on 2009-11-01
I have a problem with "add user" (System > Administration > Users and Groups) too, maybe related:
[LIST]
[*]my system froze when I added the third user; I gave a hard reset
[*]when I started the "Users and Groups" again, root was the only user visible
[*]note: I did a fresh install; I chose Ext4 (file system)
[*]note: I consider to do a reinstall with Ext3
[/LIST]
groeten, Roel.

about 3 hours later:
Well..., I did my reinstall with Ext3. Adding users worked OK. However later my system froze when editing some text file. Therefore I think:
[LIST]
[*] my "add user" problem is not caused by Ext4 but by my hard reset while using "Users and Groups"
[*] I guess Ubuntu 9.10 suffers freezing problems (with some hardware)
[/LIST]
p.s. emigrant, thanks for your suggestion

---

### Post by emigrant on 2009-11-01
if you want to add a user anyway,
you can do in the terminal:


sudo useradd <username>

---

