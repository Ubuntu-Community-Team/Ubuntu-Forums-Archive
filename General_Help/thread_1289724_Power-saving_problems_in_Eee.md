---
title: "Power-saving problems in Eee"
date: 2009-10-12
forum: General Help
---

### Post by imaqt55 on 2009-10-12
I recently installed Ubuntu 9.04 Netbook Remix on my Eee 1005HA netbook.  I am new to Linux, and am trying to get some simple power-saving options to work.  I have set it to suspend after being idle for a certain amount of time.  This works if I leave the screen open, but not if it is closed.  If the screen is closed, it will never suspend, it just stays on and gets EXTREMELY hot.  Any suggestions would be appreciated.

---

### Post by P4man on 2009-10-13
Im sure it possible to configure it elsewhere, but as Im not a laptop right now, try this: press alt+F2 and type "gconf-editor". Then browse to apps > gnome-power-manager > buttons. There you have lid_ac and lid_battery where you can define actions what to do in either case. (Im pretty sure you can configure this in system > preferences >  power management too)

---

### Post by imaqt55 on 2009-10-14
Ok, so maybe I wasn't clear enough in my original post.  I already did this, and in the power management settings, I have it set to suspend after being idle for 11 minutes (on both battery and ac power).  I want it to do this regardless of the status of the lid (and there no separate option), but it just doesn't work if the lid is closed - it never suspends.  If the lid is open, it suspends after 11 minutes just like it should.

I have tested the other options - like if I set it to suspend when I close the lid, that works.  But I only want it to suspend if it's been idle for a few minutes, not every time I close the lid.

---

### Post by P4man on 2009-10-14
So you dont want it to go to sleep when you close the lid, except only 11 minutes later? May I ask why?

---

### Post by imaqt55 on 2009-10-14
I don't want it to sleep every time I close the lid (I close it whenever I am not using it for a few minutes).  But I do want it to sleep if I close the lid and then forget about it.  The other night after I set it to sleep after 30 minutes, I woke up the next morning and it never went to sleep, so it was so hot, I couldn't even touch the touchpad.

It is pretty normal to want your computer to sleep after a certain amount of inactivity.  Clearly something is wrong if this works when the screen is open but not when it is closed.

---

### Post by P4man on 2009-10-14
> **imaqt55 said:**
>  Clearly something is wrong if this works when the screen is open but not when it is closed.

Someone else would argue "something is wrong" if the laptop suspends after 11 minutes despite him setting not to go to sleep on closing the lid and having an option to seperate each possible combination of lid open/close and battery power on/off to control when or not to go to sleep might be confusing.

Anyway, have a look in /etc/laptop-mode/laptop-mode.conf. Open it in an editor as root. So either open a terminal or press alt F2, then type 

```
gksudo gedit /etc/laptop-mode/laptop-mode.conf
```

I see this:
```

#
# Enable laptop mode when on battery power.
#
ENABLE_LAPTOP_MODE_ON_BATTERY=1


#
# Enable laptop mode when on AC power.
#
ENABLE_LAPTOP_MODE_ON_AC=0


#
# Enable laptop mode when the laptop's lid is closed, even when we're on AC
# power? (ACPI-ONLY)
#
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0
```

Perhaps changing that last option to 1 might help, assuming it does go to sleep after 11 minutes now when on batteries.

---

### Post by imaqt55 on 2009-10-14
I have the same problem when it is on battery power - never sleeps when the lid is closed.  

I hate to compare it to windows, but to me, windows makes much more sense in this case - I can set it to suspend immediately when I close the lid, or to suspend after some period of inactivity.

Perhaps this is not a bug, however, if you are suggesting that on any laptop using Ubuntu it is impossible to set it to sleep after a period of inactivity when the lid is closed?

---

### Post by P4man on 2009-10-14
> **imaqt55 said:**
> I have the same problem when it is on battery power - never sleeps when the lid is closed.  

I hate to compare it to windows, but to me, windows makes much more sense in this case - I can set it to suspend immediately when I close the lid, or to suspend after some period of inactivity.

Perhaps this is not a bug, however, if you are suggesting that on any laptop using Ubuntu it is impossible to set it to sleep after a period of inactivity when the lid is closed?


Dont know, never tried it as I like my laptop to go to sleep when I close the lid, it wakes up about as fast as I can open it (I disabled the lock on resume), so why not. I can check on my laptop tomorrow (left it at work), but I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/37626](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/37626)

Perhaps you can contribute your findings to it.

---

### Post by imaqt55 on 2009-10-14
Thanks for the suggestion - it seems that someone does have a fix for this problem, though I'm not sure how to do it.  He said to comment out some of the text "in gpm-manager.c at the top of idle_change_cb():" which apparently causes it to ignore the idle state when the lid is closed.  Only problem is, I have no idea how to get into gpm-manager.c - any suggestions?

---

### Post by P4man on 2009-10-14
> **imaqt55 said:**
> Thanks for the suggestion - it seems that someone does have a fix for this problem, though I'm not sure how to do it.  He said to comment out some of the text "in gpm-manager.c at the top of idle_change_cb():" which apparently causes it to ignore the idle state when the lid is closed.  Only problem is, I have no idea how to get into gpm-manager.c - any suggestions?

He modified the source code and recompiled it. Not the easiest thing to do, but maybe someone else can talk you through it. I can only give you the rough version: install build-essentials, download the source code (sudo apt-get source <package name>), change the source, compile. Heh.

---

