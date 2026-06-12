---
title: "Command line only skin/mode?"
date: 2012-07-20
forum: General Help
---

### Post by sodaa on 2012-07-20
I recently installed ubuntu 12.04 and kubuntu-desktop on a macbook pro and although I am enjoying them, I am getting horrendous battery life using them.

Since I am mainly using terminal only, I was wondering if there was an interface or something I could download where I could log out and log into a shell only environment? I will occasionally need to look something up on the internet, so I would want to be able to switch back to something where I can use a browser.

I am aware I can boot into text mode by altering the kernel boot line; however, I have problems when exiting it, the ubuntu/kubuntu dektop does not appear (just by background image), and I can't get back to the text mode easily.

I am mainly interested in doing this so I can choose to save some battery power by using the shell only mode when I know I will be working in it for a long time, so I don't waste power displaying all the openGL graphics.

---

### Post by zombifier25 on 2012-07-20
I don't know how to set it to log in terminal by default, but you can log in a terminal-only desktop by pressing Ctrl + Alt + F1 at logon.

---

### Post by sodaa on 2012-07-20
I can get it to boot into text mode ok, it's just from there it's not really practical if I want to use a webrowser occasionally and then jump back etc. I was wanting to install something that could maybe be on the ubuntu login drop down menu of interfaces that I can log into (like I have KDA Plasma Workspace, Ubuntu, and Ubuntu 2D at the moment), and then I could simply log out and log back in to ubuntu or kubuntu etc.

Ctrl + Alt + F1 doesn't seem to work for me, do you mean on the logon screen?

---

### Post by MutantJohn on 2012-07-21
[http://ubuntuforums.org/showthread.php?t=912300](http://ubuntuforums.org/showthread.php?t=912300)

---

### Post by steeldriver on 2012-07-21
I may have missed the point here but if your aim is to conserve resources I'm not sure that simply switching away to a virtual terminal (while leaving the X session and all the trimmings running in VT7) is really going to do anything for you.

You could boot into console mode and then startx manually as/when required OR (I have never tried it) in principle you could do something like this

[http://askubuntu.com/questions/77191/how-can-i-use-lightdm-for-user-defined-sessions](http://askubuntu.com/questions/77191/how-can-i-use-lightdm-for-user-defined-sessions)

and then create a simple xinitrc file that loads a lightweight wm and an xterm

Or you could simply make the jump to a less resource hungry desktop like xfce or openbox.

---

### Post by Cheesehead on 2012-07-21
If you use top to look at CPU/MEM as a measure of resource consumption, using the tty consoles takes almost no resources. The X server requires some resources...but it's the applications that use X that really hog all the cycles (and increase power consumption).

So you can use a tty, and the unused X server will be a trivial drain. But if you start loading up X with firefox and empathy and other stuff, you will consume a lot more.

The 'powertop' package is a great resource for discovering settings on your system that can be changed to increase battery life.

---

