---
title: "Help with Ati drivers 11.8"
date: 2011-08-22
forum: General Help
---

### Post by Perseides on 2011-08-22
Firstly, i apologize if i posted in the wrong section of the forum and for being noobish in ubuntu......

its my first time using ubuntu (anything besides windows >.<)  and i d just installed ubuntu 11.04 in my comp. Now theres some problem with my ati driver.... i cant seems to install it. 

I d googled it and found the site:
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html)
which explains step by step how to repackage the whole thing...

but when i tried to installed the repackaged .deb ati driver, this occurs and i cant install it, it says:

dpkg: error processing fglrx (--install):
dependency problems - leaving unconfigured

any1? help plz?

---

### Post by jfed on 2011-08-22
When I had to install my restricted drivers it was quite easy, I have a bit of an older card but it might still work, not sure though.

Go to System>Administration>Additional Drives

From there you might be able to install the graphics drivers you need easily.

hope this helped

---

### Post by Perseides on 2011-08-22
I d tried that, but a problem stating: 

SystemError: Binary package fglrx has no trusted origin, rejecting. 

cant install. =(

---

### Post by benjy on 2011-09-03
@Perseides,

I too had that problem with the Restricted Drivers installer. 

I fixed it by opening up a terminal and doing the following:

```
sudo apt-get update && sudo apt-get upgrade
```

I am setting up a friends laptop which uses an ATI HD 4250 and to be honest with the proprietory drivers it's a little laggy.

I'm going to try the 11.8 drivers straight from ATI but.. I've never had a whole lot of luck with them in the past.

---

