---
title: "Community Please Help Me...."
date: 2009-07-19
forum: General Help
---

### Post by tuxmanic on 2009-07-19
**Hello Everyone.... .** 

Our College INTERNET LAB (Consist 120 identical Systems, currently running on Win XP) Is **Going Switch to Ubuntu**.... 

For This purpose as a FOSS Enthusiast i need some Help from the Community... Bcoz if these things done** more than 2000 students will get d chance to Experience The WORLD of Linux**....  

i already googled all these but still in confusion ... So pls help me..  First up all SORRY for BAD Language.. 


**1**. Which Ubuntu Version We have to Choose** 8.04 LTS** or Latest **9.04 Jaunty** ?

**2**. Which desktop Environment KDE /Gnome ?( but Most of the students not familiar ant linux distro till now...) personally i prefer gnome but some people saying KDE will be good for windows users

**3**. First The complete Installation Is done on a system with necessary applications... Then we have to clone the complete hard disk to remaining system with working GRUB... but there are some problems


[LIST]
[*]     Only Few of them have optical drive.. So we are not preferring installation through optical media... but all the systems are Connected through High speed N/W.

So Reaming Option is hard disk cloning (so that we can avoid necessary application installation on each systems seperatley if installed on a single system with all settings)
[*]Hard disk cloning through Network
[*]First Clone the Master installation to a External hard disk & clone to all other systems using this Ext. HDD
[/LIST]
So Which Method We have to use n How? . pls explain????


**4**. After Installation & Network configuration  we have to setup Site Blocking & other security features ....  so how can i setup SQUID for all these... ?



Thanks in advance......

---

### Post by .nedberg on 2009-07-19
> **tuxmanic said:**
> **Hello Everyone.... .** 

Our College INTERNET LAB (Consist 120 identical Systems, currently running on Win XP) Is **Going Switch to Ubuntu**.... 

For This purpose as a FOSS Enthusiast i need some Help from the Community... Bcoz if these things done** more than 2000 students will get d chance to Experience The WORLD of Linux**....  

i already googled all these but still in confusion ... So pls help me..  First up all SORRY for BAD Language.. 


**1**. Which Ubuntu Version We have to Choose** 8.04 LTS** or Latest **9.04 Jaunty** ?

Test with 8.04, if it works, stick with it! 9.04 will have newer versions of applications though. But an LTS is preffered in a situation like this!
> **tuxmanic said:**
> 
**2**. Which desktop Environment KDE /Gnome ?( but Most of the students not familiar ant linux distro till now...) personally i prefer gnome but some people saying KDE will be good for windows users

Why not both and let the users choose when they log in?
> **tuxmanic said:**
> 
**3**. First The complete Installation Is done on a system with necessary applications... Then we have to clone the complete hard disk to remaining system with working GRUB... but there are some problems


[LIST]
[*]     Only Few of them have optical drive.. So we are not preferring installation through optical media... but all the systems are Connected through High speed N/W.

So Reaming Option is hard disk cloning (so that we can avoid necessary application installation on each systems seperatley if installed on a single system with all settings)
[*]Hard disk cloning through Network
[*]First Clone the Master installation to a External hard disk & clone to all other systems using this Ext. HDD
[/LIST]
So Which Method We have to use n How? . pls explain????

Clonezilla can help with this. It can even work as a server and you can clone many machines at once over the network.

> **tuxmanic said:**
> 
**4**. After Installation & Network configuration  we have to setup Site Blocking & other security features ....  so how can i setup SQUID for all these... ?


Sorry, can't help with that...

---

### Post by tuxmanic on 2009-07-20
[COLOR=Red]**Thanks [nedberg]("http://ubuntuforums.org/member.php?u=193487") ...... Im gng to try Clonezilla.....**[/COLOR]

---

### Post by russo.mic on 2009-07-20
Hey love it.  

I just wanted to give my +1 for gnome, as It's good to offer choice, but at the expense of confusing users.  I often have a hard time explaining that you can have 2 different gui's running on top of the same operating system.  

I generally find KDE to be less stable.  Esp. since the lastest releases.  very cool stuff there doing, but I vote to give them more time to work it out.

---

### Post by .nedberg on 2009-07-20
> **russo.mic said:**
> 

I generally find KDE to be less stable.  Esp. since the lastest releases.  very cool stuff there doing, but I vote to give them more time to work it out.

If you end up with 8.04, then KDE will be at version 3.5. That version is very stable! 9.04 has got KDE 4, more bling, less "stable".

Even if I am a KDE user I would recommend Gnome, because it is more supported here on the forums and easier to get help if you need it. It is also the "default" Ubuntu GUI.

---

