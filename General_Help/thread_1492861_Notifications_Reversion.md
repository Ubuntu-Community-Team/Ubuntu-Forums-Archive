---
title: "Notifications Reversion"
date: 2010-05-25
forum: General Help
---

### Post by Anzan on 2010-05-25
I've just dist upgraded my main production box to Lucid Lynx 10.04. All is well except the notifications have reverted to the stylr from 8.04 or so.

Instead of appearing top left and being without a border and so on they are appearing bottom right with an ugly yellow border. One thing though is that they display a timer and can be clicked off.

It's not so much a problem as just weird.

Does anyone have any ideas about how this happened or have a similar experience?

---

### Post by lisati on 2010-05-25
Post edited. Original wording might not be seen as funny by everyone.

---

### Post by Anzan on 2010-05-25
Oh, I see. Right. Thank you, no harm intended.

---

### Post by epicoder on 2010-05-25
I've never had this problem before... maybe the upgrader goofed a config file?

---

### Post by Anzan on 2010-05-25
Yes, I've been looking through the config files and cannot determine which one is for notifications.

---

### Post by kansasnoob on 2010-05-25
Let's have a look at the status of some packages, please post the output of:

```
aptitude show ubuntu-desktop|head -2 && aptitude show notification-daemon|head -2 && aptitude show notify-osd|head -2
```

And also some specific Ubuntu version info:

```
uname -a
```

```
cat /etc/issue
```

I'm assuming you're talking about "notify-osd" but on Ubuntu Desktop they appear just above center on the right.

BTW, I'm Lance from the Ayatana list :)

---

### Post by Anzan on 2010-05-25
Hi, Lance.

1) aptitude show ubuntu-desktop|head -2 && aptitude show notification-daemon|head -2 && aptitude show notify-osd|head -2


2) $ uname -a
Linux zubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux


3) $ cat /etc/issue
Ubuntu 10.04 LTS \n \l

---

### Post by kansasnoob on 2010-05-25
You didn't show the output of:

```
aptitude show ubuntu-desktop|head -2 && aptitude show notification-daemon|head -2 && aptitude show notify-osd|head -2
```

Example:

> lance@lance-desktop:~$ aptitude show ubuntu-desktop|head -2 && aptitude show notification-daemon|head -2 && aptitude show notify-osd|head -2
Package: ubuntu-desktop
State: installed
Package: notification-daemon
State: not installed
Package: notify-osd
State: installed


---

### Post by Anzan on 2010-05-25
Silly sod am I.

~$ aptitude show ubuntu-desktop|head -2 && aptitude show notification-daemon|head -2 && aptitude show notify-osd|head -2

Package: ubuntu-desktop
State: installed
Package: notification-daemon
State: installed
Package: notify-osd
State: installed

---

### Post by kansasnoob on 2010-05-25
The upgrade left "notification-daemon" installed:

> Package: ubuntu-desktop
State: installed
[B]Package: notification-daemon
State: installed[/B]
Package: notify-osd
State: installed

So I'd go to Synaptic and mark "notification-daemon" for complete removal, apply that operation, and then mark "notify-osd" for reinstallation. After that's applied the configuration files should be rewritten.

---

### Post by Anzan on 2010-05-25
All right. I've done that.

To test, I had someone in my contacts list sign out of Pidgin and back on. I had a pop-up appear in the centre of the screen notifying they were online with buttons for "Yes" "No" and "Cancel".

And now a Forecastfox pop-up appeared centre screen with the temperature and two buttons for "Okay" and "Dismiss".
 
I'll wait for something else and scrot it.

Here we go:

---

### Post by Anzan on 2010-05-25
Bonus: The notifications just hang there until an option is clicked and in the case of Forecastfox it takes over the current browser window and goes to the weather site.

EDIT:
That behaviour was so obnoxious I've reinstalled notification-daemon.

---

### Post by kansasnoob on 2010-05-25
That is the way notify-osd behaves. I don't care for it either but SABDFL made that decision.

---

### Post by Anzan on 2010-05-26
Really? I was sure that sabdfl wanted non-interactive popups, no borders, nothing clickable. These are kind of the opposite of that.

Anyway, thanks, Lance.

I'll just stay with my 8.04 style notifications in 10.04. The rest of my GNOME setup is pretty funky and non-standard anyway.

---

