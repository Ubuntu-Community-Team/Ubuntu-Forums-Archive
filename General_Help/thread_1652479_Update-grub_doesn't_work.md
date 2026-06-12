---
title: "Update-grub doesn't work"
date: 2010-12-24
forum: General Help
---

### Post by whitewolf573 on 2010-12-24
I have installed ubuntu and Centos 5 , but when i do sudo update-grub , the new centos 5 is not detected. Some days ago i did the same ( i installed ubuntu , and then Centos 5 ) , but i had to format the hard disk because some problems i had.

The thing is that in that first time update-grub worked , but now not , why ?

Shouldn't be detected this time too ? 

I have to manually add the new entry to the grub no ?

( I have found a guide about grub2 , so i think i will read it :) )

---

### Post by efflandt on 2010-12-24
It is not wise to have more than one grub boot loader in the same place (like both trying to use the mbr).  Otherwise if they both fight over the same one, one may step on the other.

You can put grub on a primary Linux partition, it will complain, but works with standard mbr and and that partition marked as boot partition in partition table. So it should work chainloaded from whatever CentOS uses for a boot loader, if it cannot boot Linux directly.  Although, I am not sure if it would work with grub on an extended or logical partition.

What does **sudo os-prober** show from Ubuntu?

---

### Post by garvinrick4 on 2010-12-24
When installing Centos It is a RedHat cousin so would be anaconda installer and will have
a little box that you can check or uncheck that says do not install grub at all. Use it and install 
the Ubuntu grub2 to sda and then sudo update-grub and you will get a clean dual boot. 
 All the Fedora's, openSuse, Redhat, Centos use grub-legacy and anaconda as installer software. 
I like the do not install any grub selection in anaconda.

---

### Post by whitewolf573 on 2010-12-25
> **garvinrick4 said:**
> When installing Centos It is a RedHat cousin so would be anaconda installer and will have
a little box that you can check or uncheck that says do not install grub at all. Use it and install 
the Ubuntu grub2 to sda and then sudo update-grub and you will get a clean dual boot. 
 All the Fedora's, openSuse, Redhat, Centos use grub-legacy and anaconda as installer software. 
I like the do not install any grub selection in anaconda.

I think I choosed to install centos boot to his partition. Like I did the first time. So it is better to not install any grub at all in centos and then do update-grub in ubuntu.

---

### Post by garvinrick4 on 2010-12-25
Yes, install no grub at all and then after install boot into Ubuntu and update-grub and 
grub2 will put in config files and boot menu for you and you got a nice working system.
grub2 and grub-legacy do not play together well at all. Merry Christmas partner.

---

