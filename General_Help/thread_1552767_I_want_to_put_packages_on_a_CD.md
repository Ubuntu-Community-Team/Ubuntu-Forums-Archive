---
title: "I want to put packages on a CD"
date: 2010-08-14
forum: General Help
---

### Post by Cherry Cotton on 2010-08-14
Hey-o, all! I want to install Ubuntu on my girlfriend’s computer, but I also want to install some additional packages she’d like, like GIMP. Trouble is, she doesn’t have an Internet connection on her computer. I knew of AptOnCD, and tried to use that, but that program hasn’t been updated in a long time and seems very unreliable for pulling dependencies (select “gimp” and it will fail to select “gimp-data” and so on even if you’ve checked “auto-select dependencies,” for instance).

So, I’d like some way to pull whatever packages I want, and all associated dependencies, and put them on my girlfriend’s computer. My strong preference would be to do this by making a CD repository from which I could install packages to her computer using Synaptic. Reasons for this include: #1. I don’t think her computer even has an Ethernet card, so networking is out, and #2. I don’t know if her computer even has any USB ports, so flash drives are out. (Making a custom install CD is also out, because that’s way more sophisticated than I’d trust myself with.)

Further motivation: until I do something, her raggedy old computer is stuck using Windows 2000. I want to rescue my girlfriend from this fate, and make a show of my nerd devotion to her. Please help me, fellow Ubuntunauts! Thank you!

---

### Post by Elfy on 2010-08-14
try keryx

[http://keryxproject.org/](http://keryxproject.org/)

but if you have all the packages there's nothing to stop you copying them from your apt cache to the other one

---

### Post by elliotn on 2010-08-14
Check this post
 ubuntuforums.org/showthread.php?t=819396

---

### Post by elliotn on 2010-08-14
[check this post]("ubuntuforums.org/showthread.php?t=819396")

---

### Post by Cherry Cotton on 2010-08-15
The problem with simply transferring cache files is that I don&#8217;t want to put _everything_ from my computer onto hers, just packages she&#8217;d like (and their dependencies). The problem with the Keryx project is that it requires a flash drive, and I do not know if her computer even has USB ports. Besides that, I&#8217;d like something that I can take to her house (like a CD), rather than something I&#8217;d have to take to her house, bring back to mine, take to her house, bring back to mine if something goes wrong, etc...

**EDIT:** She says she does have USB ports, score! So, I&#8217;ll try Keryx. Let me know, in the meantime, if you have any other ideas. Thanks!

**EDIT 2:** Oh, and to make this easier, I put Keryx on a flash drive, started Ubuntu from the installation CD, and created a Keryx project using the LiveCD environment as the basis. Since both our computers use a 32-bit architecture, I&#8217;ve now created a Keryx project identical to what I would have if I had already installed Ubuntu on her computer and used that for the basis. This way, I&#8217;ll have programs to install on her computer right after installing Ubuntu.

---

### Post by elliotn on 2010-08-15
> **elliotn said:**
> [check this post]("ubuntuforums.org/showthread.php?t=819396")

If u read the link I posted above and did as mentioned, the folder created will have all programs including their dependencies, installing audacity for example, u double click on audacity.deb then it'll say dependancy audacity-data is not satisfied, u simply go to that folder and look for it.

---

