---
title: "I can't play DVD's"
date: 2009-11-05
forum: General Help
---

### Post by fbjoey on 2009-11-05
I cant play DVD's on my C Series Lifebook. When I insert the disk I get a disc icon on my desktop with the correct name. I try opening it with VLC and it lets me. But when I click play it quickly enlarges to full screen then goes back to the small view.

---

### Post by Giblet5 on 2009-11-05
Did you install ubuntu-restricted-extras yet?

(called restricted because some of the bits are closed source)

```
sudo apt-get install ubuntu-restricted-extras
```

It installs lots of audio and video codecs, plus the ability to decode protected DVDs.

---

### Post by aysiu on 2009-11-05
I think *ubuntu-restricted-extras* should cover it.

If it doesn't, you may have to install *libdvdcss2*, which is available in the Medibuntu repositories.

Instructions for adding Medibuntu:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by fbjoey on 2009-11-05
Yer I did that earlyer and still no luck.

---

### Post by michy99 on 2009-11-05
Check out the Comprehensive Multimedia & Video Howto:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by aysiu on 2009-11-05
> **fbjoey said:**
> Yer I did that earlyer and still no luck.
So both *ubuntu-restricted-extras* and *libdvdcss2* didn't work?

---

### Post by Maheriano on 2009-11-05
That thing is way too long to read, it confused me.

This will fix you up:
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
and then
```
sudo apt-get install libdvdcss2
```

---

### Post by coffeecat on 2009-11-05
If you have already installed ubuntu-restricted-extras **and** libdvdcss2, DVDs should also be playable in the default Totem Movie Player. Have you tried Movie Player? If DVDs work there then it's a VLC problem and we need to look closer at VLC. If not - I don't know.

> **Giblet5 said:**
> plus the ability to decode protected DVDs.

Unfortunately, not quite. Ubuntu-restricted-extras gives you libdvdread, but not libdvdcss2 which you need to unscramble encrypted DVDs.

---

### Post by AteZ on 2009-11-05
have you tried this yet?

DVD Menu Navigation
To fully enable DVD Menu support you’ll have to get your hands dirty by opening a terminal and typing: -

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

i found that one here: [http://www.omgubuntu.co.uk/2009/10/10-useful-things-to-do-after-installing.html]("http://www.omgubuntu.co.uk/2009/10/10-useful-things-to-do-after-installing.html")

---

### Post by fbjoey on 2009-11-05
libdvdcss2 fixed it :) Thanks again.

---

