---
title: "Rearranging the grub"
date: 2010-07-06
forum: General Help
---

### Post by Total Noob on 2010-07-06
How do I change the default OS on grub, and adding more time to make my choice?

Thanks.

---

### Post by philinux on 2010-07-06
> **Total Noob said:**
> How do I change the default OS on grub, and adding more time to make my choice?

Thanks.

The easy gui way is to install startupmanager. 

[startupmanager]("apt:startupmanager")

The menu entry will appear in system>admin

---

### Post by wilee-nilee on 2010-07-06
> **Total Noob said:**
> How do I change the default OS on grub, and adding more time to make my choice?

Thanks.

It would probably help to name your distros, and post the output from this in a Ubuntu terminal.
```
sudo grub-install -v
```

As the above suggests startup manager is a good tool, in later distros it defaults to a grub.cfg line so if you get a kernel upgrade it will possibly offset where grub defaults to at boot, so just know how to get to the grub boot menu if your don't know now. You probably are getting the grub menu with the questions asked, I assume.

---

### Post by Total Noob on 2010-07-07
Thanks but I didn't have luck with either proposed solution.

My Ubuntu is 7.4; it neither had a startup manager nor access to it thru the repository.

I guess it will have to be by terminal, unfortunately, I don't know enough about it to have understood how to use sudo. I tried the instructions given, but was give a response like this: grub 0.97 installed. No opp'y to amend the functionality of anything.

Can I ask to have my hand held all the way? Thanks.

---

