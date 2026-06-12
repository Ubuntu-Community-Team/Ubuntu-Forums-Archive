---
title: "updates from local server"
date: 2010-12-22
forum: General Help
---

### Post by gnulab on 2010-12-22
Hi guys,

I'm migrating 3 laptops that were installed with Windows XP to Ubuntu, after all they're using Words & Excel primarily.

However, I'm facing the problem of slow internet, thus software, such as Skype, need to be downloaded 3 times, is wasting quite a lot of my time. Security updates for Ubuntu 10.10, each totalling to 200mb has to be downloaded 3 times.

So, I'm thinking of download it once, put it in my NAS, share the folder, then each laptop will only need to point to the shared directory in order to install updates & softwares.

Is that possible? And how do I go about doing that? If such an article or thread has been posted, could you point me to that link?

Currently, I do the beginner fool method, download everything 3 times. :(

Thank you.
Henry

---

### Post by Verbeck on 2010-12-22
if the same os is installed on all 3 machines and all have the same software sources, then copy all the .debs in /var/chache/apt/archives from one computer to the next after a full update

then just use synaptic/update manager normally to install programs/updates

---

### Post by Ghost_Mazal on 2010-12-22
Another way is to install the software AptonCd on the pc with all the software. That can burn for you a disc with all the downloaded and installed apps on it.

If the other two pc's are the same OS you can install it using that disc.

A third way is to us remastersys. That will make an bootable installable iso that will give you like your own distro with all the apps on it that you can install on new pc's.

---

### Post by gnulab on 2010-12-22
> **Ghost_Mazal said:**
> Another way is to install the software AptonCd on the pc with all the software. That can burn for you a disc with all the downloaded and installed apps on it.

If the other two pc's are the same OS you can install it using that disc.

A third way is to us remastersys. That will make an bootable installable iso that will give you like your own distro with all the apps on it that you can install on new pc's.

The 2nd method is more practical than the 3rd one.

The 3rd one means one will be copying from scratch, from OS to data files, I reckon this method takes up more time than the 2nd method.

---

### Post by Ghost_Mazal on 2010-12-22
> **gnulab said:**
> The 2nd method is more practical than the 3rd one.

The 3rd one means one will be copying from scratch, from OS to data files, I reckon this method takes up more time than the 2nd method.

Not if you know you gonna do it beforehand before you install OS. Then OS and apps is all installed at once. Faster than installing OS and then apps.

If OS is already installed then nr 2 is best yes.

---

### Post by gmargo on 2010-12-22
Install the **apt-cacher-ng** caching proxy package on one machine and configure all of the machines to point through it.  Everything of current value is cached and available to the next requester.

[http://packages.ubuntu.com/maverick/apt-cacher-ng](http://packages.ubuntu.com/maverick/apt-cacher-ng)

---

### Post by gnulab on 2011-01-05
> **Ghost_Mazal said:**
> Not if you know you gonna do it beforehand before you install OS. Then OS and apps is all installed at once. Faster than installing OS and then apps.

If OS is already installed then nr 2 is best yes.

My previous experience with Windows XP is that I can't do that if the machines are of different hardware. Say the wireless hardware in 1 laptop is Atheros and the other is Broadcom. After installing from the CD, it will result in BSoD (Blue Screen of Death).

Is Ubuntu tolerant if it is different hardware?

Thank you.
Henry

---

### Post by Ghost_Mazal on 2011-01-05
Yes. Ubuntu is very good at that. Not like Windoze.

And (seeing as you qouted my post) with a remstersys iso you do a fresh install (with all software and updates added) so it picks up the hardware during the install anyway.

---

