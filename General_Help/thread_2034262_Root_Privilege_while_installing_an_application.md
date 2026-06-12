---
title: "Root Privilege while installing an application"
date: 2012-07-28
forum: General Help
---

### Post by omiazad on 2012-07-28
Hi,
I wanted to install my printer's Driver/Software from [here]("http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_PROSPECT_PRO209&page=product&frompage=null#1") on Ubuntu 12.04 but it's asking me to provide Root password-
[IMG]http://i47.tinypic.com/2m6khuh.png[/IMG]

 When I put my password it either says wrong password or aborts installation-
[IMG]http://i48.tinypic.com/2mzw3ft.png[/IMG]

But when I install the same on Mint 13, it got installed like a charm. Do I need to enable administrative rights or something on my Ubuntu to install this software?

Please suggest.

---

### Post by sisco311 on 2012-07-28
It seems that the script prompts for the root password which is locked in Ubuntu. Run it as root:
```
gksu ./lexmark*.deb.sh
```


[uhelp]community/RootSudo[/uhelp]

---

### Post by The Cog on 2012-07-28
Read this for full info: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I would suggest that you run the installer using gksu, like this, which will run it as root:
```
gksu ./lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh
```

Use **sudo** for text-only programs, but **gksu** for graphical ones.

---

### Post by sisco311 on 2012-07-28
> **The Cog said:**
> 
Use **sudo** for text-only programs, but **gksu** for graphical ones.

Point taken. Fixed my post. :)

---

### Post by omiazad on 2012-07-28
> **sisco311 said:**
> It seems that the script prompts for the root password which is locked in Ubuntu. Run it as root:
```
gksu ./lexmark*.deb.sh
```
[uhelp]community/RootSudo[/uhelp]

And which password to use?

Mint didn't need any special key for installing this. I wonder why it's needed on Ubuntu!

---

### Post by The Cog on 2012-07-28
With sudo and gksu, you give your own login password. This just proves it's you and not someone else who walked up to the computer while you were away getting a coffee.

@sisco311: I wasn't trying to correct you - your answer wasn't there when I started typing.

---

### Post by omiazad on 2012-07-28
> **The Cog said:**
> With sudo and gksu, you give your own login password. This just proves it's you and not someone else who walked up to the computer while you were away getting a coffee.

@sisco311: I wasn't trying to correct you - your answer wasn't there when I started typing.


Thanks a lot. It solved my problem. :)

---

