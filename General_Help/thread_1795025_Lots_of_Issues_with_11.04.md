---
title: "Lots of Issues with 11.04"
date: 2011-07-01
forum: General Help
---

### Post by zachnap on 2011-07-01
Hey, I'm using Ubuntu 11.04, 64-bit, intel processor (sandybridge)  and am having some issues. First, Firefox has blinking video. I looked into upgrading to Firefox 5 but I can't. There is no way to access an update manager of any sort. I click on it and nothing happens. The same is happening for other system applications like Settings - I can't access it because if I click on it nothing happens. Now, there isn't even and update manager that can be found anywhere. I can't do sudo apt-get.... because terminal tells me that no such command exists. 

I had a display problem where every-time the displays come out of sleep, the red display number box pops up and I have to turn it off - I change the setting over and over again but it happens anyway.

In general, in 11.04 it is extremely difficult to find what you are looking for. All of the menu bars are gone and you have to search scroll through every application to find anything. Before I could just click "System>Settings... etc. I don't like this setup.

Anyway, that last paragraph was a mini-rant. Does anyone have any suggestions as to why my 11.04 is so screwed-up? It wasn't always like this. Things worked fine initially.

---

### Post by linuxuser12345 on 2011-07-01
Replace 11.04 with 10.04.2 or 10.10 for a while. That will keep you good! ;)

---

### Post by wildmanne39 on 2011-07-02
> **zachnap said:**
> Hey, I'm using Ubuntu 11.04, 64-bit, intel processor (sandybridge)  and am having some issues. First, Firefox has blinking video. I looked into upgrading to Firefox 5 but I can't. There is no way to access an update manager of any sort. I click on it and nothing happens. The same is happening for other system applications like Settings - I can't access it because if I click on it nothing happens. Now, there isn't even and update manager that can be found anywhere. I can't do sudo apt-get.... because terminal tells me that no such command exists. 

I had a display problem where every-time the displays come out of sleep, the red display number box pops up and I have to turn it off - I change the setting over and over again but it happens anyway.

In general, in 11.04 it is extremely difficult to find what you are looking for. All of the menu bars are gone and you have to search scroll through every application to find anything. Before I could just click "System>Settings... etc. I don't like this setup.

Anyway, that last paragraph was a mini-rant. Does anyone have any suggestions as to why my 11.04 is so screwed-up? It wasn't always like this. Things worked fine initially.Hi, log out and click on your user name go to the bottom of the screen and choose ubuntu classic. Also for flash problems open firefox click on tools go to addons and install flashaid then follow the directions it almost always fixes flash problems. Did you do an upgrade or did you do a clean install?

---

### Post by AlmightyMokona on 2011-07-02
sounds like you did an upgrade from windows, did you?  That flashing screen error can be a bug in your registry that is effecting your graphics card.

---

### Post by Mark Phelps on 2011-07-02
> **zachnap said:**
> In general, in 11.04 it is extremely difficult to find what you are looking for. All of the menu bars are gone and you have to search scroll through every application to find anything. Before I could just click "System>Settings... etc. I don't like this setup.

Understand that, at present, this ability to go "back" to the "old" Gnome view is only available in 11.04.  Canonical has repeatedly stated that with 11.10, there will be no such option.  And, while there are rumours of Gnome 3 being such a replacement in 11.10, Canonical has not yet changed their position on FORCING everyone to use Unity in 11.10.

---

### Post by amjjawad on 2011-07-02
What shall I say? Unity? Oh well, better to login as GNOME Classic or use 10.04.2 LTS as previously suggested by our friends here.

Good luck!

---

### Post by zachnap on 2011-07-02
> Hi, log out and click on your user name go to the bottom of the screen  and choose ubuntu classic. Also for flash problems open firefox click on  tools go to addons and install flashaid then follow the directions it  almost always fixes flash problems. Did you do an upgrade or did you do a  clean install? 	

I'll try that. I upgraded from 10.10 to 11.04.
> 
		sounds like you did an upgrade from windows, did you?  That flashing  screen error can be a bug in your registry that is effecting your  graphics card. 	

I don't know what you mean: "upgrade from windows." I upgraded from 10.10 to 11.04 while in Ubuntu.

---

### Post by wildmanne39 on 2011-07-02
> **zachnap said:**
> I'll try that. I upgraded from 10.10 to 11.04.


I don't know what you mean: "upgrade from windows." I upgraded from 10.10 to 11.04 while in Ubuntu.
Hi, a lot of people have trouble because they upgraded from 10.10 instead of a fresh install, here is a link that usually fixes the problems from an upgrade.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by beew on 2011-07-02
> **zachnap said:**
> 
In general, in 11.04 it is extremely difficult to find what you are looking for. All of the menu bars are gone and you have to search scroll through every application to find anything. Before I could just click "System>Settings... etc. I don't like this setup.
.

Try this.

[http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray](http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray)

---

### Post by beew on 2011-07-02
> **zachnap said:**
> I'll try that. I upgraded from 10.10 to 11.04.


I don't know what you mean: "upgrade from windows." I upgraded from 10.10 to 11.04 while in Ubuntu.

He meant WUBI presumably.

---

### Post by zachnap on 2011-07-02
> **wildmanne39 said:**
> Hi, log out and click on your user name go to the bottom of the screen and choose ubuntu classic. Also for flash problems open firefox click on tools go to addons and install flashaid then follow the directions it almost always fixes flash problems. Did you do an upgrade or did you do a clean install?

This gave me a background and icons only, so there is now no way to access anything.

I think I will try the page you linked to because it describes the problem I just mentioned.

Update: no go... I also cannot login through terminal. I did a ctrl+alt+F1 to tty1. It says my information is incorrect but I entered the only passwords I know.

---

### Post by wildmanne39 on 2011-07-02
> **zachnap said:**
> This gave me a background and icons only, so there is now no way to access anything.

I think I will try the page you linked to because it describes the problem I just mentioned.

Update: no go... I also cannot login through terminal. I did a ctrl+alt+F1 to tty1. It says my information is incorrect but I entered the only passwords I know.Hi, it would be the user password you created when you installed ubuntu.

---

### Post by zachnap on 2011-07-02
> **wildmanne39 said:**
> Hi, it would be the user password you created when you installed ubuntu.

Yeah, I tried it. I changed my password at one point so now there are two different passwords for linux for some reason...I have to enter both to get into ubuntu... I tried both. It won't even let me type a password - i.e., there are no asterisks after I enter the password, however, the user login space shows my login name after I type it.

My linux OS is completely unusable. I've never seen anything so screwed-up. It is as if one-by-one over the past couple month programs just started deleting themselves and self-destructing. The only way for me to get on the net now is to double-click an html file.

---

### Post by wildmanne39 on 2011-07-02
> **zachnap said:**
> Yeah, I tried it. I changed my password at one point so now there are two different passwords for linux for some reason...I have to enter both to get into ubuntu... I tried both. It won't even let me type a password - i.e., there are no asterisks after I enter the password, however, the user login space shows my login name after I type it.

My linux OS is completely unusable. I've never seen anything so screwed-up. It is as if one-by-one over the past couple month programs just started deleting themselves and self-destructing. The only way for me to get on the net now is to double-click an html file.
Hi, when you enter your password it does not show it on the screen at all for security reasons, after you type it just hit enter, it is possible you will have to reset your password.

---

### Post by zachnap on 2011-07-02
> **wildmanne39 said:**
> Hi, when you enter your password it does not show it on the screen at all for security reasons, after you type it just hit enter, it is possible you will have to reset your password.

It just doesn't work. It works during the login prompt when ubuntu starts but it does not work in terminal at all. I hit enter even though it is blank and it says "incorrect" or something but it is not incorrect - it just doesn't function.

---

### Post by wildmanne39 on 2011-07-02
> **zachnap said:**
> It just doesn't work. It works during the login prompt when ubuntu starts but it does not work in terminal at all. I hit enter even though it is blank and it says "incorrect" or something but it is not incorrect - it just doesn't function.
Hi, here is a link to reset your password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by zachnap on 2011-07-02
> **wildmanne39 said:**
> Hi, here is a link to reset your password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I appreciate the help but why would I need to reset my password? I know what my password is cause I use it to do the initial login. Terminal just won't accept a password input. I think it is time to just do a clean install. None of this makes sense.

apt-get is a "command not found" - it knows sudo.

---

### Post by walt.smith1960 on 2011-07-02
> **Mark Phelps said:**
> Understand that, at present, this ability to go "back" to the "old" Gnome view is only available in 11.04.  Canonical has repeatedly stated that with 11.10, there will be no such option.  And, while there are rumours of Gnome 3 being such a replacement in 11.10, Canonical has not yet changed their position on FORCING everyone to use Unity in 11.10.

Forcing?  No.  Right now GNOME classic is there but it's a very long way from finished and I doubt it'll be identical to Gnome 2.x.  The "Applications" menu is blank right now, the "Places" menu works.  The biggest disappointment to me right now is that there are nowhere near the choices in the "System" settings which are the same as Unity.  There are packages available called Gnome-panel and Gnome-panel-fallback (I think. Not certain of the exact title).  Xfce & LXDE will likely be available for 11.10 as well.

---

### Post by wildmanne39 on 2011-07-02
> **zachnap said:**
> I appreciate the help but why would I need to reset my password? I know what my password is cause I use it to do the initial login. Terminal just won't accept a password input. I think it is time to just do a clean install. None of this makes sense.

apt-get is a "command not found" - it knows sudo.
Hi, you may be right about the clean install, make sure you repartition to get a clean install, and do not just install over the top of that system since it is not working correctly.

---

### Post by zachnap on 2011-07-04
Alright, I clean-installed 11,04 and things are working for now, however, firefox is still blinking videos. But whatever.

---

