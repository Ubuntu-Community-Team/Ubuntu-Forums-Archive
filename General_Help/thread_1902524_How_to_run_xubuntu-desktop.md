---
title: "How to run xubuntu-desktop???"
date: 2011-12-31
forum: General Help
---

### Post by jmoney47 on 2011-12-31
Hey everyone, 

I have just installed Ubuntu 11.04 Chroot onto my HP TouchPad. I used the command "apt-get install xubuntu-desktop" to download the xfce desktop, but I can't figure out how to start it. What command should I type to run it? For example, with lxde it is "lxdesession."

Any suggestions would be greatly appreciated.

---

### Post by dRounse on 2011-12-31
Sign out, and on the login screen there should be a box that says Unity or whatever you are using and press that and XFCE should be an option

---

### Post by jmoney47 on 2011-12-31
> **dRounse said:**
> Sign out, and on the login screen there should be a box that says Unity or whatever you are using and press that and XFCE should be an option

It doesn't exactly work like that. I am running it on an HP TouchPad, so all I have is a terminal in which I can type commands. It's similar to Ubuntu server where there is no GUI at all.

---

### Post by 2F4U on 2011-12-31
What about 
startxfce4?

---

### Post by Paqman on 2011-12-31
If it's 11.04 or earlier:

```
sudo service gdm start
```

For 11.10 or later:

```
sudo service lightdm start
```

---

