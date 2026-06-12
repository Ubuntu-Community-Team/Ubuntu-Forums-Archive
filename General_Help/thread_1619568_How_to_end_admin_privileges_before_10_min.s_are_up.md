---
title: "How to end admin privileges before 10 min.s are up in Lucid Lynx"
date: 2010-11-11
forum: General Help
---

### Post by InMyHumbleOpinion on 2010-11-11
I recently installed Maverick Meerkat on a hand me down laptop.  And noticed that when I entered the password for admin privileges to install from the update manager, a key icon appeared on the top bar.  I moused over it and saw I could use THAT to end privileges before the 10 minute grace was up.  I should have thought of it before, and, small as it is, I thought this was a great feature.

So, when I upgraded from Karmic Koala to Lucid Lynx on my desktop, I thought that feature would be there, but it's not.

So first I'm wondering if it's there, but just not default.  If so, how do I get that icon to appear?  If not, how do I otherwise end admin privileges early?

---

### Post by dcstar on 2010-11-12
> **InMyHumbleOpinion said:**
> 
.........
If not, how do I otherwise end admin privileges early?

```
sudo -k
sudo -K
```

---

### Post by mister_playboy on 2010-11-12
That key icon was new in 10.10.  It's not part of 10.04, AFAIK.

---

### Post by oldos2er on 2010-11-12
> **InMyHumbleOpinion said:**
>  how do I otherwise end admin privileges early?

You can edit /etc/sudoers and change the default timeout: [http://art.ubuntuforums.org/showthread.php?t=763142](http://art.ubuntuforums.org/showthread.php?t=763142)

---

