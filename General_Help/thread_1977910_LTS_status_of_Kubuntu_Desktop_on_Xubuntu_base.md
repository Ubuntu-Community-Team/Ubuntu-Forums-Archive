---
title: "LTS status of Kubuntu Desktop on Xubuntu base"
date: 2012-05-10
forum: General Help
---

### Post by KBD47 on 2012-05-10
Question, I installed Kubuntu Desktop onto Xubuntu 12.04 I decided I'd rather have Kubuntu but didn't want to reinstall all my favorite apps. Anyway, I know that Xubuntu 12.04 was a 3 year LTS, but since I've installed the Kubuntu desktop, is it still a 3 year LTS operating system, or are the sources changed with the Kubuntu desktop making it a Kubuntu 5 year LTS?
Thanks.
KBD47

---

### Post by Enigmapond on 2012-05-10
12.04 is a 5 year distro and will be supported until 2017 it doesn't matter which version you choose..12.04 is still 12.04 so  relax/enjoy.

Cheers!

---

### Post by Bucky Ball on 2012-05-10
> **Enigmapond said:**
> 12.04 is a 5 year distro and will be supported until 2017 it doesn't matter which version you choose..12.04 is still 12.04 so  relax/enjoy.

Cheers!

Actually, Xubuntu 12.04 LTS is still only supported for three years, much to my dismay (I am a big fan and use it on all my machines).

One point; it is the OS that has long-term support, *not* the desktop environment, if you follow. If you're talking kubuntu-desktop installed on an Xubuntu, Xubuntu is supported for three years, regardless of what packages you have running on it. *It is t**he actual OS you are using* which will reach end-of-life.

---

### Post by KBD47 on 2012-05-10
I wonder if the sources can be changed to make it 5 years instead of 3? I wonder what makes the difference? It would have to be the sources wouldn't it? Seems like I could just change all the sources to Kubuntu from Xubuntu.

Would this work?

sudo apt-add-repository ppa:kubuntu-ppa/ppa sudo apt-add-repository ppa:kubuntu-ppa/backports sudo apt-get update sudo apt-get dist-upgrade
Thanks!

---

### Post by 3Miro on 2012-05-10
Lubutu decided to make this a regular 18 months release. I guess Xubuntu went for the 3 years. Actually, it makes sense. The long term support is cost that has to be offset by gain and only vanilla Ubuntu has a chance of real tangible gain via wide spread enterprise adoption. Very few regular users would use 12.04 for longer than say 3 years (next LTS is scheduled for 14.04).

---

### Post by Bucky Ball on 2012-05-10
> **3Miro said:**
> Lubutu decided to make this a regular 18 months release. I guess Xubuntu went for the 3 years. Actually, it makes sense. The long term support is cost that has to be offset by gain and only vanilla Ubuntu has a chance of real tangible gain via wide spread enterprise adoption. Very few regular users would use 12.04 for longer than say 3 years (next LTS is scheduled for 14.04).

Define a 'regular user'? ;)

---

### Post by KBD47 on 2012-05-10
I had this same question regarding Lubuntu 12.04 awhile back. If the repositories are all set to precise and precise universe and precise security--what the heck makes the other releases only 18 mos and 3 years respectively? If it is that the Lubuntu and Xubuntu people stop sending updates that are specific to those desktops (LXDE & Xfce) and the apps specific to the desktops, what would keep theose distros from getting security updates? And other updates if Kubuntu or Unity was installed on top of them?

---

### Post by 3Miro on 2012-05-10
> **Bucky Ball said:**
> Define a 'regular user'? ;)

Non corporate, i.e. something someone may have at home as opposed a corporate owned machine intended for low cost, low maintenance and the bare minimum features to get the work done.

---

### Post by KBD47 on 2012-05-10
I'm kind of surprised at the numerous posts I've read on Ubuntu forum from those who seem shocked at the idea a home computer user would want to keep an OS on their machine for 5 years. People are still using XP over a decade later. 5 years is not so long for those who don't like to change the OS, and computers have a pretty long shelf life.

---

### Post by Bucky Ball on 2012-05-11
> **KBD47 said:**
>  5 years is not so long for those who don't like to change the OS, and computers have a pretty long shelf life.

+1. And the older, generally the more stable the release is. That's what I require. ;)

---

### Post by lykwydchykyn on 2012-05-11
There's a lot of confusion around the different Ubuntu versions having different LTS lengths.

It basically amounts to this:

 - The repositories are the same for all the major Ubuntu respins (K/X/L/U)
 
 - "Support" means the availability of new security updates and bugfixes
 - The *core packages* of the OS are maintained by Ubuntu, and will be supported for 5 years.

 - Packages specific to a respin (say, the KDE packages) are maintained by that project, and will only be kept up for that many years.

So, for example, if you want to run Lubuntu for 5 years, you will still get updates for the kernel and other core software -- basically, any component that's also used by regular Ubuntu.  But you probably won't get LXDE updates after 18 months.

Make sense?

---

### Post by KBD47 on 2012-05-11
> **lykwydchykyn said:**
> There's a lot of confusion around the different Ubuntu versions having different LTS lengths.

It basically amounts to this:

 - The repositories are the same for all the major Ubuntu respins (K/X/L/U)
 
 - "Support" means the availability of new security updates and bugfixes
 - The *core packages* of the OS are maintained by Ubuntu, and will be supported for 5 years.

 - Packages specific to a respin (say, the KDE packages) are maintained by that project, and will only be kept up for that many years.

So, for example, if you want to run Lubuntu for 5 years, you will still get updates for the kernel and other core software -- basically, any component that's also used by regular Ubuntu.  But you probably won't get LXDE updates after 18 months.

Make sense?

Yes, that makes perfect sense and is exactly what I thought--thank you!
  I even added the Kubuntu specific ppa so my hybrid Xubuntu with the Kubuntu desktop should have the 5 years LTS on the Ubuntu and Kubuntu specific areas.
Thanks again.
KBD47

---

