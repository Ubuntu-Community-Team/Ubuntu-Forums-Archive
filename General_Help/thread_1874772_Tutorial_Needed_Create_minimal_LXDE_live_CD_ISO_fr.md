---
title: "Tutorial Needed: Create minimal LXDE live CD ISO from ubuntu-mini-remix-?-i386.iso"
date: 2011-11-03
forum: General Help
---

### Post by Pierre16 on 2011-11-03
I just saw your tutorial: Modest Spec or Barebone Installation of Ubuntu.  It is great and even greater that it is up to date.

It is almost exactly what I need but instead of installing, I would like to create a live CD with minimal LXDE.  I have been able to create an ISO with UCK and Customizer but both fail to boot.  I am able to chroot and install lxde (sudo apt-get install lxde --no-install-recommends).  

UCK tells me that I have to edit boot scripts to tell the system how to boot but I have no idea how to do this.  Neither do they.  
[https://bugs.launchpad.net/uck/+bug/885491](https://bugs.launchpad.net/uck/+bug/885491)

The Customizer iso gets a kernel panic error at the Ubuntu .... splash and they have given up on trying to fix the problem.  I am stuck.
[https://sourceforge.net/apps/phpbb/u-customizer/viewtopic.php?f=3&t=17&p=64#p64](https://sourceforge.net/apps/phpbb/u-customizer/viewtopic.php?f=3&t=17&p=64#p64)
Everybody has given up!

More and more people are getting into creating their own distros, and  LXDE is very popular these days... It would be fantastic if you could provide a tutorial on how to create a minimal LXDE live CD from the Ubuntu-mini-remix, one that would also tell people what boot script to edit and how.

I have been producing the [Quelitu Lightweight OS ISO]("http://wavesofthefuture.net/computers/linux-operating-system-refurbish-computer-free.shtml") from the Lubuntu ISO but would like to build directly from a minimal LXDE installation now.

Any help for my problem in the meantime?

What you do is great.  I hope you can help me and others.

Thanks.

---

### Post by aysiu on 2011-11-03
This was originally posted in the Psychocats Tutorials Updates thread, but this is a bit beyond me and seems to be a request for help.

I'm hoping someone with some knowledge about this can help out here.

---

### Post by Paddy Landau on 2011-11-03
I'm no expert, but if you want LXDE, maybe you can save yourself plenty of bother and get a lightweight Ubuntu distro by simply creating a Live CD (or USB) with [Lubuntu]("https://wiki.ubuntu.com/Lubuntu").

Lubuntu is an official member of the Ubuntu family, but it is lightweight (runs well even on very old computers) and uses LXDE. I run it on my old machines, which would otherwise have gone to recycling.

It's worth a try, unless I have misunderstood your requirements.

---

### Post by JC Cheloven on 2011-11-03
Hi, I'm not sure to completely understand your issue, but It seems to me that all you need is a tool like remastersys. The main developer (known as Fragadelic) has recently continued its development after discontinuing it for a while, which is excellent news :)

Here are some links that may point you in the right direction:
[Main announcement]("http://www.remastersys.com/forums/index.php?PHPSESSID=jbeubenbnlslblasdmcaqups51&topic=1742.0")
[Remastersys post related to your specific problem]("http://www.remastersys.com/forums/index.php?PHPSESSID=jbeubenbnlslblasdmcaqups51&topic=1757.0")
[Post of the author here at ubuntu forums]("http://ubuntuforums.org/showthread.php?t=1870607"). Also containing references to minimal lxde install of recent ubuntu.

Hope that helps

---

### Post by Pierre16 on 2011-11-04
I have been using Lubuntu but there are issues and would like to try to build from scratch (mini-remix + lxde).  

I just posted on Remastersys.  Thanks for the information.  The problem is that you have to install the OS with Remastersys.  UCK and Customizer let you edit the iso directly, which is much better.

According to UCK, all I need to do is to tell the boot script to use lxde as default desktop session.

Please, keep the answers coming... I am still looking for a solution.

Thanks everyone!

---

