---
title: "msttcorefonts"
date: 2011-12-23
forum: General Help
---

### Post by rng on 2011-12-23
I cannot find msttcorefonts in synaptic, though it is supposed to be there: 

[https://help.ubuntu.com/community/UbuntuEyeCandy](https://help.ubuntu.com/community/UbuntuEyeCandy)

---

### Post by Bucky Ball on 2011-12-23
ttf-mscorefonts-installer

That's what you're after. What release are you using???

---

### Post by rng on 2011-12-23
Thanks. I think, once I install ttf-mscorefonts-installer I would need to run it. Would the command be 'sudo ttf-mscorefonts-installer' or something else?

I am using 10.04 LTS.

---

### Post by howefield on 2011-12-23
Just search for it in Synaptic and mark for install. You won't need any commands.

Once installed, the fonts will be available for you to use.

---

### Post by Bucky Ball on 2011-12-23
Just install it. It is the msfonts installer and therefore that's what it will do. See here:

[http://blog.sudobits.com/2010/06/25/how-to-install-mircosoft-windows-fonts-on-ubuntu-10-04/](http://blog.sudobits.com/2010/06/25/how-to-install-mircosoft-windows-fonts-on-ubuntu-10-04/)

Disregard the second section with deals with copying fonts from a Windows install (unless you only want particular fonts and not all of them). ;)

---

### Post by rng on 2011-12-23
According to the link, font files should be in '.Fonts' folder in home, but I read somewhere they should be in /usr/share/fonts folder?

[http://blog.sudobits.com/2010/06/25/how-to-install-mircosoft-windows-fonts-on-ubuntu-10-04/](http://blog.sudobits.com/2010/06/25/how-to-install-mircosoft-windows-fonts-on-ubuntu-10-04/)

---

### Post by spcwingo on 2011-12-24
> **rng said:**
> According to the link, font files should be in '.Fonts' folder in home, but I read somewhere they should be in /usr/share/fonts folder?

[http://blog.sudobits.com/2010/06/25/how-to-install-mircosoft-windows-fonts-on-ubuntu-10-04/](http://blog.sudobits.com/2010/06/25/how-to-install-mircosoft-windows-fonts-on-ubuntu-10-04/)

If installed in ~/.fonts they would only be available to that one user.  If installed in /usr/share/fonts they would be available to all users (with the correct permissions, of course).  ;)

---

### Post by Bucky Ball on 2011-12-24
Do you want to install specific fonts or just mscorefonts??? If the later just install the installer from Synaptics as previously mentioned. That easy. It will install all ms fonts ...

---

### Post by illuminator08 on 2012-01-14
I have found several of the MS fonts do not seem to install.

- helvetica
- cambria

are two specifically...

Any ideas?
:D

---

