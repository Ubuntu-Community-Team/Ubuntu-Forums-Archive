---
title: "Is there a way to manually install GParted?"
date: 2010-01-27
forum: General Help
---

### Post by diligence400 on 2010-01-27
I have a Ubuntu system where the internet has been whitelisted so that I can't use Synaptic. I was wondering if there was a way to install GParted without Synaptic? Do something with the ISO file perhaps? Or would this turn out to be quite complicated?

---

### Post by Locutus_of_Borg on 2010-01-27
can you download the source?

or go to packages.ubuntu.com and download the deb?

---

### Post by garvinrick4 on 2010-01-27
What is white listed? I know a little code to get internet access but do not understand whitelisted.

---

### Post by lisati on 2010-01-27
[http://en.wikipedia.org/wiki/Whitelist](http://en.wikipedia.org/wiki/Whitelist)

---

### Post by zeroseven0183 on 2010-01-27
If you want, you can download the latest stable release of Gparted at [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

Or use the LiveCD instead.

---

### Post by Lars Noodén on 2010-01-27
> **diligence400 said:**
> I have a Ubuntu system where the internet has been whitelisted so that I can't use Synaptic. I was wondering if there was a way to install GParted without Synaptic? Do something with the ISO file perhaps? Or would this turn out to be quite complicated?

What's the obstacle to getting the Ubuntu repositories whitelisted?  They should all be **.archive.ubuntu.com*.  It would help to know the situation if there are barriers and to know the what excuses the barriers are offering. 

You can install from a USB stick if you also have the dependencies there, too.

---

### Post by Robster2 on 2010-01-27
Gparted is on the live CD but it does not install.

If you do a 

locate  gparted 

find out where the files are and copy them?

---

### Post by lisati on 2010-01-27
> **Robster2 said:**
> Gparted is on the live CD but it does not install.

If you do a 

locate  gparted 

find out where the files are and copy them?

Or ```
sudo apt-get install gparted
```

---

### Post by efflandt on 2010-01-27
You can insert an installation CD for your Ubuntu version, check the box in Synaptic to add the CD as a source (repository), refresh its list, and install gparted from there.

---

### Post by diligence400 on 2010-01-28
> **Locutus_of_Borg said:**
> can you download the source?

or go to packages.ubuntu.com and download the deb?

This worked! Thanks :D

As for why I need to do this, it's a long story, but just take it as me learning something new :)

I know it's better for Synaptic to do installations as it will deal with all the dependencies, which sucks for people who don't have internet...

---

