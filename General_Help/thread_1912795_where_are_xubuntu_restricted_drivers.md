---
title: "where are xubuntu restricted drivers?"
date: 2012-01-21
forum: General Help
---

### Post by geovino on 2012-01-21
I've installed Xubuntu 11.10 64 bit. I had it installed last year and this time I can't find the xubuntu-restricted-drivers to install flash and libdvdcss and everything else to run multimedia. where did it go?

---

### Post by imachavel on 2012-01-21
system settings >
additional drivers

I think. What driver you want?? :popcorn:

---

### Post by geovino on 2012-01-21
> **imachavel said:**
> system settings >
additional drivers

I think. What driver you want?? :popcorn:

sorry not drivers, I'm talking about flash and libdvdcss and everything that runs multimedia. that all used to be in synaptic and now its gone.

---

### Post by raja.genupula on 2012-01-21
Hi this can help you
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by geovino on 2012-01-21
> **raja.genupula said:**
> Hi this can help you
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This is the command I was looking for:

sudo apt-get install ubuntu-restricted-extras

Thank you  :)

---

### Post by BlinkinCat on 2012-01-21
> **geovino said:**
> This is the command I was looking for:

sudo apt-get install ubuntu-restricted-extras

Thank you  :)

Are you sure you don't mean Xubuntu restricted extras? - :)

---

### Post by geovino on 2012-01-21
> **BlinkinCat said:**
> Are you sure you don't mean Xubuntu restricted extras? - :)

your right... is there much difference? I ran the ubuntu one and everything multimedia is working.

just ran the xubuntu restricted extras and this is the only additions:

davek@dave-xub:~$ sudo apt-get install xubuntu-restricted-extras
[sudo] password for davek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libffmpegthumbnailer4 tumbler-plugins-extra xubuntu-restricted-addons
The following NEW packages will be installed:
  libffmpegthumbnailer4 tumbler-plugins-extra xubuntu-restricted-addons
  xubuntu-restricted-extras
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 58.8 kB of archives.
After this operation, 340 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

just installed those so I should be OK.

---

### Post by BlinkinCat on 2012-01-21
There may be very little difference - sorry but I don't know.

But I do know I did the same thing when I was running xubuntu for a few months and did not encounter any problems - :)

---

### Post by raja.genupula on 2012-01-21
> **geovino said:**
> This is the command I was looking for:

sudo apt-get install ubuntu-restricted-extras

Thank you  :)

welcome man , please mark your thread as solved from thread tools.

---

