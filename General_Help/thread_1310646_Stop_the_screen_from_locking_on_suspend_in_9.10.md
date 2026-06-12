---
title: "Stop the screen from locking on suspend in 9.10?"
date: 2009-11-02
forum: General Help
---

### Post by tryingtoboot on 2009-11-02
I want to make it so when I put the computer in standby or hibernate it doesn't lock the screen. I only see the option to do this for the screensaver and for automatic login. How do I do this for standby/hibernate?

---

### Post by Johndo1 on 2009-11-02
I'll catch hell for saying this but:
I kinda like 9.04 better. I have vista, 9.10 and 9.04 and 9.10 gave me lots of problems. I only bring this up because I read your other questions and since you need it fixed for your dad I thought I'd throw that out there.

Anyway for your problem.

Go System > Preferences > Screensaver and uncheck the box that says lock when screensaver is active.

And

System > Preferences > Power Management 
In there you can find some interesting things.

Hope this help.
(I'm currently in 9.04 could be different in 9.10)

Also after re-reading this and checking i'm not sure if power-management evenn has that option lsited. Try it out...

---

### Post by tryingtoboot on 2009-11-02
> **Johndo1 said:**
> I'll catch hell for saying this but:
I kinda like 9.04 better. I have vista, 9.10 and 9.04 and 9.10 gave me lots of problems. I only bring this up because I read your other questions and since you need it fixed for your dad I thought I'd throw that out there.

Well I was having a problem with the video driver in 9.04 that I thought was supposed to be fixed in 9.10 (which it doesn't look like it was) so that's why I upgraded. I want to stick with 9.10 because of the performance, but if I can't get it working I will try openSUSE 11.2 Gnome when it comes out.

> **Johndo1 said:**
> 
Anyway for your problem.

Go System > Preferences > Screensaver and uncheck the box that says lock when screensaver is active.


Already did that.

> **Johndo1 said:**
> 
And

System > Preferences > Power Management 
In there you can find some interesting things.

Hope this help.
(I'm currently in 9.04 could be different in 9.10)

Also after re-reading this and checking i'm not sure if power-management evenn has that option lsited. Try it out...
Yeah, it doesn't have the options there. I read somewhere about gconf-editor but I'm not sure what to do there.

---

### Post by Johndo1 on 2009-11-02
Check this thread out:
[http://ubuntuforums.org/showthread.php?t=201256]("http://ubuntuforums.org/showthread.php?t=201256")

Try this: (wich is in the link I provided)
```

gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false

```

If this ends up making your screen not go blank when you shut it just do these:

```

gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen True
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings True

```

---

### Post by tryingtoboot on 2009-11-02
> **Johndo1 said:**
> Check this thread out:
[http://ubuntuforums.org/showthread.php?t=201256](http://ubuntuforums.org/showthread.php?t=201256)

Try this: (wich is in the link I provided)
```

gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false

```If this ends up making your screen not go blank when you shut it just do these:

```

gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen True
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings True

```
That didn't work. When I try to put the computer in standby, the screen goes black, but the computer doesn't actually go into sleep like with the blinking power indicator like it does in XP. And when I move the mouse, it still asks for my password.

---

### Post by bigbroantonio on 2009-11-03
I had the same problem.  I did two things:

_**1.**_

[LIST]
[*]Open the terminal, and type  **sudo gconf-editor**  (you'll need to type root password)

[*]In the window that comes up go to **apps > gnome-power-manager > lock**

[*]On the right, **UNCHECK suspend and hibernate** and make sure that the **use_screensaver_settings is CHECKED**
[/LIST]

**_2. (I'm not sure if this is necessary - please let me know)_**

[LIST]
[*]In your terminal type **sudo gedit /etc/default/acpi-support**

[*]Go to the line that says **LOCK_SCREEN=true** and put a # in front of it.  So, you'll have a line that reads:  **#LOCK_SCREEN=true**

[*]Close, save and try it out.
[/LIST]

It worked for me.

Too complicated, though.  Should be much easier (especially since when you ask to automatically log in during install you assume the same would happen after standby or hibernate).

---

### Post by tryingtoboot on 2009-11-03
> **bigbroantonio said:**
> I had the same problem.  I did two things:

_**1.**_

[LIST]
[*]Open the terminal, and type  **sudo gconf-editor**  (you'll need to type root password)
[*]In the window that comes up go to **apps > gnome-power-manager > lock**
[*]On the right, **UNCHECK suspend and hibernate** and make sure that the **use_screensaver_settings is CHECKED**
[/LIST]

**_2. (I'm not sure if this is necessary - please let me know)_**

[LIST]
[*]In your terminal type **sudo gedit /etc/default/acpi-support**
[*]Go to the line that says **LOCK_SCREEN=true** and put a # in front of it.  So, you'll have a line that reads:  **#LOCK_SCREEN=true**
[*]Close, save and try it out.
[/LIST]

It worked for me.

Too complicated, though.  Should be much easier (especially since when you ask to automatically log in during install you assume the same would happen after standby or hibernate).

Even that didn't work. Maybe there were other things you checked or unchecked too?

---

### Post by bigbroantonio on 2009-11-04
The attachment shows what my gconf-editor setup looks like under apps > gnome-power-manager > lock

As for editing LOCK_SCREEN in acpi-support, I've pasted my file here:

[http://pastebin.com/d5e82bc91](http://pastebin.com/d5e82bc91)

---

### Post by bigbroantonio on 2009-11-04
Oh, and one more thing...

Make sure that in SYSTEM > PREFERENCES > SCREENSAVER the option to lock after the screensaver is UNCHECKED.

---

### Post by 3rdalbum on 2009-11-04
What about typing into the terminal:

```
sudo pm-suspend
```

---

### Post by tryingtoboot on 2009-11-09
[FONT=monospace]All those check boxes and stuff doesn't do squat. sudo pm-suspend would be great if that's what happened when I push suspend! I can't BELIEVE how something like this can't disabled, let alone a GUI option. Is everyone who makes Gnome 100% certain that everybody on earth [/FONT]wants to lock their screen when they put the computer in suspend?

I'm setting this up for my Dad so he doesn't have to use Windows. I have automatic login and all fine, but I think he'll be annoyed if he has to put in the password every time. And half the time he'll probably call me, asking me what his password is. If that's what Linux forces I'm not gonna do it. So tell me, how do you change this simple setting?!

---

### Post by mac.ryan on 2009-11-17
Annoying, that's true! Here's teh [corresponding bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/255228") in launchpad. As of today there are no known workaround for this.

---

### Post by Mothinator on 2009-11-17
Ugh.. this is annoying. Just ran into this bug on Karmic. Apparently it has existed since Intrepid.

Hopefully, it will get fixed soon.

---

### Post by pollywog on 2010-05-01
I just upgraded Karmic-to-Lucid final release and now my laptop has this bug. It did not before. I followed advice posted at :
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/255228]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/255228")
But to no avail.:(

---

### Post by pollywog on 2010-05-01
Strike that. Problem was just that "lock screen when screensaver is active" (System>Preferences>Screensaver)became checked by default after upgrade. Unticked and its OK now

---

### Post by WilliamCampbellJr on 2010-05-04
Upgraded myself from Karmic to Lucid, and I'm still having the locked screen issue under suspend, even after un-ticking the locked screen option after screen saver. Any other ideas? This is frustrating.

---

### Post by MoarningSun on 2010-05-05
Have you tried any of the possible solutions above or in the bug report? For what I'm aware these are the ways to do it:

For Lucid try [this]("http://ubuntuforums.org/showthread.php?t=1466504"): 

In Karmic you could disable the lock screen after suspend by going this route: 

Hit Alt+F2 and type "gconf-editor" (launch as user, so no sudo or gksu !!)
Go to apps > gnome-power-manager > lock and uncheck everything
Hit ctrl+alt+delete and choose suspend

This should result in no locked screen at wakeup! Mind that there are many ways to initiate a suspend in Ubuntu and this doesn't work for all of them! (Because not all methods to suspend use these particular gconf-settings) If you don't need lock screen at all you should try to disable it all together: In the gconf-editor go to desktop > gnome > lockdown and check disable_lock_screen. Does it work the way you want to now?

---

