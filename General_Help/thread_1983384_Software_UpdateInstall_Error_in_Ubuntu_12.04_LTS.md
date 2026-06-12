---
title: "Software Update/Install Error in Ubuntu 12.04 LTS"
date: 2012-05-20
forum: General Help
---

### Post by merkav on 2012-05-20
Hi,

Recently I have installed Ubuntu 12.04 LTS (Precise Pangoline) on my newly bought Lenovo Thinkpad E420. I have downloaded the installer from [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)   and I really like the look and functionality. 

After that I have installed quite a few necessary softwares through Ubuntu software Centers e.g. gimp, kile, adobe flash player, audacious, LinuxDc++, vlc, chrome, adobe acrobat reader etc. But after that, whenever I am trying to update 12.04 LTS through **available update option**, I am getting the following error message:

[IMG]http://s14.postimage.org/e39og2kvl/Screenshot_from_2012_05_20_17_11_23.jpg[/IMG]

Or, whenever I am trying to install some software through **Ubuntu Software Center**/ by running **sudo apt-get install** command, I am getting stuck.

Please help me to get rid of the problem as soon as possible. I have some assignment coming up and I really need to install some necessary softwares and I really don't want to quit ubuntu.

---

### Post by zvacet on 2012-05-20
You can do upgrades in two ways:

1. in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

2. install synaptic

```
sudo apt-get install synaptic
```

open synaptic and click on refresh and after that on mark all updates.

---

### Post by 2F4U on 2012-05-20
What mirror do you use? Does the behaviour change if you use a different mirror?

---

### Post by Easy Limits on 2012-05-20
The servers were having some issues all weekend up till now.  You may try re-booting.  Re-booting took care of a similar problem I was having.

---

### Post by merkav on 2012-05-21
Hi All,

Being frustrated after trying different solutions suggested over internet, I decided to re-install 12.04 LTS. Now, the problem is I am not able to install any software through Software Center. The mirror is:

[IMG]http://s18.postimage.org/d5iy7oxpl/Screenshot_from_2012_05_21_10_20_34.png[/IMG]

I tried to install synaptic, but the error is:

[COLOR=Red]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate[/COLOR]


Please,  please help me. I am going mad....

---

### Post by merkav on 2012-05-21
Whenever I am trying to install a software through Software Center, it is getting queued, but displaying :

[IMG]http://s14.postimage.org/c1kl74cip/Screenshot_from_2012_05_21_10_33_25.png[/IMG]

and finally the error message is:

[COLOR=Red]Failed to download repository information [/COLOR]

---

### Post by zvacet on 2012-05-21
In Ubuntu software center >edit<software repositories>updates tab check first two and refresh.After that

```
sudo apt-get install synaptic
```

I prefer to install with synaptic.You can even keep your system up-to-date with synaptic.Click on refresh and after that on mark all updates. ;)

---

### Post by sikander3786 on 2012-05-21
> **merkav said:**
> [COLOR=Red]Failed to download repository information [/COLOR]

From Terminal, please post the _complete_ output of this command:

```
sudo apt-get update
```

---

