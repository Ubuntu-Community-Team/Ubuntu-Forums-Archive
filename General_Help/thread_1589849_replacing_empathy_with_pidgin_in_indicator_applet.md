---
title: "replacing empathy with pidgin in indicator applet"
date: 2010-10-07
forum: General Help
---

### Post by xihad76 on 2010-10-07
**What i did :**

1. uninstalled empathy and installed pidgin. 

**what happened then:**

1. Default chat icon still remains under the indicator applet. if i click it , nothing happens.

2. pidgin icon is showing fine there at number 3.


What i want to do:

1. i want to assign pidgin with that default chat menu under indicator applet. if not possible,atleast i want to remove that default chat menu and replace it with pidgin at number 1 position.

i m using 10.04 lucid lynx. 

thnx!

---

### Post by dbd on 2010-10-19
I'd also like to do this, but I don't think it's currently possible.

The indicator applet is still reasonably new, and getting significant upgrades with each release. Also big things are coming for it soon, since in 11.04 the notification area will be gone, and everything will be forced to make use of the indicator applets:
[http://design.canonical.com/2010/04/notification-area/](http://design.canonical.com/2010/04/notification-area/)
So hopefully by the time that happens pidgin will be supporting the indicator applet, or we'll be in big trouble!

---

### Post by FrancoNero on 2010-10-29
I think this is a big issue especially because Empathy is a useless piece of C, and most power users still depend on Pidgin as a decent all-round messaging client that does what's promised

---

### Post by zornp on 2010-11-14
had the same problem under 10.10 maverick too.
removing the indicator applet and adding it with "add to panel..." again did the trick for me

---

### Post by Electric_Bubble on 2010-11-16
The pidgin has nested himself in the indicator applet, but as 'pidgin instant messenger' and not as 'chat' darn, annyways still beats empathy :-D the only thing bothering me now are to pop-ups when someone comes online :-S I have a massive friends list and every 2 seconds i see someone coming online, it annoys me  :-(

---

### Post by kitno84 on 2010-12-28
> **zornp said:**
> had the same problem under 10.10 maverick too.
removing the indicator applet and adding it with "add to panel..." again did the trick for me

worked for me also.  (haven't rebooted yet though, we'll see if it stays fixed)

---

### Post by mattman85 on 2011-01-20
> **Electric_Bubble said:**
> The pidgin has nested himself in the indicator applet, but as 'pidgin instant messenger' and not as 'chat' darn, annyways still beats empathy :-D the only thing bothering me now are to pop-ups when someone comes online :-S I have a massive friends list and every 2 seconds i see someone coming online, it annoys me  :-(

Go into Plugins, and choose LibNotify Popups. Configure the plugin to not show buddies signing in. Thats the first thing I found once I installed Pidgin and added Facebook IM to it!

---

### Post by dbd on 2011-01-23
> **Electric_Bubble said:**
> The pidgin has nested himself in the indicator applet, but as 'pidgin instant messenger' and not as 'chat' darn, annyways still beats empathy :-D the only thing bothering me now are to pop-ups when someone comes online :-S I have a massive friends list and every 2 seconds i see someone coming online, it annoys me  :-(

You can get rid of 'chat', so you just have 'pidgin instant messenger' by uninstalling empathy. Not quite as nice as it just saying 'chat', but at least that's not there wasting space :)

---

