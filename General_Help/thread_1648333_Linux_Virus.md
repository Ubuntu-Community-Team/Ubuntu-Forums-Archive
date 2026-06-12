---
title: "Linux Virus?"
date: 2010-12-18
forum: General Help
---

### Post by nl4m on 2010-12-18
I was just using the epiphany browser to watch some videos on youtube when out of nowhere all my open windows disappear and this icon appears on my lower panel. When you click on it, it launches firefox and takes you to this link: [http://s.ytimg.com/yt/img/pixel-vfl3z5WfW.gif](http://s.ytimg.com/yt/img/pixel-vfl3z5WfW.gif) 

False alarm... Sorry.[]("http://www.sophos.com/security/analyses/viruses-and-spyware/trojdloadhp.html?_log_from=rss")

---

### Post by noah++ on 2010-12-18
> **nl4m said:**
> It seems to be a trojan called "Troj/Dload-HP" that effects windows OS's. It was released on December 17 (yesterday). This website tells you what the trojan did to your computer, the file/registry changes it made. What it does not cover Linux, only windows:
[http://www.sophos.com/security/analyses/viruses-and-spyware/trojdloadhp.html?_log_from=rss](http://www.sophos.com/security/analyses/viruses-and-spyware/trojdloadhp.html?_log_from=rss)
How did you conclude that it was this Trojan? In any case, Linux malware is rare; and Windows malware almost certainly doesn't affect Linux.

If you Google for that URL  that appeared on your desktop, and for ytimg.com, I think you'll agree that it's nothing harmful. The URL refers to a 1px x 1px placeholder image, and ytimg.com is YouTube's private domain for hosting its own auxiliary content.

I am guessing you made some mouse gesture without realizing it (Synpatics-driven trackpads can suddenly get sensitive and inaccurate, for example) that saved an image on your screen to the desktop and switched focus to the desktop.

---

### Post by nl4m on 2010-12-18
> **noah++ said:**
> How did you conclude that it was this Trojan? In any case, Linux malware is rare; and Windows malware almost certainly doesn't affect Linux.

If you Google for that URL  that appeared on your desktop, and for ytimg.com, I think you'll agree that it's nothing harmful. The URL refers to a 1px x 1px placeholder image, and ytimg.com is YouTube's private domain for hosting its own auxiliary content.

I am guessing you made some mouse gesture without realizing it (Synpatics-driven trackpads can suddenly get sensitive and inaccurate, for example) that saved an image on your screen to the desktop and switched focus to the desktop.

Sorry for the paranoia. You have to excuse me I was a former Windows users. The first thing I learned using windows is that if any changes take place that you did not do yourself it's the work of a virus. So, initially, the first thing I did was to google it. I found that website saying it's a trojan. That's when my windows (paranoid of an attack) mind frame kicked in and I began to jump to conclusions.   

You are 100% correct. One of the features in Ubuntu is that if you drag and drop a URL/link to your panel it creates a launcher for it. As soon as I saw your post about it being a "mouse" issue something click in my head and I dragged an image to my panel to see what will happens, and sure enough I got the same launcher icon.

---

### Post by P1C0 on 2010-12-19
You can always use this specialized linux virus scanning script:
```
#!/bin/bash
echo Linux virus scanner
sleep 1
echo Scanning now...
sleep 10
echo Still scanning...
sleep 10
echo Almost done...
sleep 5
echo Drum roll...
sleep 3
echo No viruses found!!!
sleep 1
echo Done
```Someone else has posted this a while ago, but I don't remember the name, sorry.

---

### Post by feddozz on 2010-12-20
> **P1C0 said:**
> You can always use this specialized linux virus scanning script:
```
#!/bin/bash
echo Linux virus scanner
sleep 1
echo Scanning now and checking e-cards...
sleep 10
echo Still scanning and unpacking presents...
sleep 10
echo Almost done...
sleep 5
echo Drum roll...
sleep 3
echo No viruses found!!!
sleep 1
echo Done
```Someone else has posted this a while ago, but I don't remember the name, sorry.


That's a brilliant script! Over Cristmas time you may want to check for new viruses hidden in Christmas e-cards. Use this:

```

#!/bin/bash
echo Linux XMas virus scanner
sleep 1
echo Scanning now...
sleep 10
echo Still scanning...
sleep 10
echo Almost done...
sleep 5
echo Drum roll...
sleep 3
echo No viruses found!!! Merry Xmas!
sleep 1
echo Done
```

Watch out for the new year's script coming soon!!

---

