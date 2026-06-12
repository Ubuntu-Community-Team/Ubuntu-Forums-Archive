---
title: "How do I get from the login to desktop"
date: 2006-02-22
forum: General Help
---

### Post by Matabus on 2006-02-22
This probably the stupidest question ever asked, and its probably in this forum, or somewhere else, but I dont have the time to look through it.  I apologize for my ignornace, but:

After the ubuntu boots up, it goes to what looks like MS Dos(i know its not), I log in, and now what.  How do I get to the desktop, or what looks like windows.  Like whats on the screenshots?????????

Thank you for your patience.

---

### Post by suRoot on 2006-02-22
I'm not sure I understand you, but I think you mean you're getting a console login - just text onscreen & no graphics?  If that's the case, there's something wrong with your video configuration.  Do you know what kind of video card you have?  Just for kicks, you can try running the command startx after logging in, which should start Xwindows, if it'll start.

---

### Post by heimo on 2006-02-22
Did you install Ubuntu using default install, not server install? You should go directly to log in screen which gets you to gGnome desktop, but if it's not happening, it's not installed or there was problems starting X Window System.

Try:
```
sudo /etc/init.d/gdm start
```

---

### Post by Matabus on 2006-02-22
Thanks guys I will try it tonight.   I used the default install.  Yeah, my login is only text.  No graphics.

I never even tried to go in the graphics.

---

### Post by heimo on 2006-02-22
[quote=Matabus]Thanks guys I will try it tonight.   I used the default install.  Yeah, my login is only text.  No graphics.

I never even tried to go in the graphics.[/quote]

Were there any errors? If not, I'd also try to run these commands to make sure everything is installed as expected:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade


```

---

### Post by Matabus on 2006-02-22
I never got any errors. I just thought it was the normal thing, that there was some code that I had to write to load up the desktop.

---

### Post by elzeon on 2006-02-23
[QUOTE=heimo]Were there any errors? If not, I'd also try to run these commands to make sure everything is installed as expected:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade


```[/QUOTE]

after executing that code i got a message that i don't have enough space))) i have allocated to little space for root files)) but everything seemed to be going fine....

---

### Post by Matabus on 2006-02-23
I believe I have fix the problem.  Since I messed around so much, I must of messed up my login.  I uninstalled Ubuntu, then reinstalled it.  This time it took way longer than the first time I installed it.

I must have just installed the server.  But now that I did the full install it works.  Thank you for all your help.

---

