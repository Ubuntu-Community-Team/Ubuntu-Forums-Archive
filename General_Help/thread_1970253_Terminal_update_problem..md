---
title: "Terminal update problem."
date: 2012-05-01
forum: General Help
---

### Post by chrissy.millichamp on 2012-05-01
I have Ubuntu 12.04 , and whenever I run sudo apt-get update I get this message saying this, W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
What do u think that could solve the problem?

---

### Post by oboedad55 on 2012-05-01
> **chrissy.millichamp said:**
> I have Ubuntu 12.04 , and whenever I run sudo apt-get update I get this message saying this, W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
What do u think that could solve the problem?

Go to /etc/apt and edit sources.list to remove or comment out the duplicate entry. Or us Synaptic to do the same.

---

### Post by chrissy.millichamp on 2012-05-01
Firstly, how do u enter the sourcelist in order to edit it?

---

### Post by oboedad55 on 2012-05-01
> **chrissy.millichamp said:**
> Firstly, how do u enter the sourcelist in order to edit it?

Either install Synaptic and go to the repositories and edit there. Or install nano and do it from the command line. Go to /etc/apt and do "nano sources.list". Remove the duplicate entry and then cntrl-x and save. Then do sudo apt-get update. You'll have to do these commands with sudo.

---

