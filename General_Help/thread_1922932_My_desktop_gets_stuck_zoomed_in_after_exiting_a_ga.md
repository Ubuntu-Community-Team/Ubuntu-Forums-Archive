---
title: "My desktop gets stuck zoomed in after exiting a game."
date: 2012-02-09
forum: General Help
---

### Post by Anonire on 2012-02-09
I am like 3 days old using Ubuntu. I just downloaded and installed Ubuntu 11.10, I think is is the version. It's the first with Unity, I believe. I didn't even realize what Unity and Gnome were until somewhere in my searches, it dawned on me people were talking about the desktop layout along with, I assume, some minor changes to the function of the OS.

     Anyhow, I try these games that I got from "Ubuntu Software Center," and upon exiting some of them, (The first time this happened was with that RPG Alien Penguin game.) my desktop is zoomed in really close. I mean I'm having difficulty watching videos because their minimal size is too large because my desktop is so zoomed in.

In windows, this problem is easy to fix because games change the screen resolution, and if it happens to stay that way upon exiting the game, one can easily fix this by readjusting the screen resolution. 

However, in Ubuntu here, it seems the screen resolution stayed right where it was supposed to, which means it must be another issue. I tried downloading and using Compiz settings to see if I could utilize the zoom in/out feature to fix this, but it didn't seem to work. When I finally figured out that "Super" meant the windows key, I tried clicking on it for the zoom function, but all it does is number the icons on the left so that whatever number I push, the number only activates the icon. And I try using button 1 and button 2 on the mouse, since I established Super key + 1 for zoom in and Super key+2 for zoom out. By the way, the desktop didn't zoom in or out, nothing did.

So when that didn't work, I attempted put in a code via "Terminal" that I found online for reseting the desktop back to defaults:
unity --reset 
It loaded a bunch of stuff, took a several minutes, but 
it didn't put my desktop back to normal zoom.
Anyhow, I'm so new at this, I'm probably missing something very simple that any idiot can do. So if someone could kindly enlighten this idiot on how to put my desktop back to normal upon exiting a game, it would be greatly appreciated.

The only thing that did bring my desktop back to normal view was to restart my PC. However, I do not wish to do that every single time I play one of those games. And that Penguin game seems like it almost has a Fallout-esque way about it, and Fallout was sort of fun. I wouldn't want to have to deal with this issue every time I exit the game.

---

### Post by Rodney9 on 2012-02-09
You could try going to monitor settings see here how -

[http://www.myapitips.com/2011/11/02/how-to-change-monitor-resolution-in-ubuntu-11-10/](http://www.myapitips.com/2011/11/02/how-to-change-monitor-resolution-in-ubuntu-11-10/)

or another way around it is to use 

```
alt/ctrl f2 
login 
sudo killall
alt/ctrl f7
```

This will drop to the full terminal, black screen, then close everything, then drop you back to your refreshed desktop.

Rodney

---

### Post by Anonire on 2012-02-09
> **Rodney9 said:**
> 

```
alt/ctrl f2 
login 
sudo killall
alt/ctrl f7
```This will drop to the full terminal, black screen, then close everything, then drop you back to your refreshed desktop.

Rodney

That Code thing, I'm not sure exactly how to use that yet. Do I have to download a compiler like Dr Java or that one available in "Ubuntu Software Center," and use it that way or is it possible to use that code directly via the Terminal?

I tried to copy and paste the code into the Terminal window, but it didn't work right because the first command, alt/ctrl f2, and all it says, "no such file or directory," then at "login," it says "Cannot possibly work without effective root." Sudo killall requests my password.

When doing them all manually each one step by step, of course ctrl/alt f2 brings up the terminal, typing login gives the same response.

Sudo killall all only brings up a menu, and pressing ctrl/alt f7 does absolutely nothing that I can see.

---

### Post by Anonire on 2012-02-09
> **Rodney9 said:**
> 

```
alt/ctrl f2 
login 
sudo killall
alt/ctrl f7
```This will drop to the full terminal, black screen, then close everything, then drop you back to your refreshed desktop.

Rodney

I messed around with the killall command and found out that typing:
killall -u<screenname> resets my entire desktop and forces me to have to sign back in, and that manages to reset my desktop back to normal again. 

I'm going to have to figure out that code thing you were talking about because that website, I tried to follow what it was saying, and it didn't seem like I was doing anything. I didn't see any kind of change on my resolution, and it gave me resolution numbers that were way higher than even my video card can do, and my card is much better than my monitor. So I must be doing something wrong, however that code you gave me looks more promising.

---

### Post by Rodney9 on 2012-02-10
alt and ctrl and f2 are the keys on your keyboard, you hold down all 3 and that will log you out.

Then type in your login name and your password.

Then type > sudo killall and it will ask you for your password, type it in.

Then hold alt and ctrl and f7.

I do agree that it sounds like something is wrong in your monitor resolution, the above is for when you get stuck.

This wiki will help with resetting your monitors resolution etc - 

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Rodney

---

