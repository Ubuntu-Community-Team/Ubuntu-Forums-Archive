---
title: "Puredyne - can't open deb packages?"
date: 2011-04-20
forum: General Help
---

### Post by djwkd on 2011-04-20
Hi,

I'm trying to install Skype. I downloaded the deb file (Puredyne is Ubuntu based, so I figured it uses deb files, right? lsb_release-a gives me Ubuntu 9.10.)

Anyway, when I double click on deb files, it comes up with the "Oopen With" dialogue.

I've chmoded the file with

```
chmod +rwx skype.deb
``` But perhaps thats the problem?

Thanks in advance,

Dom.

---

### Post by nitstorm on 2011-04-20
have you tried
```
sudo dpkg -i skype.deb
```

---

### Post by djwkd on 2011-04-20
Aye, that appears to have worked - cheers!

---

