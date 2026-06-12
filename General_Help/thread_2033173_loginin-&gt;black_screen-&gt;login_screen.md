---
title: "loginin-&gt;black screen-&gt;login screen"
date: 2012-07-25
forum: General Help
---

### Post by carstimon on 2012-07-25
Hi,

I am having the following problem.  I log in to my user account from the login screen, then I get, for about ~2 seconds, a black screen with a blinking dash in the upper left.  Then I am returned to the login screen.  This problem only happens on my account; I can log in to the guest account just fine.  Also, I can go to tty1 with ctrl+alt+f1 and login to my account.

Update:  I restarted, and instead of just a blinking dash I got the message:
"Stopping runlevel system V compatibility                       [ok]"
for again about 2 seconds, before being returned to the login screen.

Here is what I have done recently to my machine: 
Today I installed ubuntu 11.10 on a blank HD from an old USB stick, and immediately upgraded to 12.04.  I had a few cycles of restarting, logging in/out etc where everything worked fine.  There is one thing I am certain I did during my most recent session:  I created
~/.xsession
and added the following to it:
setxkbmap -option ctrl:nocaps       # Make Caps Lock a Control key which I got from the instructions [here.]("http://emacswiki.org/emacs/MovingTheCtrlKey#toc5")

I tried removing the .xsession file, and that didn't fix the problem.

I have attached xsession-errors.txt, which is what was in the ~/.xsession-errors file; I don't know if this is relevant.

---

### Post by steeldriver on 2012-07-25
Have you checked the ownership on your .Xauthority / .ICEauthority files?

```
ls -l ~/.*authority
```

If either has become root-owned then delete it e.g.

```
sudo rm ~/.Xauthority
```

This can happen if you are messing with startx and accidentally start it as sudo...

---

### Post by carstimon on 2012-07-25
That was exactly it, thank you!  I had fooled around with trying to restart X after I tried to change caps to ctrl.

---

