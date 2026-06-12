---
title: "recommended partition size for / ?"
date: 2010-01-23
forum: General Help
---

### Post by pepe machine on 2010-01-23
hello everyone, title says it all

what is the recommended partition size for / ??

i have installed my ubuntu in my laptop (has 320G hard drive) with this partitions:
80G for /
237G for /home
3G for swap

did i partition it correctly??

i thought that applications would be installed in / but i was wrong, instead applications were installed in /home.. (are my observations correct??)

now im thinking of reformatting again and make / a little bit small.

please recommend me partition size for / , /home, and swap

---

### Post by audiomick on 2010-01-23
Hallo.
Yes, your / is bigger than it needs to be. I observed on a newly installed system recently that / had only around 2.7GB in it. Mine has a bit over 6 GB in it after a few years and a few upgrades.

Your / will grow with time, so it does want a bit of elbow room.

General opinion seems to be

10 - 15 GB for /
Swap a fraction bigger than your RAM if you want hibernate to work. Hibernate writes the contents of the RAM to the swap space
/home the rest of the space.

edit: Applications are stored in / , but I don't know exactly were. User settings are stored in /home.

---

### Post by falconindy on 2010-01-23
If you keep a lean installation and get in the semi-regular habit of cleaning up cruft (unused programs, ancient log files, dl'ed packages), then you should never need more than 20g for your /. I keep an extremely lean root partition that just recently surpassed 3GB.

Your observations are incorrect. System applications are installed to /bin and /sbin. User installed applications via a package manager are in /usr/bin and /usr/lib. If you're so inclined, manually compiled applications will end up in /usr/local/bin and /usr/local/lib.

More info: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by pepe machine on 2010-01-24
thanks a lot guys.. ^^

---

### Post by HereInOz on 2010-01-24
Regarding the swap partition, the conventional wisdom is twice your RAM size, but, being unconventional, I have never been able to work out why that would be the case.  Consider:

If you have 4 GB RAM, and use your machine for general purposes, the likelihood of you ever using the swap partition is almost nil.  (Linux isn't like Windows in this regard). 

So you could actually get away with a small 1GB swap partition (2 x RAM = 8GB would be overkill) and all would be rosy. However, if you only have 512MB RAM, then the possibility of running into the swap partition is quite high, and you could find that 2 x RAM = 1GB is just inadequate.

I run a couple of virtual machines, and I like to have at least 6GB af total system memory available.  Probably a bit much for you, but if you made your RAM plus the swap = 4GB total, you would probably be well and truly covered. 

You have plenty of HDD space, so the swap file could happily be 4GB and no one would notice.  You will never use it all, but it will be nice to have.

---

### Post by Ordes on 2010-01-24
yo.. as others mentioned.. 10-20 gb should be enough for "/". on my home-file server i just have 10gb. on my main machines i use 15gb..

for swap, i prefer to have my total ram about 8gb. 4gbram, 4gb swat. its more than i ever need. but on the hdd-sizes we have these days i dont really miss 4gb :)

applications are installed in "/". what u oberserved that they get installed in "home" is not the application, but the user settings /configs for the applications.

btw, u probably dont need to reformat. u should be able to shrink "/" with using gparted

---

### Post by dcstar on 2010-01-24
> **HereInOz said:**
> Regarding the swap partition, the conventional wisdom is twice your RAM size, but, being unconventional, I have never been able to work out why that would be the case.


[http://ubuntuforums.org/showpost.php?p=2528643&postcount=2](http://ubuntuforums.org/showpost.php?p=2528643&postcount=2)

---

### Post by aldaeron on 2011-09-16
David I read your linked post regarding swap size.

My question is how small can I make my swap size?

I have 24 GB RAM and a 120 GB SSD that I don't want to waste space for swap on.  Windows bloats up the SSD already.  Will 1GB suffice? 2 GB?

Thanks!

---

### Post by Elfy on 2011-09-16
> **aldaeron said:**
> David I read your linked post regarding swap size.

My question is how small can I make my swap size?

I have 24 GB RAM and a 120 GB SSD that I don't want to waste space for swap on.  Windows bloats up the SSD already.  Will 1GB suffice? 2 GB?

Thanks!

Always best to not tack onto another thread especially an old one. 

You can always install without swap if you wish - no hibernate though.

If you need further help then start a thread.

Closed

---

