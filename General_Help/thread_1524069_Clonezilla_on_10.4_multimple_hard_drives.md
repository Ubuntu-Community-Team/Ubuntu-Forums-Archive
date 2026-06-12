---
title: "Clonezilla on 10.4 multimple hard drives"
date: 2010-07-04
forum: General Help
---

### Post by zeta_immersion on 2010-07-04
Hi everyone, I have researched this and came up empty and I hope someone may know the answer.

I have installed Ubuntu 10.4 worked fine, and Clonezilla (including configuring it) -- (though my /etc/networking/interfaces seems to give an error in line 2 I have the following questions)

I have installed a second Hd (250Gb) ... and I have formatted it with gparted so it mounts fine and I am able to see it ... is there any way to make it a permanent mount and have Clonezilla use it to store images on it? ... The first HD was formatted LMV during the Ubuntu installation.
Thank you.

---

### Post by howefield on 2010-07-04
> **zeta_immersion said:**
>  have installed Ubuntu 10.4 worked fine, and Clonezilla (including configuring it) -- (though my /etc/networking/interfaces seems to give an error in line 2 I have the following questions)

Not sure what you mean here, how do you install Clonezilla ?

> I have installed a second Hd (250Gb) ... is there any way to make it a permanent mount and have Clonezilla use it to store images on it? ...

What file system have you formatted it with ? If it is a linux file system you'll be able to add it to your fstab. 

Clonezilla will be able to use it to store images of your other drive.

---

### Post by zeta_immersion on 2010-07-04
What I did was install ubuntu server. (nnote 2 disks 250gb each)

1. First I installed Ubuntu server (used entire disk as VLM and partitioned it in 20Gb .. the rest not sure where it went)

2. Went into /etc/networking/interfaces and added static eth0

3. Updated packages and then grabbed the key for clonezilla (ie: wget -q [http://drbl.sourceforge.net/GPG-KEY-DRBL](http://drbl.sourceforge.net/GPG-KEY-DRBL) -O- | sudo apt-key add -) and installed it ... in the end using impacient script)

4. Went back into /etc/networking/interfaces and made eth1 (static) *DNS*
after which internet stopped working ... saying error in line 2 

5. Added 2nd drive and used gparted formatting it ext3, flag VLM and mounts fine 

the problem I am having is how to make the second drive detectable by clonezilla so it knows to use it as a storage drive for images?

Thanks for your help

---

