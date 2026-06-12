---
title: "No Gnome panels!"
date: 2010-10-27
forum: General Help
---

### Post by fallenshadow on 2010-10-27
Ive experienced before that removing packages related to Evolution breaks Ubuntu. Once again ive experienced this again!! :mad:

Ubuntu luckily isn't completely broken but now all the Gnome panels are missing!! Clicking on change desktop background also does nothing! :mad:

Any ideas as to what may have been uninstalled?

---

### Post by stoneage on 2010-10-27
Gnome-applets and gnome-panel probably.

Here are some other likely contenders:-
[ATTACH]173681[/ATTACH]

If you use Synaptic go to File -> History, it will tell you what you did.

---

### Post by sikander3786 on 2010-10-27
Try

```
sudo apt-get install -f
```

What does this say?

```
killall gnome-panel
```

---

### Post by kerry_s on 2010-10-27
do the ctrl+alt+f1 
log in
sudo apt-get update
sudo apt-get install ubuntu-desktop

> Ive experienced before that removing packages related to Evolution breaks Ubuntu. Once again ive experienced this again!!


then don't do it. :lolflag:

---

### Post by fallenshadow on 2010-10-27
I had an idea already that in order for me to have a working desktop the best thing would be to install ubuntu desktop.

So I did and it worked!! :) :guitar:

Here is what I did:

1. Restarted my PC.
2. Picked Root terminal on recovery menu.
3. sudo apt-get install ubuntu-desktop.
4. reboot (inside the terminal restarted the PC)
5. Back working again... except I had to go uninstalling stuff I previously had uninstalled like tomboy and empathy. :)

While I do appreciate them having a package which can bring your system back to life... this should not have happened in the first place. I have already sent a letter to Mark Shuttleworths secretary about this and asked her to pass it onto him. It must have never got to him because I got no response! :mad:

The fact that Evolution is so tightly integrated into Ubuntu is a serious problem. I can only uninstall Evolution so it doesn't appear in my menu, knowing that the bulk of Evolution is still there! :mad:

Uninstalling something as innocent as Evolution plugins, which I obviously wouldn't need with Evolution itself uninstalled should not uninstall essential parts of the Ubuntu desktop like applets/panels, gnome-control-center and others!!  ](*,)

I feel like im talking to a brick wall at times because Mark is too far up there for my words to reach him! If I could talk to him at least he might see the sense in what im saying!

Evolution is an application like the many others in Ubuntu, so why can't it be uninstalled like a normal application?? :confused:

//End of rant/stress relief. :D

---

### Post by WorMzy on 2010-10-27
If you're that upset about having redundant apps, then move to another distro. I recommend Arch Linux, though it's seriously not newbie friendly. You start off with the very basics of a Linux OS, and build up from there. There are no false-dependencies. You will need the evolution-data-server package if you want gnome-panels though. Empathy and bug-buddy also rely on it.

---

### Post by fooman on 2010-10-27
i don't think it was "*evolution-plugins*" that caused this.  more likely it was "*evolution-data-server-common*" that took the boatload of much needed packages along with it.

i have uninstalled all packages with "evolution" in their name *except for "evolution-data-server-common"*....with no ill affects at all.  i am using ubuntu 10.04, and have done this on previous versions as well.

btw,  apt-get or synaptic both throw out a list of what they about to uninstall, and you must acknowledge with a y/n or ok in order to proceed....need to read through those lists before continuing.

---

### Post by fallenshadow on 2010-10-28
No it was actually libcamel, which is described as the MIME handler for Evolution!

Now how the hell is a new user supposed to know they are not supposed to remove this??

By the way most users beginning in Ubuntu will not be using Synaptic and use Software Center, which only tells you a list of Evolution items will be removed. This is why I thought hey everything is fine its only removing Evolution stuff. :mad:

When in fact it seems to secretly remove important system packages!! Without ANY kind of warning!  ](*,)

---

### Post by fooman on 2010-10-28
ahh,  the software center!  did not think of that,  since i never use it myself.  

i see what you mean now....tried it myself just to see what gets uninstalled along with libcamel: synaptic gives a nice big list, while the software center just mentions a few of the things that will go along with libcamel.  :(

---

### Post by WorMzy on 2010-10-28
Wow, if there's isn't one already, someone aught to create a bug report for that on launchpad. That's pretty sloppy by Ubuntu's standards; but then, when you have at least five different interfaces for installing/removing packages there's bound to be some oversight.

---

### Post by fallenshadow on 2010-10-29
Really its a problem with Ubuntu and the way they are doing things but I think I will report under Ubuntu Software Center, since it seems I can't report directly to Ubuntu.

EDIT: Now reported - [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/668382](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/668382)

---

### Post by fallenshadow on 2010-10-30
I would like if anyone who has a Launchpad account could click on "Yes it affects me" in order to get this bug sorted sooner than later, before new users end up breaking their installs.

Just click on the link above to get to the bug report.

Especially the people here who tried it and can confirm the problem! However in theory this affects every Ubuntu user because nobody will get a warning when they try to remove libcamel in Ubuntu Software Center.

Thanks guys! ;)

PS: Im sorry for being a crazy rage monkey at the start of this thread! :D

---

