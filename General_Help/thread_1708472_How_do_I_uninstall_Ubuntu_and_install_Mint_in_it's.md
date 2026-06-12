---
title: "How do I uninstall Ubuntu and install Mint in it's place?"
date: 2011-03-16
forum: General Help
---

### Post by Perpetual_Bliss on 2011-03-16
I got bored with Ubuntu pretty quick, and now just want something that works fast on my netbook, so I want to uninstall Ubuntu and replace it with Linux Mint xfce -- I was wondering if there was a way I could do that directly? 

Any advice on how I should go about doing this is greatly appreciated - Pleases and thank yous!

Oh, I should add that my netbook is currently dual booting win7 starter and Ubuntu 10.10 netbook edition

---

### Post by davepoth on 2011-03-16
Probably be easiest to delete the partition with Ubuntu on and start again.

---

### Post by zvacet on 2011-03-16
Mint is based on Ubuntu so the install process should be the same.When you came to the partition stage install Mint on Ubuntu partition.That should do it.

---

### Post by Perpetual_Bliss on 2011-03-16
> **zvacet said:**
> Mint is based on Ubuntu so the install process should be the same.When you came to the partition stage install Mint on Ubuntu partition.That should do it.
Thanks. So, I don't need to delete the Ubuntu parition beforehand? I'm afraid if I delete it first, I'll get rid of GRUB and my system won't start.

---

### Post by techunit on 2011-03-16
> **Perpetual_Bliss said:**
> Thanks. So, I don't need to delete the Ubuntu parition beforehand? I'm afraid if I delete it first, I'll get rid of GRUB and my system won't start.
No you don't have to delete the partition before hand. In Mint it uses a different partitioner in the installer. I believe that if your going to be partitioning you will end up using gparted (very easy to work with).

However I cannot remember if that is the actual partitioner used in the installation of mint.

If you are going for a straight install you should be able to just use the installation wizard.

Now if your problem lies with the GUI of Ubuntu that can easily be fixed. However with 11.04 coming out so soon with so many UI changes I might advise you to wait.

---

### Post by MARP1961 on 2011-03-16
Before you go with Mint, perhaps you should Google 'Mint Hamas'.

---

### Post by Hugh971 on 2011-03-16
If the reason you want to try Mint is for XFCE you could always just install XFCE on top of Ubuntu. That way you wouldn't lose anything.

---

### Post by Perpetual_Bliss on 2011-03-16
How do I do that? And will it bloat up the OS? I just want Gnome/Unity gone, and use only xfce.

---

### Post by Perpetual_Bliss on 2011-03-16
Anyone? *BUMP*

---

### Post by Strongman332 on 2011-03-16
no it should not slow your computer down any. however it will take some space up on your hard drive. to switch between the two just pick which one you want when you login

---

### Post by zvacet on 2011-03-17
If you want to add xfce then

```
sudo apt-get install xubuntu-desktop
```

and if you want to remove gnome and use xfce read [this.]("http://www.psychocats.net/ubuntu/purexfce")

---

