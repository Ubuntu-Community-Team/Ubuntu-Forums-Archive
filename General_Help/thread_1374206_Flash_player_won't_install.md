---
title: "Flash player won't install"
date: 2010-01-06
forum: General Help
---

### Post by mocatz187 on 2010-01-06
Hi.
I am looking for instructions on installing adobe flash to ubuntu
This plugin works effortlessly in Xubuntu , OZOS and many others but not in ubuntu.
where are the so called "repositories" and how do you use them.
I am familiar with the RUN command in windows and nothing more.
Why is Ubuntu so much more stubborn than Xubuntu , kubuntu and OZOS. I had those OS's on this computer and I could watch videos at youtube!!!!
when I searched the ubuntu karmac documentation for flassh it turned up only one english link and it was dead reverting me back to the search page i started at.
the main search page is bloated with things like : what is ubuntu, wher to get ubuntu, is ubuntu free.
if I have read all of that I might as well see if adobe can help. There is no available documentation available at this time that I can find without going to a non ubuntu site.
 
Thanks

---

### Post by xtjacob on 2010-01-06
To install flash on 32-bit Ubuntu you click applications and go to the Ubuntu Software Center and lookup flash. There should be adobe flash plugin or install or something along the lines of that.

---

### Post by mocatz187 on 2010-01-06
At the software center there is nothing that says Adobe and there is nothing that says Flash.
What version of Ubuntu are you using?

---

### Post by xtjacob on 2010-01-06
9.10

---

### Post by mocatz187 on 2010-01-06
So you don't have any idea as to the exact name of this plugin

---

### Post by khelben1979 on 2010-01-06
Go to [this webpage]("http://www.adobe.com/software/flash/about/") from Adobe and report back what you got installed in this thread.

[Here you get the flash player]("http://get.adobe.com/flashplayer").

---

### Post by ajgreeny on 2010-01-06
Can you show us the output of ```
cat /etc/apt/sources.list
```please.  There certainly should be a version of adobe flashplugin available in the repositories, so I can omly assume that you have a problem of some sort with your apt sources.  Also make sure you don't have a version of the gnash plugin or swfdec installed as these can conflict with adobe flashplugin

---

### Post by JustMarius on 2010-01-06
try this im sure it will work


sudo apt-get install ubuntu-restricted-extras

---

### Post by xtjacob on 2010-01-06
sorry I was at school. It should be called Adobe Flash plugin, or Adobe Flash Plugin 10. Maybe it's in the Ubuntu Media Repo:```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by mocatz187 on 2010-01-07
Yes Ubuntu restricted areas worked!
now I can watch people do silly things on YouTube.
 
Thanks everybody.

---

