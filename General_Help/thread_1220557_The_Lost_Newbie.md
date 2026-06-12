---
title: "The Lost Newbie"
date: 2009-07-22
forum: General Help
---

### Post by Koovo on 2009-07-22
OK, I successfully installed Ubuntu onto my empty hard drive.  My laptop is an HP Pavilion dv6500t (2007 model).  Everything more or less worked out of the box, except for a few things.  Before I complain, if any of my problems have been reported before, please post a link to the corresponding thread.

If I restart my laptop, Ubuntu displays a blank screen.  WTF?  If I suspend the laptop, Ubuntu displays, yet again, a blank screen. WTF?  All this happens AFTER I open the computer.

One more thing, is there a way to configure Ubuntu to automatically enter suspend mode when the laptop is closed?  Vista does this and "wakes up" demanding a password before taking the user to his/her desktop.

---

### Post by 3rdalbum on 2009-07-23
> **Koovo said:**
> One more thing, is there a way to configure Ubuntu to automatically enter suspend mode when the laptop is closed?  Vista does this and "wakes up" demanding a password before taking the user to his/her desktop.

Right-click (?) the battery icon and choose Power Management Settings, it's in there.

---

### Post by adempewolff on 2009-07-23
Many setups have trouble resuming and suspending, a lot of these bugs have been fixed in Jaunty (9.04).  Which version are you using? Type "uname -a" into a terminal (applications > accessories > terminal) and paste it here if you are not sure.

However I have never heard of a blank screen after a restart.  Please confirm this is after "restart" not "hibernate"?

If you shut the computer down and then start it normally do you also get a blank screen or only on restart?

---

### Post by Koovo on 2009-07-24
OK, here we go:  laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

If I suspend the laptop and try to "wake it up" my monitor seems to not turn on. I can shut down and restart the computer just fine.

---

### Post by adempewolff on 2009-07-26
It looks like some people with similar models have had problems here and might have fixed them: [http://ubuntuforums.org/showthread.php?t=827128](http://ubuntuforums.org/showthread.php?t=827128) its a pretty old thread though so I don't know if it is still relevent.

I forgot that uname -a just tells me your kernel (which is the latest btw), do you know whether you are using 8.04 (Hardy Heron), 8.10 (Intrepid Ibex), or 9.04 (Juanty Jackalope)?  If you are using an earlier version than 9.04 upgrading might help.  Otherwise you might just have to hope for a fix soon (which does happen, my setup didn't work until 9.04).

A good way to assure that a fix happens sooner is to help debug it yourself.  This can be overwhelming but there are a lot of how tos out their that make it a little easier and if you start posting more technical information you might attract the attention of more knowledgable people than myself.  Here are some links to some howtos:
[http://ubuntuforums.org/showthread.php?p=3066404](http://ubuntuforums.org/showthread.php?p=3066404)
[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)

Also a couple things that made my life easier while I was waiting for a fix for my suspend problems: save tabs in firefox with "bookmark all" if you don't want to lose what you are viewing online, if you can get hibernate to work (suspend to disk vs suspend to RAM) use that--only a little slower than suspend to RAM.

Good luck!

---

### Post by philcamlin on 2009-07-26
try disabling your screensaver too:popcorn:

---

### Post by adempewolff on 2009-07-26
Oh and renaming the title of this thread to "HP Pavilion dv6500t Suspend/Resume issues" will probably help in getting the attention of people for might be able to help.

and this might help: [http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html) but I don't know if it supports Ubuntu

---

