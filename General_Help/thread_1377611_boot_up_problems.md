---
title: "boot up problems"
date: 2010-01-10
forum: General Help
---

### Post by hatridge on 2010-01-10
Ubuntu installs fine.
Updates install fine.
It all checks out.
Problem seems to come after running linux for a few hours for some reason it starts to act up, and then automatically reboots itself. When it reboots it will not recognize the password. It just loops and loops. I have to reinstall linux to get into my machine. this is my 3rd install. I ran a disk utility and that seems fine. I am very new to linux but familiar with computers and Win@#$%. Any suggestions?

---

### Post by TheHimself on 2010-01-10
This sounds weired. Which applications have you installed (after installing Linux)?

---

### Post by hatridge on 2010-01-10
Nothing much....some decoder to play mp3 files in rythembox, compiz advanced desktop editor and compiz fusion icon, added local weather to a task-bar.....thats it. The rest of the stuff I did was all common tweaks....color, themes, fonts ect. My first instinct was either a corrupt hard drive or since it seems to be fine for about 5 hours, could it be a cooling problem? power source... is there a fan speed test somewhere?

---

### Post by hatridge on 2010-01-10
oh and one other thing ...i did install abdode flash for linux.for website videos

---

### Post by SecretCode on 2010-01-10
Sounds like a heat problem *could* be the cause.

Install sensors-applet
```
sudo aptitude install sensors-applet
```
and then add the "Hardware Sensors Monitor" applet to your panel.

Right-click, select preferences, and see what temperature sensors you have available. Enable them and keep an eye on the graphs...

---

### Post by hatridge on 2010-01-10
I suspect overheating as well.

Next question...When inputting code you provided, I am assuming you mean in the terminal? 
Type it in like a DOS code? 
Well.... when I do that...I get a prompt to type password. When I **TRY** to type anything it seems I have no control over keyboard. Nothing will type in terminal. Must force quit.
What is wrong with my terminal?

 *note - terminal works good  (basic commands) up until I get to this password prompt, then it locks up

 Bean new to Linux and this forum, should I be asking this question in a different post?
and while I'm here....I have noticed that every time I post, I get a bean? Is 8 or 9 beans too many for the beginners forum? It would not let me access it after logging in. Is the goal to have as few beans as possible?....or.... Have I wore out my beginner beans? Is there a bean forum where I could learn about the beans? I'm asking you, because it seems like you have "bean" answering questions here for some time. No disrespect.

thanks

---

### Post by SecretCode on 2010-01-11
Yes, open a terminal window e.g. via Applications > Accessories > Terminal and type the command. Using 'sudo' requires your own password (which it then remembers for some number of minutes) - the password characters are being accepted, even though it doesn't display *s or anything. This is entirely normal, just entirely unlike windows!

Your bean count is just your post count, and shouldn't give you any problems. I don't know why you had a problem accessing the forum - if it persists, and you can get into "Forum Feedback and Help", ask for assistance there.

---

### Post by hatridge on 2010-01-11
ok thank you, that seemed to install ....but I can't seem to find it after the install. How do I bring it up?

---

### Post by SecretCode on 2010-01-11
Run these commands as well (I forgot about them):
```
sudo sensors-detect
service lm-sensors start
sensors -s
```
lm-sensors should have been installed as part of sensors-applet.

Then if you right-click on a blank part of your top panel, and select "Add to panel...", you should find "Hardware Sensors Monitor" in the list. Click add.

---

### Post by hatridge on 2010-01-11
that worked thank you very much

---

### Post by hatridge on 2010-01-11
core temp 22  degrees Celsius
GPU temp 57 degrees Celsius....what is normal please?

---

### Post by SecretCode on 2010-01-11
Normal depends on your system!

57 deg C is pretty cool. And 22 deg C is nothing ... room temperature. See if you have other sensors available in the applet preferences menu (you may not).

Keep an eye on the GPU temp (your CPU temp will probably be similar). See what it normally goes up to while the computer's still working fine (could easily be 85 degC). 

Then perhaps set the upper limit in the applet (you'll have to dig around for the preferences) - then you'll get a notification popup when it exceeds that.

If you always have high temperatures when you experience these lockups, that's your problem. Of course, it could be something else...

---

