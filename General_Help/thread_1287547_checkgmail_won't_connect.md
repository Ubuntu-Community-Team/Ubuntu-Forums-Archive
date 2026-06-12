---
title: "checkgmail won't connect"
date: 2009-10-10
forum: General Help
---

### Post by CarlC4 on 2009-10-10
every time i try to log into CheckGmail i get an error saying that I have incorrect username and password, but i actually do have the correct username and password. please help

---

### Post by akakingess on 2009-10-10
If you do a search on this forum,  you will find it has been an issue for a week or two, here is just one thread that I found [http://ubuntuforums.org/showthread.php?t=1268721&highlight=checkgmail](http://ubuntuforums.org/showthread.php?t=1268721&highlight=checkgmail)

---

### Post by tatsuno on 2009-10-13
```
checkgmail -update
```

---

### Post by P4man on 2009-10-13
consider using gnome-gmail-notifier instead. It integrates nicely with the notification stuff, although its rather light on features.

---

### Post by MyR on 2009-10-13
tatsuno: checkgmail -update wouldn't work for me.
P4man: checkgmail is one of the most useful apps for Linux (my experience)

I did this:

```
wget http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/checkgmail
sudo chmod +x /usr/bin/checkgmail
```

peace

---

### Post by Merovius on 2009-10-16
Thanks MyR that did the trick. :guitar:

---

### Post by Johnny B on 2009-10-16
try checkgmail -update
and use a capital Y

---

### Post by 123betty on 2009-10-21
> **Johnny B said:**
> try checkgmail -update
and use a capital Y 

Thanks!!
Tried several times to update with no luck until I saw your your comment about "Y"

---

