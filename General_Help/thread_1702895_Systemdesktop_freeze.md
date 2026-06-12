---
title: "System/desktop freeze"
date: 2011-03-08
forum: General Help
---

### Post by Jane202 on 2011-03-08
Hi All, 

I am new to Ubuntu and previously used the MAC OS.  I've learned my way around a little in terms of configuring desktop effects, but now I'm having trouble with my Desktop freezing up.

Here's what happens:
*The top panel can not be clicked on
*My internet (Firefox) works except I can not click on the Command Menus (File, Edit, etc)
*I have to manually restart my computer 

I tried to search this and the responses were either complicated or not exactly my problem.  Does anyone have information on this?

Thanks!
Jane

---

### Post by DanneStrat on 2011-03-08
> **Jane202 said:**
> Hi All, 

I am new to Ubuntu and previously used the MAC OS.  I've learned my way around a little in terms of configuring desktop effects, but now I'm having trouble with my Desktop freezing up.

Here's what happens:
*The top panel can not be clicked on
*My internet (Firefox) works except I can not click on the Command Menus (File, Edit, etc)
*I have to manually restart my computer 

I tried to search this and the responses were either complicated or not exactly my problem.  Does anyone have information on this?

Thanks!
Jane

Does it still happen after you restart

the computer?

It may be that gnome-panel got messed up.

Try to restore the panels by running

the following in a terminal(run it as one command)

(If you can't get to terminal from the menu

because of the panel, instead right-click on

your desktop and make a new "application launcher"

In the launchers "command" box type "gnome-terminal".

Now you can use that shortcut to launch terminal.)

```
gconftool &#8211;-recursive-unset /apps/panel && rm -rf ~/.gconf/apps/panel && pkill gnome-panel

```

This should bring the panels back to the

default state and possibly fix the other problems

you're experiencing.

Good luck.

---

### Post by Jane202 on 2011-03-11
Thanks!  It is still happening,though restarting it does work. I just don't like having to restart a few times a day :)

As of right now, I've been lucky and its been freezing less. Sometimes when it freezes, I let it be for a bit and then it works.  

I'm still having problems with the audio, however I'm buying *Linux for Dummies* to help me work through it.

Thanks again!
Jane

---

