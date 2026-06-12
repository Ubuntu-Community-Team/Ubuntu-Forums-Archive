---
title: "When will GRUB 1.97 released version package come?"
date: 2009-11-08
forum: General Help
---

### Post by rajesh_shenoy on 2009-11-08
When will GRUB 1.97 released version package come to the Synaptics Package Manager / aptitude in Ubuntu 9.10 Karmic Koala?

Alternatively, does anyone know how to install GRUB 1.97 released version? The source code tarball is available for download, but I'd rather not go through the compile / make steps.

---

### Post by Plumtreed on 2009-11-08
There is some info here

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by rajesh_shenoy on 2009-11-09
Thanks for the reply, @Plumtreed. That's a very useful link, but unfortunately its not very helpful to my situation.

---

### Post by falconindy on 2009-11-09
Grub 1.97 was released on the 25th of October. I doubt you'll get any feedback as to when it'll be put in the repos. Typical answers to a question such as that are along the lines of "when its ready". Are you having problems with Beta4?

---

### Post by rajesh_shenoy on 2009-11-09
Thanks for the reply, @falconindy. No, I'm not having any problems so far (it's been 4 days since I installed Ubuntu 9.10). It's just that I was a little rattled to see a beta boot-loader in a released version of an OS. Makes me slightly nervous having a beta product in charge of such an important thing as the MBR.

---

### Post by phillw on 2009-11-09
> **rajesh_shenoy said:**
> Thanks for the reply, @falconindy. No, I'm not having any problems so far (it's been 4 days since I installed Ubuntu 9.10). It's just that I was a little rattled to see a beta boot-loader in a released version of an OS. Makes me slightly nervous having a beta product in charge of such an important thing as the MBR.

Hi,

Things Grub2 are looked after at the following areas  -->>   [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)  and [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743) and [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Should be able to answer any concerns / issues you have.

Regards,

Phill.

---

### Post by ranch hand on 2009-11-09
Your question is one that a lot of us would love the answer to.

There is a stable version available.  1.96.  1.97beta4 is, by far, better.

We started with 1.96 in Karmic testing at Alpha2.

I am excited about 1.97 being released into the repos.  I am not going to mess with it until it is though.  I want the Ubuntu devs to have a look at it first.  They may tweek it a bit for us.

Also, the real weakness of grub2 is os-prober.  I would like to see a new version or at least a couple of updates for it a lot more than 1.97.

---

### Post by phillw on 2009-11-09
> **ranch hand said:**
> Your question is one that a lot of us would love the answer to.

There is a stable version available.  1.96.  1.97beta4 is, by far, better.

We started with 1.96 in Karmic testing at Alpha2.

I am excited about 1.97 being released into the repos.  I am not going to mess with it until it is though.  I want the Ubuntu devs to have a look at it first.  They may tweek it a bit for us.

Also, the real weakness of grub2 is os-prober.  I would like to see a new version or at least a couple of updates for it a lot more than 1.97.


<< Big yellow streak down my back :lolflag:

I've not yet made the leap over to Grub2, nor ext4.

Got some more backing up to do before I let 9.10 have a 'clean' run on my computer, I did the upgrade & it isn't broken, so I'm in no rush to fix it :D

Phill.

---

### Post by falconindy on 2009-11-09
> **phillw said:**
> I've not yet made the leap over to Grub2, nor ext4.
I'll let you in on a little secret: Neither are worth the hassle of switching over to.

---

### Post by phillw on 2009-11-09
> **falconindy said:**
> I'll let you in on a little secret: Neither are worth the hassle of switching over to.


I'm going for the LTS on a new partition, as I have servers etc, set up my confused computer.  I'll let lucid lynx have fun, but keep my existing area. Besides, I quite like Shiretoko as my browser, I use a USB huweii modem for 3G connection to the internet. Hopefully I can help a little on nailing any problems.

Phill.

---

### Post by rajesh_shenoy on 2009-11-10
Thanks everyone for your replies. I finally managed to install GRUB 1.97 released version on my own. Needed an extra step to work around a bug in the "update-grub" command. Details here: [http://ubuntuforums.org/showthread.php?t=1317680](http://ubuntuforums.org/showthread.php?t=1317680)

Cheers!

---

### Post by ranch hand on 2009-11-10
See any difference?

---

### Post by rajesh_shenoy on 2009-11-10
Nope, none at all. But then I'm not a power user, so I guess I wouldn't really notice anything unless it's too obvious. The OS-prober functioned well and detected my Windows 7 partition. The GRUB menu itself looks a little tidier with slightly better font (I think!). Haven't tried the grub-splashimages feature yet.

The main reason I upgraded was that now I don't have a jarring "BETA" thrown in my face first thing every morning...! :)

Cheers!

---

