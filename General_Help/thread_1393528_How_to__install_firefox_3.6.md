---
title: "How to  install firefox 3.6"
date: 2010-01-29
forum: General Help
---

### Post by Mashvv on 2010-01-29
Hey ! hows it goin ?? anyways i would like to know how  to install firefox 3.6  and  just to tell you that i used this tutorial to  do it [http://linuxhub.net/2009/11/how-to-install-firefox-3-6-on-ubuntu-karmic-koala/ ]("http://linuxhub.net/2009/11/how-to-install-firefox-3-6-on-ubuntu-karmic-koala/")
 and i did everything perfectly but at the end it told me to download a plug in which i dont want to ( not secure ) so i was just wondering if there was a way just to treplace the ubuntu version of firefox  into to the Mozilla version ! thanks ow and i just realized that ubuntu sucks without knowing  how to run things in terminal  so if there is any tutorial that help plz recommend it !
ThANKS :)

---

### Post by scouser73 on 2010-01-29
[[COLOR="Red"]**Download Firefox 3.6**[/COLOR]]("http://www.mozilla.com/en-US/firefox/all.html")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> **sudo -i**
Enter your password if asked
> **cd /opt**
> **chown -R username firefox**
[COLOR="Red"]**The username is what you use to log in to Ubuntu**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

