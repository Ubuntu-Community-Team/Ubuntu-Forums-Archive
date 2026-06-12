---
title: "Easy one... How to install Java?"
date: 2011-02-04
forum: General Help
---

### Post by Senzuri on 2011-02-04
Hi, I've never used any linux server before and I've just purchased a ubuntu VPS.

I need to know how I can install Java from SSH.

Also another quickie, is there anyway I can enable any type of VNC or similar remote access program?

Thanks for the help guys.. :KS

EDIT: I've tried sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts but no luck
EDIT2: Also have ubuntu 9.10 installed if that helps.

---

### Post by veggen on 2011-02-04
What do you mean by "no luck"? What exactly went wrong? It didn't find the packages? Or it installed but java still isn't recognized?
If it's the first, check [this](http://www.ubuntugeek.com/sun-java6-packages-got-new-ppa-new-for-ubuntu-10-1010-04.html).
VNC-wise, I know there was a detailed discussion about it on this forum about a month or two ago. Try searching for it. But to answer your question, yes, it's possible.

---

### Post by kukker32 on 2011-02-04
enter the software center, and search for 'java' and hopefully there should be some java packages there, the ones you would need is java enviroment blah blah blah..
and java browser plugin.. this should be helping you installing java.

---

### Post by sammiev on 2011-02-04
Hope you find this [helpful]("http://sites.google.com/site/easylinuxtipsproject/java#TOC"). GL :)

update: Welcome to Ubuntu! :)

---

### Post by Senzuri on 2011-02-04
Thanks for all the replies. I was able to get it working by using sudo apt-get update (I think)

---

