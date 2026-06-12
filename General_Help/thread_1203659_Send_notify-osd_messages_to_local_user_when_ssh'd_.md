---
title: "Send notify-osd messages to local user when ssh'd in?"
date: 2009-07-03
forum: General Help
---

### Post by SoftwareExplorer on 2009-07-03
Consider the following situation: I'm at school, on computer a with ssh (maybe putty if I'm on windows on computer a) and I'm doing my update rounds of: login to computer b, run sudo apt-get update&&sudo apt-get upgrade,
and then repeat with c, d, e, f and so on. Furthermore, the updates include a new kernel, so I have to restart. Is there a command that I can run from ssh prompt to send a message using notify-osd to whatever user may be logged in at the physical machine?

---

### Post by SoftwareExplorer on 2009-08-02
Bump.

---

### Post by lswb on 2009-08-03
notify-osd was made primarily to be pretty, I don't think it is actually useful yet!

---

### Post by SoftwareExplorer on 2009-08-03
Well I'm able to send messages to myself through the command line, but I can't log into the specific session of the user via ssh? It would start a separate login normally. How would I get around that?

---

### Post by SoftwareExplorer on 2009-08-22
I think I could figure out the rest if I could just make my ssshed shell part of an existing session, just like if the person on the existing session ran the terminal from the menu.

---

### Post by t0p on 2009-08-22
There's the [**msg**]("http://kb.iu.edu/data/acjl.html") command, also [**write**]("http://kb.iu.edu/data/acjl.html"), but these are command line utilities which (I think) need both users to be logged into a terminal.  You could use the **mail** command to send an email between machines, but there you also have the issue of notification to handle.

---

### Post by lswb on 2009-08-22
I think that in order for this to work, each user who is to receive notifications would have to run a command in his session that would in effect "subscribe" to the notifications you are trying to provide. I say this because X won't allow writes to a user's display from other users, not even root. In fact, take look at the startup programs for a gnome session (Main menu/System/Preferences/Startup Programs) I believe you will see a program there that accounts for most notify-osd message you are currently receiving, and any others would be the result of some program run subsequent to session startup.

With the dnotify or inotify-tools packages, a script could be written that would use notify-osd to popup a message when a file is written to some specified directory. The script could be included in the users session startup applications. Or if instant reaction to the message is not necessary, the script could say run a loop that checks for a message file then sleeps for 60 seconds. A cron job may seem like an obvious alternative, but getting cron to reliably display something on an X display can be problematical.

---

### Post by SoftwareExplorer on 2009-08-23
doesn't notify-osd use dbus also? IIRC the package to use notify from the command line usaully needs to be installed. Can users send dbus messages between different X sessions/screens?

---

### Post by lswb on 2009-08-23
> **SoftwareExplorer said:**
> doesn't notify-osd use dbus also? IIRC the package to use notify from the command line usaully needs to be installed. Can users send dbus messages between different X sessions/screens?

That seems like a really good idea. I know for example that Network Manager uses dbus to tell applications if a network connection is up. Unfortunately I don't know enough about dbus to suggest a way to actually implement it. There is a dbus-send cli tool for sending dbus messages and also a dbus-monitor command. I'm looking at the man pages for dbus-send and dbus-monitor now and it seems like they could be used. I have a terminal open where I've run dbus-monitor, and when I unplug my laptop power supply for instance, I see the dbus messages resulting from that.

I believe the user would still need a session-startup program running to check for the messages, but I might be wrong or maybe there is already some program in the default startup programs that can be used.

The man pages for the dbus commands suggest [http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus) for more info. Also maybe you could start a new thread with dbus in the title and someone more knowledgeable about dbus might notice and reply with some ideas. 

I think your original idea would be very useful and could be expanded into a more general method allowing logged in users to send notification messages to each other (if desired by the targeted user).

---

### Post by SoftwareExplorer on 2009-08-26
> **lswb said:**
> That seems like a really good idea. I know for example that Network Manager uses dbus to tell applications if a network connection is up. Unfortunately I don't know enough about dbus to suggest a way to actually implement it. There is a dbus-send cli tool for sending dbus messages and also a dbus-monitor command. I'm looking at the man pages for dbus-send and dbus-monitor now and it seems like they could be used. I have a terminal open where I've run dbus-monitor, and when I unplug my laptop power supply for instance, I see the dbus messages resulting from that.

I believe the user would still need a session-startup program running to check for the messages, but I might be wrong or maybe there is already some program in the default startup programs that can be used.

The man pages for the dbus commands suggest [http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus) for more info. Also maybe you could start a new thread with dbus in the title and someone more knowledgeable about dbus might notice and reply with some ideas. 

I think your original idea would be very useful and could be expanded into a more general method allowing logged in users to send notification messages to each other (if desired by the targeted user).
Ok, I'll start another thread. I remember reading some ubuntu wiki page that was about adapting your software to use notify-osd and it actually told you what command to send, but I couldn't figure out how to do it properly with dbus-send (I think that was the command). So if anyone knows where that page is, it would be a big help with a new thread. Thanks!

---

### Post by SoftwareExplorer on 2009-08-26
I also read the freedesktop dbus link, but I didn't help the non-programmer that I am.

---

