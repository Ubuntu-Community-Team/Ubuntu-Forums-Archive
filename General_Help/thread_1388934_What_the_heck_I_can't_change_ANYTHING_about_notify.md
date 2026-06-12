---
title: "What the heck I can't change ANYTHING about notify-osd?"
date: 2010-01-23
forum: General Help
---

### Post by KrashKharma on 2010-01-23
notify-osd is one of my favorite things about ubuntu but the pop ups last _WAY TOO LONG_
It drives me ******* insane.

I've been googling for an hour and can't find any way to change it. Is this true?


This is literally a big enough deal that I might just un-install it. 
But... ..........that would be terrible because I think it's a fantastic app if it didn't sit there for five god damn minutes telling me about messages I read five minutes ago...








No, not literally five minutes, so don't respond saying "There's no way its five minutes" or "if it lasts that long something's wrong with your computer"


If I really can't change the timing then that's an awful call on the part of the programmers who made it. Who the hell wants an app that can't be adjusted in any way?

---

### Post by d3v1150m471c on 2010-01-23
```

sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled

```

Restart and they're gone.

---

### Post by KrashKharma on 2010-01-24
But I want it :(

I just don't want it to last as long as it does. It's like a minute and 15 seconds seriously.

---

### Post by jeff.sadowski on 2010-02-08
Maybe your wanting the same thing as me. It might be nice if individual users could filter notify's messages. Like maybe if there is a configuration tool for notify to not take messages from certain apps or maybe a regex filter I could put messages through.

---

