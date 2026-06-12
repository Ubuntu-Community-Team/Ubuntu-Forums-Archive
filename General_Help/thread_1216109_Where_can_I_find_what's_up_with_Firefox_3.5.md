---
title: "Where can I find what's up with Firefox 3.5?"
date: 2009-07-17
forum: General Help
---

### Post by tridentblack on 2009-07-17
Update software just claimed it downloaded Firefox 3.5, but the Firefox from the Applications menu is still Firefox 3.0.11. This Firefox forces British spellings on me, like "Labour Centre" instead of "Labor Center".

I downloaded Firefox 3.5.1 from Mozilla, and it runs well except for crashing in fullscreen mode on Youtube, so I assume that's why we are still using 3.0.11...But my question is, where can I find out the status of projects that are bundled with Ubuntu and their versions? I'm new to Ubuntu, but I'm a software developer so developer resources are fine.

Thanks!
Luke

---

### Post by L815 on 2009-07-17
You can look here for Mozilla's PPA : 
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)


Also, you can install firefox 3.5 via:
```
sudo apt-get install firefox-3.5
```

It will install separate from 3.0.

If you are happy with 3.5, you may do a:
```
sudo apt-get remove firefox-3.0
```

Mind you, firefox-3.5 will be branded 'Shiretoko' (sp?) because it hasn't been officially release (i think that's the reason).

---

### Post by tridentblack on 2009-07-18
Thanks for that resource. I believe the current release of Firefox is 3.5.1, that's what I'm running from their main download page, it doesn't say Beta:
[http://www.mozilla.com/en-US/firefox/personal.html?from=getfirefox](http://www.mozilla.com/en-US/firefox/personal.html?from=getfirefox)
It crashes on Youtube fullscreen, which is why I assume everybody is still running 3.0.11? But I wanted to watch that. Thanks.

---

### Post by vinutux on 2009-07-18
yeh...you need to install shiretoko..unbranded FF version instead of Branded one...for Brander FF you need to wait till 9.10

---

### Post by armagedonc on 2009-07-18
how can I run 3.0.1 and 3.5 separately.

---

### Post by vinutux on 2009-07-18
> **armagedonc said:**
> how can I run 3.0.1 and 3.5 separately.

If you are installing 3.5 from PPA it called Shiretoko (unbranded version of FF/codename of FF) Both of them are under your **[COLOR="DarkGreen"]Application>internet[/COLOR]** section

---

### Post by lovinglinux on 2009-07-18
> **tridentblack said:**
> I downloaded Firefox 3.5.1 from Mozilla, and it runs well except for crashing in fullscreen mode on Youtube

See **Solution** [*[COLOR="Red"]**FOT008**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT008).

For future reference....

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

