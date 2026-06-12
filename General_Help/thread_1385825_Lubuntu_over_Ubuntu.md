---
title: "Lubuntu over Ubuntu"
date: 2010-01-20
forum: General Help
---

### Post by chisle on 2010-01-20
I wanted to know if it is pretty safe to install lubuntu over ubuntu so that i just need to change sessions to go into lubuntu GUI. i was looking at it in the synaptic package manager and it asks me to remove network manager and network manager GNOME. not sure if i want to do this or what will happen. I read about installing kubuntu-desktop over ubuntu and how that is fine. i wanted to try out lubuntu since it is less resource intensive and my laptop is 5 years old and probably could use something  like that. plus not to mention i been trying to get my dad to switch to linux but i know his computer is pretty old, he's still running windows 98.  thanks for any suggestions.

---

### Post by SchizmWolf on 2010-01-20
My advice is to not do it until it's *at least* in the beta stage. Installing an alpha over anything is a bad idea unless you've a backup or are running it in such a way that a major error in it wouldn't effect the parameters of the main op.

---

### Post by AntoniusMisfit on 2010-01-20
A safe way to test is to try it with a VM with Ubuntu already installed on it. I'm going to try that, but first I'll do it with a minimal(command-line only) install and "sudo apt-get install lubuntu-desktop" as if installing a Lubuntu iso.

I'll post here with my results tomorrow.

---

### Post by AntoniusMisfit on 2010-01-20
Well, I'm making this post within a "Lubuntu" VM after installing a minimal environment and doing a "sudo apt-get install lubuntu-desktop" to install the LXDE environment. It's a pretty standard LXDE environment, but enough parts of GNOME are automatically installed as to fool GDM into having "GNOME" as the default desktop choice. Just switch it to LXDE and then remove the gnome-session package afterwards. And as far as Wicd replacing network-manager, it seems to work decent enough as to not worry about it.

---

### Post by chisle on 2010-01-20
alright thanks for the post AntoniusMisfit. I'm glad you did it first, lol, so i didnt have to be the lab rat. i think i'll be trying it on vm as well.

---

