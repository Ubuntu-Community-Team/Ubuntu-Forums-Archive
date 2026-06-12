---
title: "Flash not working correctly"
date: 2010-05-31
forum: General Help
---

### Post by ksihawk7 on 2010-05-31
This is probably a noob question, but I can't help but ask. A lot of times when I try to play a flash game or watch a youtube video, I can view everything fine, but it doesn't do anything when I click on them, it will make the animation like it does when I click on it, but it doesn't do anything. How can I fix this?

---

### Post by Agent ME on 2010-05-31
I had the same problem in Ubuntu 9.10 64-bit, using the default version of Flash that used nspluginwrapper. It was fixed when I added [this ppa](https://launchpad.net/~brandonsnider/+archive/experimental-flash), which installed a more recent version of Flash without nspluginwrapper.

---

### Post by lovinglinux on 2010-06-01
This is caused when you run a 32bit flash plugin on a 64bit browser.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

