---
title: "Is there a way to never show the greeter?"
date: 2009-11-02
forum: General Help
---

### Post by dborozo on 2009-11-02
Hi,

I've got a mythbuntu computer I use only as a media server with XBMC.  I recently upgraded from jaunty to karmic.  My question is if there's a way to persistently skip the gdm greeter and always launch XBMC.

In past versions of Ubuntu, the automatic/timed login settings would apply both to when gdm was freshly launched or to when it was returned to by a session ending.  Now that I've installed karmic, I can enable automatic login so that when gdm starts it loads XBMC, but if XBMC crashes (which it does occasionally), the system hangs returns to gdm without automatically logging back in.  Since there's no keyboard/mouse attached, this is an annoyance.  

I just want to know if there's some way to either remove gdm and launch using something else, or to enable automatic login in cases where gdm isn't being freshly started.

Thanks

---

### Post by Giblet5 on 2009-11-02
Click System -> Administration -> Login

Click the "Unlock" button.

Set your account to login automatically.

Put XBMC in your startup applications (System -> Preferences -> Startup Applications).

Ta da.

---

### Post by bodhi.zazen on 2009-11-02
FYI you can also set this when installing, it is an option at the bottom of the screen where you set up your user.

You can also do this from a terminal

```
gksu gdmsetup
```

---

### Post by dborozo on 2009-11-02
I'm using a standalone XBMC session (without gnome).  This solution works for automatically logging in the first time, but any time xbmc crashes, it returns to gdm and doesn't automatically login again.  Since I don't have a keyboard attached, it just hangs on the login screen.  I was wondering if there's a way to have it automatically log in when returning to gdm (not starting it fresh).

---

### Post by bodhi.zazen on 2009-11-02
yes, it is called I think timed login, you set it so that it logs you in automatically after 10-30 seconds (you pick the time).

---

### Post by dborozo on 2009-11-02
I have the timedlogin option enabled too.  The relevant section of my gdm.conf looks like this:

AutomaticLoginEnable=true
AutomaticLogin=dborozo
TimedLoginEnable=true
TimedLogin=dborozo


This seems to make it automatically login the first time, but not subsequent times.

---

### Post by bodhi.zazen on 2009-11-02
Those settings look correct to me, not sure why it is not working.

Hopefully someone who knows more can answer.

---

