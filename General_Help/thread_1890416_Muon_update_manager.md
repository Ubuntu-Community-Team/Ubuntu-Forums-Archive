---
title: "Muon update manager"
date: 2011-12-03
forum: General Help
---

### Post by fidelandche on 2011-12-03
Hi all,

I have installed Kubuntu 11.10 along side Ubuntu 11.10 via the software centre. The problem I am getting is the Muon update manager is telling me that I have four updates, I go to install them but I get the following error message.. *This operation cannot continue since proper authorization was not provided* So how do I go about the authorization process??

Cheers

---

### Post by bluexrider on 2011-12-03
run it with root permissions

sudo muon

---

### Post by oldos2er on 2011-12-03
Since muon is graphical you'd want to use ```
kdesudo muon
``` But, this is a known bug: [https://bugs.launchpad.net/ubuntu/+source/qapt/+bug/875657](https://bugs.launchpad.net/ubuntu/+source/qapt/+bug/875657)

---

### Post by fidelandche on 2011-12-03
Thanks for that, now able to update.

---

### Post by Megalex on 2011-12-04
I am having a similar issue. I tried using 

kdesudo muon and sudo muon but it is still showing the same error message

---

### Post by Megalex on 2011-12-04
> **Megalex said:**
> I am having a similar issue. I tried using 

kdesudo muon and sudo muon but it is still showing the same error message

Let me revise what I said... I am having a similar issue, but the error message that is showing up is,

"Another application seems to be using the package system at this time. You must close all other package managers before you will be able to install or remove other packages."

I doubt if there is indeed a "similar application" that is opened, so what do you suggest I do. Please help...

---

### Post by oldos2er on 2011-12-04
You can only have one package manager open at a time. Do you have Synaptic, apt-get, Software Center, or something similar running?

---

### Post by Megalex on 2011-12-05
> **oldos2er said:**
> You can only have one package manager open at a time. Do you have Synaptic, apt-get, Software Center, or something similar running?

Hi Ann,

Thanks for replying. But that is what I am trying to tell, no "similar application" is opened when I am trying to do the upgrades. Muon is the only package manager installed in my Kubuntu.

One thing to note here is that the upgrades keep on appearing on the taskbar at the notifications area. Whenever I hit "Install updates" , that is when the error message appears.

---

### Post by oldos2er on 2011-12-05
Maybe there's something here that can help: [http://kubuntuforums.net/forums/index.php?action=printpage;topic=3119344.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3119344.0)

---

### Post by Megalex on 2011-12-06
> **oldos2er said:**
> Maybe there's something here that can help: [http://kubuntuforums.net/forums/index.php?action=printpage;topic=3119344.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3119344.0)

Yes, it worked. So the solution is:

Run sudo rm /var/cache/apt/archives/lock .

Then reboot.

Afterwards, run sudo dpkg --config -a .

You can now install the updates using Muon.

Thanks very much!

---

### Post by miluethi on 2012-02-14
> **Megalex said:**
> Yes, it worked. So the solution is:

Run sudo rm /var/cache/apt/archives/lock .

Then reboot.

Afterwards, run sudo dpkg --config -a .

You can now install the updates using Muon.

Thanks very much!
Still doesn't work for me.

---

### Post by miluethi on 2012-02-14
What helped for me - I installed the sudo apt-get install kubuntu-desktop after an initial installation of ubuntu is:

**sudo apt-get install polkit-kde-1**

According to this [website]("https://bugs.launchpad.net/ubuntu/+source/polkit-kde-1/+bug/867737") there is a bug the kubuntu-desktop dependencies that polkit-kde-1 will not get installed.

---

