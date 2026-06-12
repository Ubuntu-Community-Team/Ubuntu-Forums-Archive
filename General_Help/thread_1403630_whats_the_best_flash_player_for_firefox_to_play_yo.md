---
title: "whats the best flash player for firefox to play youtube vids?"
date: 2010-02-10
forum: General Help
---

### Post by colobix on 2010-02-10
Hey I just tried youtube for the very first time using firefox in ubuntu.
But when I click on a video, a blue play button comes up and when I click on that nothing but a black screen comes up.
I assume I have the wrong flash player or something.
I installed the ubuntu extra thing using the terminal, I thought that would solve the problem.
Please help me out here.

---

### Post by darolu on 2010-02-10
Install the Adobe Flash player with:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by colobix on 2010-02-10
It said its already installed. nothing changed. i mean none packages installed and none removed.

still same thing on youtube.

---

### Post by darolu on 2010-02-10
It means firefox is using something else; check the content of  '/usr/lib/firefox/plugins' and '~/.mozilla/firefox/plugins' directories, that way you'll know what other plugins you have installed, then you can uninstall them with apt-get.

---

### Post by colobix on 2010-02-10
I'm glad I gave ubuntu a new chance.
Everything is getting smoothly now.
Thanks alot :)

---

