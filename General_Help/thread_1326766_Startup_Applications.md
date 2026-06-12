---
title: "Startup Applications"
date: 2009-11-14
forum: General Help
---

### Post by fortyseven on 2009-11-14
I want to uncheck unnecessary applications in Startup Application Preferences, but I don't understand what this apps are for:
1. Check for new hardware drivers
2. Disk Notifications
3. GNOME Keyring Daemon
4. GNOME Settings Daemon
5. GNOME Settings Daemon Helper
6. Indicator applet
7. PolicyKit Authentication Agent
8. Seahorse Daemon
9. User folders update
Of course I saw that this apps have a description, but it confused me even more. Which apps can I disable?

---

### Post by Sin@Sin-Sacrifice on 2009-11-14
Technically all of them... but you might use some of them even if you don't know it. Such as the Disk Notifications. I would say Google each and try to understand whether or not you need them.

---

### Post by Tiganjero on 2009-11-14
> **fortyseven said:**
> I want to uncheck unnecessary applications in Startup Application Preferences, but I don't understand what this apps are for:
1. Check for new hardware drivers
2. Disk Notifications
3. GNOME Keyring Daemon
4. GNOME Settings Daemon
5. GNOME Settings Daemon Helper
6. Indicator applet
7. PolicyKit Authentication Agent
8. Seahorse Daemon
9. User folders update
Of course I saw that this apps have a description, but it confused me even more. Which apps can I disable?

Hi, I guess I'll just cut to the point :). Heres what they do:

1. Checks for new drivers for all of your hardware. (I suggest you keep it)
2. Those are notifications, like, 'Your free disk space is low blah blah' (But it's useful too, you can sometimes loose track of your free space :), like I do all the time)
3. GNOME Keyring is a daemon application designed to take care of the user's security credentials, such as user names and passwords. The sensitive data is encrypted and stored in a keyring file in the users home folder. (Yeah, you need it :P )
4. GNOME Settings Daemon handles the session settings. (Now you really need that :P)
5. Same as above.
6. The Indicator applet is the bar in the top right corner, unless you moved it, where all running applications are docked .
7. The PolicyKit model provides letting an user authenticate in order to gain the privilege to let a mechanism carry work out related to a specific action on the users behalf. (It's that thing that when you mount a partition on your HDD to Ubuntu, asks for your password)
8. Seahorse Daemon is used for seahorse front-end and provides PKCS11 services to applications. Seahorse Daemon has different functionality with Gnome Keyring Daemon which should not be removed.
9. The User folder update script helps to implement the XDG specification. (You should keep this)

I suggest you keep all of them. If you want you can remove the Disk Notifications, but they are useful too.
Hope I helped.

Cheers,
George

---

### Post by donato roque on 2009-11-14
The only safe way is to test your system (or your way of computing) without them starting right away.  Just untick the box but do not remove them in the Startup application list.  If you can't start your day without it then just tick them back.  No harm, no foult.  Ain't Linux great!

---

### Post by fortyseven on 2009-11-15
First of all, thank you very much for your replies, guys!

**Sin@Sin-Sacrifice**, I did a search about each app on Google and Ubuntu forums, but these were really hard to find. For example "Check for new hardware drivers", these words are so common that I didn't manage to find anything related to the service. As you can see, it's not a full list of applications, that's because I've found some. So I really needed to ask ;)

**Tiganjero**, you've just taught me everything I wanted to know about startup apps, really appreciate your help.

**donato roque**, yes you're right, it's really fun to learn how Ubuntu works, and now when I know about these apps I surely will try to play with startup configuration.

---

### Post by veli on 2009-11-15
> **fortyseven said:**
> I want to uncheck unnecessary applications in Startup Application Preferences, but I don't understand what this apps are for:
1. Check for new hardware drivers
2. Disk Notifications
3. GNOME Keyring Daemon
4. GNOME Settings Daemon
5. GNOME Settings Daemon Helper
6. Indicator applet
7. PolicyKit Authentication Agent
8. Seahorse Daemon
9. User folders update
Of course I saw that this apps have a description, but it confused me even more. Which apps can I disable?

1. Check for new hardware drivers - only keep if you're thinking about replacement of hardware. Otherwise, is not necessary
2. Disk Notifications - if you have enough space, you don"t really need this
3. GNOME Keyring Daemon - keep it
4. GNOME Settings Daemon - keep it
5. GNOME Settings Daemon Helper - can be disabled
6. Indicator applet - can be disabled
7. PolicyKit Authentication Agent - keep it, only if you have encrypted drives
8. Seahorse Daemon- can be disabled
9. User folders update - no need

I've been running Ubuntu for years with the above removed and haven't had any issues. Certainly, you can keep all of them running provided you have lots of RAM and CPU.

---

### Post by 3rdalbum on 2009-11-15
Keep them all on, except for Check For New Hardware Drivers (which you can do manually). Everything else should really be running.

---

### Post by fortyseven on 2009-11-16
> **3rdalbum said:**
> Keep them all on, except for Check For New Hardware Drivers (which you can do manually). Everything else should really be running.
I resisted to keep the whole list on, when I saw sound notification, bluetooth and similar apps starting always, when I'm not using them at all. Still thanks for your answer =)

**veli**, thank you for sharing your experience with me, it's really important while I'm learning Ubuntu and of course after =)

---

### Post by oldos2er on 2009-11-16
This list is a few years old, but still applicable for identifying services: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

 I never really cared for the Startup Applications app (I think it was Services in older versions of Ubuntu); it doesn't show all services. sysv-rc-conf does though, and works in 9.10 (so far). Just be careful you understand what you're turning off!

---

