---
title: "Debconf pop up?"
date: 2011-05-18
forum: General Help
---

### Post by cblnchat on 2011-05-18
Ive been getting this pop up screen on my computer quite often.  It ranges from just a blink to a few seconds...im not sure what it is or how i can fix it.  

Thanks.

---

### Post by ivanovnegro on 2011-05-18
I have this also on Xubuntu 11.04 but only when I install new things from the Software Center or Synaptic.
Never experienced this before on Ubuntu 10.10 and older Ubuntu releases.

---

### Post by cblnchat on 2011-05-21
> **ivanovnegro said:**
> I have this also on Xubuntu 11.04 but only when I install new things from the Software Center or Synaptic.
Never experienced this before on Ubuntu 10.10 and older Ubuntu releases.

Neither have i.  But it seems to do it randomly to me.  
Maybe when i install something...ill have to pay more attention next time.

---

### Post by 5149.5 on 2011-05-21
I see it happen during software installation.

---

### Post by Hedgehog1 on 2011-05-21
I am also seeing it pop up during software installation.

I think this is an (annoying but harmless) bug.

***The Hedge***

:KS

p.s. I think I first noticed it during the final beta, so the change happened just before release of 11.04

---

### Post by dcstar on 2011-05-23
```
sudo dpkg-reconfigure debconf
```

Select the "Gnome" option.

---

### Post by ivanovnegro on 2011-05-23
> **dcstar said:**
> ```
sudo dpkg-reconfigure debconf
```Select the "Gnome" option.

Does this command serve to fix the popping debconf?

---

### Post by cblnchat on 2011-05-25
> **dcstar said:**
> ```
sudo dpkg-reconfigure debconf
```Select the "Gnome" option.

I did that, and i installed something from Software Center and i got it 5 or so times...its seems almost like it made it worse.

---

### Post by drascus on 2011-06-22
I have also been getting this... I haven't been able to nail down a cause yet. If anyone has fixed it please update this thread. don't know if this helps but I get this message in terminal while installing...

> debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied


---

### Post by drascus on 2011-06-28
Just wanted to add that ever since I have logged into my account with my password I have never seen this message again. Let me know if that fixes it for anyone else.

---

### Post by Baneblade on 2012-08-26
We are approaching the end of 2012 and still getting this on 12.04 with latest updates installed.

Has anyone found a fix for this yet?

---

