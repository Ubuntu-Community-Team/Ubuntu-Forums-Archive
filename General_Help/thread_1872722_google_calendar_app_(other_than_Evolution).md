---
title: "google calendar app (other than Evolution)"
date: 2011-10-31
forum: General Help
---

### Post by CryptKeeper777 on 2011-10-31
I know I'm not the first one asking for apps with Google Calendar sync. But I've done a real lot of googling without finding anything that totally suits my needs...

What I want is a stand-alone calendar application with Google Calender sync. I don't need constant sync, a normal offline calendar which I can manually sync with the online Google Calendar would be fine (manually meaning that I have to press a button or run a script). I definitely don't want an app which constantly requires internet connection!
[I]
I know the calendar of Evolution mail (my preferred mail app) provides integration of Google Calendar, but that doesn't really work fine. At first it did, but once when Evolution wanted to sync when I had no internet, it kinda broke and spammed me with windows asking for the password of all integrated calendars, not accepting the real passwords but going on until I deleted the calendars. (This didn't only happen once, BTW, I gave it another chance at first...) Plus, once the connection between the Evolution and the Google calender was cut, I wasn't able to create new calendar entries (even after reconnection to the internet and restarting Evolution).[/I]

---

### Post by fragos on 2011-10-31
There's a Google calendar extension for Thunderbird that works quite well.

---

### Post by cbowman57 on 2011-10-31
Try the solution in this post [http://ubuntuforums.org/showpost.php?p=11414007&postcount=2](http://ubuntuforums.org/showpost.php?p=11414007&postcount=2)

After re-reading your post I don't know if this will help you or not.

---

### Post by CryptKeeper777 on 2011-11-01
> **fragos said:**
> There's a Google calendar extension for Thunderbird that work quite well.
But I'm not using thunderbird, and I'd generally prefer a stand-alone calendar program. 

> **cbowman57 said:**
> Try the solution in this post [http://ubuntuforums.org/showpost.php?p=11414007&postcount=2](http://ubuntuforums.org/showpost.php?p=11414007&postcount=2)

After re-reading your post I don't know if this will help you or not.
I have no idea how this could help me. I'm not even using gnome shell! :)

---

### Post by accodata on 2011-11-01
Have you thought of using sunbird?

[http://www.mozilla.org/projects/calendar/sunbird/download.html](http://www.mozilla.org/projects/calendar/sunbird/download.html)

---

### Post by CryptKeeper777 on 2011-11-01
I've stumbled over the name when I tried to found a solution with google, but I haven tried it out yet, actually. But I'll change that and report whether it's what I'm looking for.

---

### Post by fragos on 2011-11-01
Another possibility is the Google Calendar Extension for Chrome. It supports both on and offline operation. To my knowledge there are no standalone calendar applications that sync with Google Calendar.

---

### Post by CryptKeeper777 on 2011-11-01
> **fragos said:**
> To my knowledge there are no standalone calendar applications that sync with Google Calendar.
Yes there is! :-D Sunbird with [GCALDaemon]("http://gcaldaemon.sourceforge.net/features.html") is EXACTLY what I was looking for! I have a local standalone calendar app that synces with the Google Calendar without the need to be constantly online because Sunbird synces not directly with Google Calendar (and therefore doesn't produce any errors when there's no internet, unlike the Evolution calendar), but GCALDaemon synces the *.ics file with the Google Calendar *.ics file it accesses online. The Sunbird calender is thus fully usable offline. 

But GCALDaemon can also handle the Evolution calendar the same way (according to the website), so maybe I'll use the Evolution Calendar together with GCALDaemon instead of Sunbird because I use Evolution anyway as email client. We'll see. 

But anyway, problem solved. Thanks for all the answers!

---

