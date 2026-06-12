---
title: "Finally upgraded to 11.10, and now I can't use Unity 3D"
date: 2011-10-13
forum: General Help
---

### Post by alreadytaken4536 on 2011-10-13
I had this problem on a laptop when I tried Fedora 15 and it gave me that god-awful "fallback mode". I ordered and assembled a $500 midrange PC so that I wouldn't have to deal with this type of thing any more.

So I wait for 5 hours while Ubuntu upgrades, and when I finally get around to trying it, there are many things wrong and features missing.

- The dash takes 4 seconds to load after clicking on the dash button.
- I cannot drag windows between workspaces while in the workspace manager.
- I cannot change the order of items in the launcher.
- I cannot enable wobbly windows or anything else that I enjoyed in 11.04 with Compiz Fusion.
- The new and improved alt+tab feature is not looking very improved, and is nothing more than a small grey box with icons in it.
- Most importantly, and likely the source of all of these problems, I only have the Ubuntu 2D option at the log in screen!

My hardware should be more than capable of doing all of these things.

- AMD Phenom II X2 Black
- 4 GB of RAM
- AMD Radeon 6670

How do I get 3D back and have the sexy Onieric Ocelot that I was promised?

---

### Post by Vaphell on 2011-10-13
do you have proprietary drivers installed and in use? run the app that manages 3rd party drivers and check

what is the output of the line below?
```
glxinfo | egrep -w 'direct|string'
```
if you don't have glxinfo installed
```
sudo apt-get install mesa-utils
```

---

### Post by effenberg0x0 on 2011-10-14
There are proper instructions for ATI here, post #5.
[http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati](http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati)

Regards,
Effenberg

---

