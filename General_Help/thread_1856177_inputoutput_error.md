---
title: "input/output error"
date: 2011-10-07
forum: General Help
---

### Post by mkr10001 on 2011-10-07
Can anyone help me with this?

Mounted an iso, it runs fine off the disc with no install but I get this error when I'm trying to install.
redownload?
[IMG]http://img828.imageshack.us/img828/9720/lubuntuerror.png[/IMG]

---

### Post by dcstar on 2011-10-08
> **mkr10001 said:**
> Can anyone help me with this?

Mounted an iso, it runs fine off the disc with no install but I get this error when I'm trying to install.
redownload?


Or actually follow the instructions presented to you.

---

### Post by claracc on 2011-10-09
> Or actually follow the instructions presented to you. 

+1

I pressume the problem is in the copied CD or DVD, first you have to compare the md5sum of the iso copied in your HD, then you burn the iso with the lowest as possible speed, then you have to check the data copied after burning.

---

### Post by SteveDee on 2011-10-09
> **claracc said:**
> +1

I pressume the problem is in the copied CD or DVD....


-1

It looks to me like you are mounting the iso in VirtualBox, not using a CD/DVD. Its possible that your downloaded iso is corrupt, but this input/output error has been a problem on some machines for at least 3 years. Changes to the hardware, such as removing RAM strips and CD drives, has worked in some cases: [https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/245794](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/245794)

I'm not sure if installing in a VM makes matters more complicated or less so. What you are trying to do should not be a problem (I run VirtualBox with several different images) but if you can lay your hands on another computer to test this under VirtualBox this may give you some clues.

---

