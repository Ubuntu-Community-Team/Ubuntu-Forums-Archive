---
title: "Accidentally didn' t check OK for mscorefont installer"
date: 2011-11-05
forum: General Help
---

### Post by batido on 2011-11-05
Can someone assist me in installing the mscorefonts for Ubuntu 11.10?  While installing the restricted packages, I didnt click ok for the font installer by accident, and it of course refused to install the mscore fonts.  But I don't know how to go backwards and actually install the fonts.  Can someone assist?  Thanks!

---

### Post by sffvba[e0rt on 2011-11-05
Wild guess... have you tried re-running the restricted install?


404

---

### Post by batido on 2011-11-05
yes, i tried rerunning the install, nothing.

---

### Post by dniMretsaM on 2011-11-05
What do you get when you run this:
```
sudo apt-get update
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by batido on 2011-11-05
It says that 
ttf-mscorefonts-installer is already the newest version
and then it says that nothing was upgraded or updated.

Is there a way for me to "re-run"  ttf-mscorefonts-installer?  is it a program?  is there a command i would use?  thanks.

> **dniMretsaM said:**
> What do you get when you run this:
```
sudo apt-get update
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by dniMretsaM on 2011-11-05
> **batido said:**
> It says that 
ttf-mscorefonts-installer is already the newest version
and then it says that nothing was upgraded or updated.

Is there a way for me to "re-run"  ttf-mscorefonts-installer?  is it a program?  is there a command i would use?  thanks.

That means it's already installed.

---

### Post by mdhollis on 2011-11-05
what about:
```
sudo apt-get install msttcorefonts
```

---

### Post by batido on 2011-11-05
I went to the Ubuntu Software Center, and uninstalled ttf-mscorefonts-installer, and then re-installed it.

Upon reinstallation, it pops up a deconf on ubuntu screen that says:
Configuring ttf-mscorefonts-installer

and under that it says:
Declined "truetype core fonts for the web EULA" 

Under that it says:
If you do not agree to the "TrueType core fonts for the Web EULA " license terms you cannot install this software.

The installation of this package will be canceled.




And the only thing that I can do is click on a button that says forward.  I am not able to accept the agreement.  Can someone help?

---

### Post by batido on 2011-11-05
but the fonts aren't showing up.


> **dniMretsaM said:**
> That means it's already installed.

---

### Post by dniMretsaM on 2011-11-05
Try this:

```
sudo apt-get purge ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by tamerucar on 2011-12-03
> **dniMretsaM said:**
> Try this:

```
sudo apt-get purge ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer
```

Thanks, I did the same accidental decline, and purge did the magic :)

---

