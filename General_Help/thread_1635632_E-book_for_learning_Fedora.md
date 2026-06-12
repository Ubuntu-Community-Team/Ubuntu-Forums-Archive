---
title: "E-book for learning Fedora"
date: 2010-12-02
forum: General Help
---

### Post by satish_j on 2010-12-02
I have recently downloaded Fedora 14 iso file and going to triple boot my system with XP and Ubuntu.Since Fedora is red hat distribution and Ubuntu is debian-based,iam looking for some good e-book for learning fedora 14.
Any Inputs??

---

### Post by garvinrick4 on 2010-12-02
#One thing I can tell you is do not install grub when install Fedora, their is a spot in the install of anaconda that lets you choose by a check mark I believe not to install any grub
at all. Then go into Ubuntu after install and sudo update-grub Ubuntu and will put in grub2
# Fedora uses grub legacy and just is so much simpler not to get involved with both in one system
[my-guides.net]("http://www.my-guides.net/en/") 
[Main Page -]("http://ubuntuguide.org/wiki/Main_Page") 
#Here are two just find the fedora section and use the post installation guides to install.
On the use of yum vs. apt-get and the RPM usage I googled alot while learning the different terminal usage. Never did quite find a pdf book to keep handy like the Ubuntu ones out there. Post installation is about same from 12 to 14 so use what is good for you.

---

### Post by satish_j on 2010-12-02
> **garvinrick4 said:**
> 
# Fedora uses grub legacy and just is so much simpler not to get involved with both in one system
Thanks for this helpful hint..I assume that if i do not allow anaconda to install Grub,Grub2 will be used(which has been installed with Lucid at first place)AND WHICH WILL AUTO-DETECT FEDORA.AM I RIGHT?..obvioulsy after running 'sudo update-grub'..

---

### Post by garvinrick4 on 2010-12-02
> **satish_j said:**
> Thanks for this helpful hint..I assume that if i do not allow anaconda to install Grub,Grub2 will be used(which has been installed with Lucid at first place)AND WHICH WILL AUTO-DETECT FEDORA.AM I RIGHT?..obvioulsy after running 'sudo update-grub'..
Yes, os-prober will find it and put it in your grub2, exactly right.

---

