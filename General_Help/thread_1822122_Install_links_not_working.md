---
title: "Install links not working"
date: 2011-08-10
forum: General Help
---

### Post by solouko on 2011-08-10
I've found this with a lot of things and It's more annoying than anything but I'd like to try and fix it. 

Problem: When I go to install something from a website for example [WINE ]("http://www.winehq.org/download/ubuntu")there is a link reading "*click this link to install the wine1.2 package."* when I click the link and others like it I get a dialogue box appear with the message:

"this application needs to be opened with an application"

when I copy the link location I get "apt://wine1.2"

What should these links be opening with? 


I'm currently running Ubuntu 10.4 which comes with wine so it's just a case of typing: ```
sudo apt-get  install wine1.3
```
into a terminal to install it, but... if the link worked as it should, wouldn't clicking it negate the terminal window all together?

---

### Post by Darkened35 on 2011-08-10
You should be able to select the program to open it in. If you open it in Ubuntu Software Center it should work.
If USC is not in 10.04 (I don't know if it is, I never used it), there should be a program called Gdebi, use that.

---

### Post by CatKiller on 2011-08-10
The mechanism that makes that work is called apt-url. I can't remember if it's installed as a package or what, but that's what you need to configure.

---

### Post by solouko on 2011-08-10
> **CatKiller said:**
> The mechanism that makes that work is called apt-url. I can't remember if it's installed as a package or what, but that's what you need to configure.

Thank you, for some reason apt-url didnt install with Ubuntu, this is not the first annomerly I've found with this installation.  I have a feeling something went wrong as I've installed Ubuntu onto two systems this week, one was fine and still working wonderfully on my laptop, the other (the one i'm having problems with) Is so bad I'm going to try running it as a virtual machine insted.  

Thank you for the help, just knowing the name of the application is half the battle.

---

