---
title: "Can no longer hear boot sound!"
date: 2012-04-16
forum: General Help
---

### Post by Eirreann on 2012-04-16
You know that awesome sound that Ubuntu makes when you login?  Well, for some reason I can no longer hear it; in fact, it just isn't there at all.  I've rebooted about a thousand times (obvious exaggeration) and it just doesn't sound!  I'm kind of bummed; I liked that sound!  I was thinking that it could possibly be because of my installation of Xubuntu, is that it?

---

### Post by gordintoronto on 2012-04-16
Did you hear it since you installed Xubuntu? The most likely problem is somewhere in Sound Preferences.

---

### Post by Eirreann on 2012-04-17
> **gordintoronto said:**
> Did you hear it since you installed Xubuntu? The most likely problem is somewhere in Sound Preferences.

I just booted up Xubuntu and didn't hear anything there, either.

---

### Post by Eirreann on 2012-04-17
Okay, now I've uninstalled Xubuntu and I STILL can't hear anything at login!  Now I'm quite annoyed!

---

### Post by Eirreann on 2012-04-18
This is still a persisting problem; I would appreciate any help that anyone can supply!!!

---

### Post by Eirreann on 2012-04-19
Does no one not even have a suggestion?

---

### Post by tmaranets on 2012-04-19
Did you hear the startup sound before you installed Xubuntu? Check your sound settings.

---

### Post by al111 on 2012-04-19
Make sure that you didn't check 'MUTE'-

---

### Post by latinlightning on 2012-04-19
Check under Startup Applications Preferences and make sure the GNOME login sound is checked.

---

### Post by Eirreann on 2012-04-19
> **tmaranets said:**
> Did you hear the startup sound before you installed Xubuntu? Check your sound settings.
 
 Yeah, I did hear it *before* I installed Xubuntu, but I don't any more;  and even now that I have uninstalled Xubuntu I still don't hear  anything.... I looked at my sound settings but I'm not sure exactly what it is that I am looking for... everything looks fine to me; my laptop's  speakers are set as default in the Output tab and it is the only option in the hardware section....
 

> **al111 said:**
> Make sure that you didn't check 'MUTE'-

[http://tf2chan.net/dis/src/133277142475.png](http://tf2chan.net/dis/src/133277142475.png)

> **latinlightning said:**
> Check under Startup Applications Preferences and make sure the GNOME login sound is checked.

Yes, it is checked...  I'm thinking that installing Xubuntu may have altered that application in some way or other; is there any way to reinstall it?

---

### Post by Eirreann on 2012-04-20
Why do you guys respond with questions and when I answer them you don't respond to this thread again?  This is still a persisting issue, guys, I need help here.

---

### Post by Eirreann on 2012-04-20
Forget it, I was able to find a fix:

Download dconf editor if you haven't already. Then click in this order  org -> gnome -> desktop -> sound. Once in sound, click on the  theme name there (it says freedesktop if I'm not mistaken) and change it  to ubuntu (lowercase!) and exit. Log out and log back in.

---

### Post by tmaranets on 2012-04-20
If you are running Xubuntu next to Windows using Wubi,(not sure if they have Wubi for Xubuntu) go into windows and try to find a folder(most likely in your "(C)" harddrive named Xubuntu. You should have an application named "unistall-wubi". Then you can delete Xubuntu.[IMG]http://www.4shared.com/photo/yYk5SsWw/wubi.html[/IMG]

---

### Post by Eirreann on 2012-04-20
> **tmaranets said:**
> If you are running Xubuntu next to Windows using Wubi,(not sure if they have Wubi for Xubuntu) go into windows and try to find a folder(most likely in your "(C)" harddrive named Xubuntu. You should have an application named "unistall-wubi". Then you can delete Xubuntu.[IMG]http://www.4shared.com/photo/yYk5SsWw/wubi.html[/IMG]

If you had read any of the rest of the thread, you would know that Ubuntu is the only OS on this machine, and that I installed Xubuntu through the terminal... either way, refer to my last post, I found a fix.
Forgive my frustration...

---

