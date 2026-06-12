---
title: "I am dumb."
date: 2010-08-06
forum: General Help
---

### Post by Teck9 on 2010-08-06
Okay, someone put ubuntu 8.04 on my compaq presario v6000, works fine, but I don't know ANYTHING about linux or programming. I'm trying to install the adobe flashplayer, and I'm at the point where I just need to put the .so into the mozilla plugin folder but I don't know where to find it. I don't know where to find anything... I'm so lost. If anyone is willing to baby talk me through this thing I would really appreciate it. Thanks

---

### Post by Zorgoth on 2010-08-06
There was a time when what you are talking about was necessary, but I believe now you can just install the ".deb for Ubuntu 8.04+" from adobe's website and/or something like flashplayer-plugin-nonfree from the package manager.

What you are talking about relates to the terminal command "ln -s"; type "man ln" in the terminal for more information (to open the terminal, go to Applications > Accessories > Terminal or run the command "gnome-terminal" after typing the run hotkey "Alt-F2").

I would recommend installing Ubuntu 10.04 instead of 8.04 as 10.04 is the new LTS and as support for Ubuntu 8.04 will end in April 2011 (so no more updates, even security), whereas Ubuntu 10.04 will be fine for a about 2 and a half years I think.

---

### Post by corrytonapple on 2010-08-06
Make life easier on yourself and let this do it all for you::)
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by endotherm on 2010-08-06
gui way, go to Application -> Software Center and search for "Ubuntu restricted extras" and install it. this will give you a number of AV codecs, adobe flash, sun java (or at least it used to) and some other useful things for AV compatibility. crap, thats right you are using hardy. ok make that System -> Administration -> Synaptic Package Manager, instead of software center.

the cli way is fastest. open a terminal and enter:
```
sudo apt-get install ubuntu-restricted-extras
```. when prompted put in your password (note: the password prompt does not print *s for each char so it will look like it;s not taking your password, but it is) and it will perform the installation.

---

### Post by rensell on 2010-08-06
When I was using Ubuntu Desktop and downloaded flash from the adobe site, Adobe gave complete directions on how to install it, including where to put the files and everything. Possible go back to flash.com and click download (or such) and it should redirect you to the linux flash page(s).

-R

---

### Post by endotherm on 2010-08-06
> **rensell said:**
> When I was using Ubuntu Desktop and downloaded flash from the adobe site, Adobe gave complete directions on how to install it, including where to put the files and everything. Possible go back to flash.com and click download (or such) and it should redirect you to the linux flash page(s).

-R
the downside to this approach is that you take responsibility for updating manually anytime flash or firefox are updated. 

the ff plugin above looks interesting, and I have seen lovinglinux arround a good bit, but i don't believe that this is a job for a browser plugin (do you have to sudo ff?) and i am very cautious installing addons that are not verified and have only 7 reviews.

---

### Post by samg34 on 2010-08-06
I have got the adobe flash player, but i have noticed that it doesn't work for YouTube.com (r). I just get the gray box and "try again late". I have tried to get it in many different ways, but none of them actually show videos on any site.

---

### Post by rensell on 2010-08-06
I didn't stick with Ubuntu Desktop - was just "learning" with it to set up a server and compare it with win XP - I would switch but I use VB.NET software for my compare, and I don't want to rewrite it in a another language - that's neither here nor there. I was just saying the Flash.com way route worked for, Updates are not something I'm overly concerned about - when I use SSH and have updates I simply run a command and it's done - quite easier than windows actually. However, it would be better if it were more automated for a desktop environment, I agree.

-R

---

### Post by corrytonapple on 2010-08-06
> **endotherm said:**
> the downside to this approach is that you take responsibility for updating manually anytime flash or firefox are updated. 

the ff plugin above looks interesting, and I have seen lovinglinux arround a good bit, but i don't believe that this is a job for a browser plugin (do you have to sudo ff?) and i am very cautious installing addons that are not verified and have only 7 reviews.
I use it. It works well. Anyway, I trust him.
Next time, come up with a better thread title. This title will give the thread less attention.

---

### Post by ghostborg on 2010-08-06
Chromium 5 has flash out working out of the box.

---

### Post by endotherm on 2010-08-06
> **ghostborg said:**
> Chromium 5 has flash out working out of the box.
yeah, but then you have to use chromium 5.

---

