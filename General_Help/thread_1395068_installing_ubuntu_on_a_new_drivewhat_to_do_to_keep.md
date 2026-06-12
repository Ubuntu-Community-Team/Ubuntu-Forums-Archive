---
title: "installing ubuntu on a new drive/what to do to keep as much as possible"
date: 2010-01-31
forum: General Help
---

### Post by chriskin on 2010-01-31
1)copy sources lists
2)copy home folder
3)make a list of all the applications installed (not be hand, by the command i mean)

is there anything else that needs to be done other those?
will doing those make my installation look exactly the same on the new drive?

(i plan to upgrade parts of the laptop (it can hold only one hard disk) ,including choosing a new three-times-bigger 7200rpm one instead of the default small 5400rpm one)

---

### Post by spiky001 on 2010-01-31
Have you thought about clonezila?

---

### Post by chriskin on 2010-01-31
yes, and i would probably have to spend more time configuring the grub lists etc that way
and i'm not as good with grub 2 as i was with legacy grub

---

### Post by oldfred on 2010-01-31
I installed Karmic clean but kept my old install of 9.04 just in case. I found I did go back to see my fstab settings as I had added several additional mount points - I could have recreated, but it was easy to go back and copy. I also had some settings in samba that I wanted.

I think you need to remember if you made any major changes to various config files and if they would be important for a new install.

I was trying to keep a list of files I edited but they keep becoming obsolete - menu.lst, xorg.conf.

---

### Post by nothingspecial on 2010-01-31
If you have edited configs much then I would save /etc

---

### Post by chriskin on 2010-01-31
> **oldfred said:**
> I installed Karmic clean but kept my old install of 9.04 just in case. I found I did go back to see my fstab settings as I had added several additional mount points - I could have recreated, but it was easy to go back and copy. I also had some settings in samba that I wanted.

I think you need to remember if you made any major changes to various config files and if they would be important for a new install.

I was trying to keep a list of files I edited but they keep becoming obsolete - menu.lst, xorg.conf.

i won't format the previous drive so if anything is worth the trouble i can always come back for it - i will just turn it into an external (at least until i am sure i no longer need it)

> **nothingspecial said:**
> If you have edited configs much then I would save /etc

thanks

---

### Post by nothingspecial on 2010-01-31
That being said, I "try" to know what I`ve edited and save it to /blah/blah/configs

Such as sources.list or mpd.conf 

As I edit I backup, if you know what I mean.

---

### Post by chriskin on 2010-01-31
i am not be the best at remembering to make backups though :S

---

### Post by nothingspecial on 2010-01-31
> **chriskin said:**
> i am not be the best at remembering to make backups though :S

Nor was I till I had major data loss;)

---

