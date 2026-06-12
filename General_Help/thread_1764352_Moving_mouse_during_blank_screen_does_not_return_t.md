---
title: "Moving mouse during blank screen does not return to gnome desktop"
date: 2011-05-21
forum: General Help
---

### Post by TeaGoblin on 2011-05-21
An ubuntu-11.04 laptop is set to turn on the screensaver after 5 minutes of inactivity, and power management is set to blank the display after 15 minutes of inactivity.

When the screen goes blank, you're supposed to be able to move the mouse to return to your Gnome desktop. This works sometimes, sometimes not. When it doesn't, moving the mouse doesn't eliminate the black screen, although I can see the mouse cursor. ctrl+alt+del does nothing, neither do alt+tab, alt+esc or ctrl+alt+esc.
ctrl+alt+f1-12 work as they usually do, so I can "sudo /etc/init.d/gdm restart" from one of the TTYs, or via ssh.

I tested just now with setting the screensaver and power management display blanking to 1 minutes. After a minute the screen went blank (backlight on), and then after a second or two black (backlight off), and moving the mouse returned to Gnome as it should. So I don't know why sometimes it doesn't.

Two questions:
1- Which program can I run, or which service can I restart, to return to Gnome without having to kill gdm and lose all open windows?
2- What's causing this?

---

### Post by TeaGoblin on 2011-05-25
Bump, anyone?

It's not the screensaver - I set the screen to not go blank due to power management, just the screensaver, and now it doesn't do that. And knowing how poorly people generally read what others write in forums, I repeat that the screen blanking due to power management works over half the time. When it does't, the screen stays black (but the backlight is on) and I can see and move the mouse cursor, I just can't do anything else or see anything else.

---

### Post by fnog on 2011-06-02
> **TeaGoblin said:**
> Bump, anyone?

It's not the screensaver - I set the screen to not go blank due to power management, just the screensaver, and now it doesn't do that. And knowing how poorly people generally read what others write in forums, I repeat that the screen blanking due to power management works over half the time. When it does't, the screen stays black (but the backlight is on) and I can see and move the mouse cursor, I just can't do anything else or see anything else.
Hi there.

Just want you to know that you're not alone.
This is another of several issues that I've had on this last upgrade to 11.04. Since 5.04, this has been the most problematic upgrade to date... :-/

I've just disabled the blank screen under power-management settings as you mencioned.
Let's see if this workaround also works for me.

Thank you in advance for this precious tip.

Francisco Nogueira

---

### Post by chrisstankevitz on 2011-06-22
me too, same problem...

---

### Post by thenudehamster on 2011-06-22
Oddly, I can't recall having this problem with either Gnome, Unity or X-fce - but I have one machine that does it under Windoze Vista....

go figure... ;)

---

### Post by bogan on 2011-06-22
**Teagoblin** Posted:
> I tested just now with setting the screensaver and power management  display blanking to 1 minutes. After a minute the screen went blank  (backlight on), and then after a second or two black (backlight off),  and moving the mouse returned to Gnome as it should. So I don't know why  sometimes it doesn't.

Two questions:
1- Which program can I run, or which service can I restart, to return to  Gnome without having to kill gdm and lose all open windows?
2- What's causing this?I can not answer your questions, but though Mouse movement will not resume from Suspend, and sometimes will not stop a Screen Saver, on my PC running  Ubuntu 11.04 in 'Ubuntu Classic mode, pressing the 'Enter' key always does. Suspend returns via the Screen Saver,, if it does not crash into a 'Stripey Screen and hang -up there. It is a known Bug.. [B] bogan.  .:P
[/B]

---

### Post by nerollo on 2011-06-30
has anyone tried this?

ALT + F2, then:

```
unity --replace
```

---

### Post by uzd4ce on 2011-07-01
Adding my "me too" so I'll be alerted to any solutions.  For me I'd say I get stuck at the black screen about one time in five or so, and I've been ctrl-alt-backspacing to restart the desktop.

Looking forward to a solution.

Edit: Forgot to mention that I'm using Mint 11, so I'm not running Unity.  I had a similar but worse problem on Ubuntu 11.04 (ctrl-alt-backspace didn't even work).

---

### Post by hawthornso23 on 2011-07-01
I don't suffer from this problem. But reading through it all I wondered whether typing in your password followed by enter has any effect. It is just a crazy thought but maybe there is an unlock screen dialogue hiding in the darkness.

---

### Post by nerollo on 2011-07-01
tried that.. 

the screen remains black, however when you move a mouse over the place where you type in your password you can see the pointer changing from an arrow into a text pointer, no change after typing in your password and hittin ENTER tho

i think i only noticed this behaviour when the display goes to sleep when inactive

---

### Post by hawthornso23 on 2011-07-01
> **nerollo said:**
> tried that.. 

the screen remains black, however when you move a mouse over the place where you type in your password you can see the pointer changing from an arrow into a text pointer, no change after typing in your password and hittin ENTER tho

i think i only noticed this behaviour when the display goes to sleep when inactive

Interesting! This suggests my crazy idea isn't all that crazy. Did you remember to  click first on the area where the mouse pointer looks like a text pointer before typing your password and hitting enter? You want to put the focus on that invisible dialogue.

---

### Post by nerollo on 2011-07-01
yeh, i did that too

---

### Post by lunarexplorermodule on 2011-07-15
Any updates on this topic? I also have this issue using Ubuntu 64bit on a Sandy Bridge computer with Unity Desktop.

---

### Post by wildmanne39 on 2011-07-15
Hi, I am not sure this will help but you might have a look at this link.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by gspidey on 2011-07-22
Same problem here.

Is not the xorg which freezes, actually all the process seem to work properly (top from terminal 1). The problem is actually that can't back to desktop from blank screen (even the mouse is moving).

Ubuntu 11.04 with classic gnome.

---

### Post by jasil on 2011-07-28
I have the same problem with two different Ubuntu installs.
There seems to be an existing bug report of this: [https://bugs.launchpad.net/bugs/763422](https://bugs.launchpad.net/bugs/763422)

---

### Post by Dave Gravox on 2011-07-31
I'm going to add my +1 to this problem. It's quite a bug. I guess I'll have to go back to locking the screen on screen saver. Doesn't affect my Toshiba Satellite Pro L510 though.

---

### Post by ddastoor on 2011-07-31
Hi guys, i had the same problem and it wasn't even re-producable... it used to happen sometimes out of the blue.. 

Try the following:
> Uncheck the "sync to vblank" option in Compiz's OpenGl plugin... 


I read this on a forum here, but i just can't find the post any more ... The problem hasn't re-occured yet for me...

---

### Post by splashd on 2012-03-29
> **ddastoor said:**
> Hi guys, i had the same problem and it wasn't even re-producable... it used to happen sometimes out of the blue.. 

Try the following:


I read this on a forum here, but i just can't find the post any more ... The problem hasn't re-occured yet for me...

Same problem on Mint 11-- Trying this...I'll let you know

---

### Post by stryder57 on 2012-08-15
I am running Xubuntu on a toshiba laptop and experiencing the same issue. I found by hitting CTRL+ALT+F1 and then CTRL-ALT+F7(default desktop location) it brings back the desktop.

---

