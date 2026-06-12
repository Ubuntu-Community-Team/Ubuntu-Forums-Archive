---
title: "Complete Removal in Synaptic Package Manager"
date: 2010-05-18
forum: General Help
---

### Post by Richiegs on 2010-05-18
I completely removed Skype in Synaptic Package Manager. When I later downloaded and installed Skype again from its web site, the same user name that I had used before was still there instead of being blank. I wonder what I should do if I want to erase the username that I used. Thank you very much

---

### Post by angry_johnnie on 2010-05-18
just a though, since i don't really use skype.

most apps keep their configuration files in a hidden folder within your home directory.

so, try looking for something like /home/you/.skype and delete it if you find it.

next time you run skype, it shouldn't remember you.

---

### Post by jerome1232 on 2010-05-18
I thought synaptics "completely remove" and apt-get's "--purge" options did the same thing, remove ALL files including configuration files, I may be wrong though.

Have you tried using apt-get with the --purge flag?

```
sudo apt-get remove --purge *packagename*
```

---

### Post by razorboy5 on 2010-05-18
yea running

sudo apt-get remove --purge

should remove everything u dont need from uninstalled apps (i think)

---

### Post by Richiegs on 2010-05-19
sudo apt-get remove --purge skype would not delete my username because after I reinstalled Skype, my user name was still there.

---

