---
title: "Anyone Having Probs Installing Latest Virtualbox .deb?"
date: 2012-03-16
forum: General Help
---

### Post by jim_deadlock on 2012-03-16
I've downloaded virtualbox-4.1_4.1.10-76795~Ubuntu~oneiric_amd64.deb and I've checked the md5sum but USC won't open it though, it just loads and loads forever. Anyone else having trouble?

---

### Post by nothingspecial on 2012-03-16
just done it a few minutes ago

```
sudo dpkg -i virtualbox-4.1_4.1.10-76795~Ubuntu~oneiric_amd64.deb 
sudo apt-get install -f
sudo adduser $USER vboxusers
```

---

### Post by Diametric on 2012-03-16
Yes, I've been having issues.  However, once I ran my update/upgrade commands from the CLI as opposed to from the software manager, the issue was resolved and I now have the latest version.  4.1.10

Make sure to run

```
sudp apt-get update
```

then

```
sudo apt-get upgrade
```

---

### Post by jim_deadlock on 2012-03-16
CLI worked, thanks.

---

### Post by imachavel on 2012-03-16
you of course mean AFTER you download the newest version right?


sudo dpkg -i virtualbox-4.1_4.1.10-76795~Ubuntu-oneiric_intel32.deb
[sudo] password for danel: 
dpkg: error processing virtualbox-4.1_4.1.10-76795~Ubuntu-oneiric_intel32.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox-4.1_4.1.10-76795~Ubuntu-oneiric_intel32.deb


LOL LOL LOL

but I don't know how to upgrade the vbox then import an existing vdi anyway. I'm sure it's simple, and I know I could ask at vbox forums, but my account no longer works over there since oracle updated the data base and I now need an oracle account to log in to the forums and ask perryg or some other mod a question. It's ok though I'm happy with my previous version, hope the OP got it figured out ok

OP, what host are you using, how many vbox vms do you plan to have running at once, and what OS in each vm? Just out of curiosity

---

### Post by jim_deadlock on 2012-03-16
> **imachavel said:**
> sudo dpkg -i virtualbox-4.1_4.1.10-76795~Ubuntu-oneiric_intel32.deb

That doesn't look right - ...intel32.deb ?? The 32 bit filename is virtualbox-4.1_4.1.10-76795~Ubuntu~oneiric_i386.deb

So this should be all that's needed, it should replace your old version:

```
sudo dpkg -i virtualbox-4.1_4.1.10-76795~Ubuntu~oneiric_i386.deb
```

<--- my host system is over here.

I have 8G physical RAM and I usually give 2G to each of my VMs. I have Win7, WinXP and various Linux distros. I can comfortably run several VMs at once if I want to. It's all about the RAM.

---

