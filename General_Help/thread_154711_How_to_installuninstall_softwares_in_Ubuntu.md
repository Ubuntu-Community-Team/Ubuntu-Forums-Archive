---
title: "How to install/uninstall softwares in Ubuntu?"
date: 2006-04-03
forum: General Help
---

### Post by tico on 2006-04-03
Well, I know we have Synaptic and Automatix, but this is hot enough. I like to learn to install/uninstall any software in Ubuntu. What are the parameters, commands etc.?
Using Automatix, I've installed  Skype and OpenOffice. But Automatix installed Skype 1.2 and there's a newer one (2.0). It upgraded the original OpenOffice to 2.0.1, but there's a newer one (2.0.2). So, how can I uninstall these versions and get/install the newer ones? Let's say: if I go to Mozilla and download a test version of Firefox, how I'm supposed to install it (after having uninstalled the previous one or installing in another path)?

---

### Post by taurus on 2006-04-03
If you download the source, you first need to unpack it and build it.  And before you build it, you HAVE to read the README and/or INSTALL since it will tell you how to build it...

---

### Post by tico on 2006-04-03
[QUOTE=taurus]If you download the source, you first need to unpack it and build it.  And before you build it, you HAVE to read the README and/or INSTALL since it will tell you how to build it...[/QUOTE]

But how could I uninstall the previous versions before installing the new ones?

---

### Post by towsonu2003 on 2006-04-03
[QUOTE=tico]Let's say: if I go to Mozilla and download a test version of Firefox, how I'm supposed to install it (after having uninstalled the previous one or installing in another path)?[/QUOTE]
see wiki.ubuntu.com/FirefoxNewVersion
See the "dirty install instructions" to try out test versions, but be careful, it will use your firefox (and may break it, so backup your ~/.mozilla/firefox directory)

Usually, installation instructions are on programs' web sites. And usually, they are not enough ;) so you'll have to search the forums. 

For openoffice, I used their installer in Slackware and it worked without any problems. But it may be different for ubuntu/linux: there is a repository around here somewhere for latest openoffice though (search forum). You add it to your sources.list and apt-get upgrade does the rest... 

My notes:
1. Unless I am sure I DO need new features (openoffice) or bug fixes (firefox), I do NOT install newer versions (from non-synaptic resources or source). 
2. I use emulation (qemu, vmware player) to make sure the installation I will do is not going to break my ubuntu (usually they don't)
3. I search the forums
4. I post question about specific program (how to install <package> <version>)
5. I give it a try. Have backups. 
X. This is so hard for us, because we are just trying to re-learn how to use a computer.. We'll get used to it :)

---

### Post by towsonu2003 on 2006-04-03
[QUOTE=tico]But how could I uninstall the previous versions before installing the new ones?[/QUOTE]
from synaptic. don't care about ubuntu-desktop being uninstalled, but there should be no other packages that will be uninstalled.

---

### Post by siminone on 2006-04-03
Just go into Synaptic and mark them for removal.

Apart from firefox and skype, I wouldn't recommend trying to install new versions of software as most of packages that come with current version of Ubuntu are mostly up to date (well apart from firefox) and new versions will have only minor additions.

These are a pain to install from source as most of the bigger package will have dependencies and these might be newer than the ones with Ubuntu which means you have to install them. These dependencies might also have newer dependencies... Get the picture?

The best bet is to try and install a debian version (.deb) although this is risky as if it has newer dependencies it will break Synaptic.

I've done a search and this link tells you how to install firefox 1.5

[http://www.ubuntuforums.org/showthread.php?t=151702&highlight=firefox+1.5](http://www.ubuntuforums.org/showthread.php?t=151702&highlight=firefox+1.5)

---

### Post by tico on 2006-04-03
[QUOTE=towsonu2003]
2. I use emulation (qemu, vmware player) to make sure the installation I will do is not going to break my ubuntu (usually they don't)[/QUOTE]

Well, how could I use qemu, vmware etc? I can't even use wine...
Does anybody could explain me how to install Win softwares into wine and use them the way Win does?

---

### Post by towsonu2003 on 2006-04-03
[QUOTE=tico]Well, how could I use qemu, vmware etc? I can't even use wine...
Does anybody could explain me how to install Win softwares into wine and use them the way Win does?[/QUOTE]
Usually, wine doesn't work for programs I want. So,
For qemu: [http://ubuntuforums.org/showthread.php?t=39513&highlight=qemu](http://ubuntuforums.org/showthread.php?t=39513&highlight=qemu) you wanna start with "Step 1. RUNNING QEMU WITH KQEMU ACCELERATOR" but keep in mind this is for hoary (so adjust your steps as you need)
For vmware: [http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware+howto](http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware+howto)
[http://www.ubuntuforums.org/showthread.php?t=122894&highlight=vmware+howto](http://www.ubuntuforums.org/showthread.php?t=122894&highlight=vmware+howto)

I prefer qemu (compiled from source with accelerator) for now bc I can mount the images with it. but vmware seems to be a little faster. Both are slow (no playing games, sorry) compared to the real thing. And I keep having "activation" problems (30 days and Windows is gone) with both. I think people actually call Microsoft to activate their emulated Windows. 

Note that you will need to do some reading and "commanding" as you go tru the posts. Once you set it up, it's pretty much straight forward.

---

