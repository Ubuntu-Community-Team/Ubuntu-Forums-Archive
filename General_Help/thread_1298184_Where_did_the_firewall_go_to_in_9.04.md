---
title: "Where did the firewall go to in 9.04?"
date: 2009-10-22
forum: General Help
---

### Post by benali72 on 2009-10-22
Hi,

I've been using 8.04 for a while, and recently installed 9.04 into a new partition.

Where is the firewall in 9.04?  I can't seem to find either "firestarter" or "firewall" when I use "Applications->Add/Remove" or the Synaptic Package Manager.

Thank you.

---

### Post by Aero-Z on 2009-10-22
> **benali72 said:**
> Hi,

I've been using 8.04 for a while, and recently installed 9.04 into a new partition.

Where is the firewall in 9.04?  I can't seem to find either "firestarter" or "firewall" when I use "Applications->Add/Remove" or the Synaptic Package Manager.

Thank you.
It's probably UFW now. The gui for it is named gufw.

---

### Post by ubuntu27 on 2009-10-22
See:
[UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by rampageoberon on 2009-10-22
> **benali72 said:**
> Hi,

I've been using 8.04 for a while, and recently installed 9.04 into a new partition.

Where is the firewall in 9.04?  I can't seem to find either "firestarter" or "firewall" when I use "Applications->Add/Remove" or the Synaptic Package Manager.

Thank you.

Hi,

The firewall is still there. The likes of gufw, ufw, firestarter etc are frontends for the netfilter/iptables firewall.

Hope that answers your question. As suggested in an earlier post you could use gufw, ufw etc to configure the firewall if you don't want to use iptable commands.

---

### Post by benali72 on 2009-10-22
Thank you, everyone, for your help.  I enabled the automatically-installed firewall thru the UFW command on the command line.

I hope this doesn't sound presumptuous or negative in some way, but I believe --

1.  The firewall should be ENABLED by default
2.  The GUFW GUI also be installed by default and easily accessible 
    via the Applications menu

Shipping to end users with a firewall off could really cause a black eye someday for Ubuntu.  Please, Ubuntu gods, reconsider this decision!

----details from my session---

bcs@user-desktop:~$ sudo ufw status
Status: inactive
bcs@user-desktop:~$ sudo gufw
sudo: gufw: command not found
bcs@user-desktop:~$ gufw
The program 'gufw' is currently not installed.  You can install it by typing:
sudo apt-get install gufw
bash: gufw: command not found
bcs@user-desktop:~$ sudo apt-get install gufw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gufw
bcs@user-desktop:~$ sudo ufw enable
Firewall is active and enabled on system startup
bcs@user-desktop:~$ 

--- I could not find GUFW in Add/Remove (within All Applications) nor in Synaptic PM.  (I did see that Synaptic shows UFW already installed).

Thanks again, everyone, for your help.

---

