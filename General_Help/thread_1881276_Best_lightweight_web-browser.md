---
title: "Best lightweight web-browser?"
date: 2011-11-15
forum: General Help
---

### Post by fallenshadow on 2011-11-15
So I like to listen to music while im developing software and sometimes I need to search something quickly from the internet. Starting Firefox all the time is a pain as I don't need any features apart from web browsing.

I need something that is standards compliant to HTML5 and CSS, very fast, very lightweight and stable. Does such a thing exist? :D

---

### Post by fallenshadow on 2011-11-15
Bump... :P

---

### Post by tartalo on 2011-11-15
> **fallenshadow said:**
> I need to search something quickly from the internet (...) that is standards compliant to HTML5 and CSS, very fast, very lightweight and stable.

I'm answering you using dillo 3.0.1

It's not HTML5 compliant, CSS support is incomplete, and has no Javascript but there is nothing lighter with a GUI, and it's good enough to search something quicly.

It's not in Ubuntu, but it is in Debian SID, you can download the packages and install it manually.

---

### Post by tartalo on 2011-11-15
doublepost

---

### Post by Docaltmed on 2011-11-15
Well, if listening to music is your goal, how about Radio Tray? Build your own list of stations. I use it a lot.

---

### Post by killermist on 2011-11-15
If graphical interface is not necessary, lynx or elinks run from the console and are pretty snappy.

---

### Post by fallenshadow on 2011-11-15
I want something more featureful than dillo,lynx etc.

I was thinking of checking out Midori so I added the PPA and tried to install it... however it comes up with quite a scary message forcing me to cancel it.

---

### Post by raja.genupula on 2011-11-15
```
sudo apt-get install midori
```
try to install it from terminal and shows me what you got.

---

### Post by Elfy on 2011-11-15
> **fallenshadow said:**
> I want something more featureful than dillo,lynx etc.

I was thinking of checking out Midori so I added the PPA and tried to install it... however it comes up with quite a scary message forcing me to cancel it.

Why did you usee a PPA - midori is in the repos.

Try removing the PPA and see if it still wants to remove things.

---

### Post by tartalo on 2011-11-16
> **forestpiskie said:**
> Why did you usee a PPA - midori is in the repos.

And if you still prefer to use the PPA don't forget that you need the Webkit PPA too. 

> 
***************************
***** IMPORTANT *****
***************************
If you use this repository, you'll also need WebKit-team PPA :
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)


---

### Post by claracc on 2011-11-16
I recommend epiphany browser. Very quick and light. Installing also epiphany extensions can help to view youtube in html5.

It can be added css styles too and of course support java.

It has a critical bug as  crashing in some websites when back button is clicked, but it will work well enough for your purposes, I think.

It is in the repositories.

---

### Post by fallenshadow on 2011-11-16
I have successfully installed Midori... I just had to wait until the packages for 0.4.2 were released to install it.

I am liking it so far and it really suits my needs since it uses so much less ram. It also is surprisingly customizable and seems stable so far.

I might still try Epiphany but I read reviews in the software center and it sounds very buggy.

---

