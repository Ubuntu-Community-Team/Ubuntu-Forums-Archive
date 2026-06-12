---
title: "KOrganizer Reminder Daemon Problem"
date: 2009-11-07
forum: General Help
---

### Post by Wolf-Ekkehard on 2009-11-07
I am getting an Error from KOrganizer Reminder Daemon that it "Could not connect to host localhost.  Connection refused".  It pops up a window every couple of minutes - very annoying.  I had hoped it would magically go away with 9.10, but it didn't :-( (Ubuntu upgrades are very stable...).  

Any help with getting rid of this problem would be highly appreciated!!

---

### Post by Wolf-Ekkehard on 2009-11-15
bump

---

### Post by ganda99 on 2010-01-25
I have the same issue as I can't get my korganizer reminders to pop up when I log on anymore. 

Is there a bigger reason for this that I've missed or is something possibly screwed up on my side? 

I find posts with similar issues but no good resolutions.

---

### Post by ganda99 on 2010-01-25
Ooops. I've been searching so much I ended up posting to the wrong thread. 

Sorry about that. 

Anyway, I can't get korgac/korganizer to launch and remind me of appointments on startup/login and I can't find any resolutions to similar problems. 

Any help would be greatly appreciated.

---

### Post by divesky on 2011-09-11
Same problem here. 

The 'start reminder daemon at login' is ticked. 
The file  /usr/share/autostart/korgac.desktop shows the following:

# KDE Config File
[Desktop Entry]
Name=KOrganizer Reminder Client
Exec=korgac %i
Icon=korgac
Type=Application
GenericName=KOrganizer Reminder Daemon Client
Terminal=false
X-KDE-autostart-after=panel
X-KDE-autostart-condition=korgacrc:General:Autostart:true
#do not uncomment the following line, else autostart fails
#NoDisplay=true
OnlyShowIn=KDE;
X-Ubuntu-Gettext-Domain=desktop_kdepim


Despite this, the daemon does not start at login and only gets activated after running KOrganizer once. The reminders pop-up soon after. But there is no point in it as most of the reminders are already old by that time...

Any known fixes?

---

### Post by divesky on 2011-09-26
For those of you who are facing a similar problem: 

I found that even if you have ticked "Start Reminder Daemon at Login", it wasn't working for me. 

So, I manually added the daemon to startup list. To do this:

System > Preference > Startup Applications

In the dialog box that comes up click on "Add" button. It provides another dialog box. On the new dialog box:

i) Give it a name like "KOrganizer reminder daemon" on the name field

[COLOR="SeaGreen"]---
[I]Aside:
The reminder daemon is called "korgac"
Do a "which korgac" on a terminal to see where the daemon is 'installed'.
The output of which command will tell you the location.
End Aside
[/I]---
[/COLOR]
ii) Under command **either** type in the location of "korgac" **or** go to the location using "Browse" button and select "korgac"

iii) Give a custom comment to remind yourself about this program later eg. "this will remind me of all events on KOrganizer at startup". 

iv) Save

v) Close "startup Applications Preferences" dialog box.

That's it. It should start giving you reminders when you log in to your computer from now on - as it is supposed to do.

---

