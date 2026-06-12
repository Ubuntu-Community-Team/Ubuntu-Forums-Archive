---
title: "Broken icons in system tray"
date: 2010-12-06
forum: General Help
---

### Post by jonatanschroeder on 2010-12-06
Since I installed Ubuntu 10.10 Maverick in a new computer (my lab's computer), there are three broken icons in the system tray. They are black rectangles, with white borders, and a forbidden sign in the middle. I can't figure out what program is related to them, and they don't respond to left or right click. Can anyone point me in some direction? I thought about using programs like xprop/xwininfo to figure out what program they are related to and kill it, but these don't work for system tray, only for windows.

---

### Post by wilee-nilee on 2010-12-06
In the terminal run.
```
killall gnome-panel
```

This will reload the panel.

---

### Post by jonatanschroeder on 2010-12-06
This removes all the icons from the notification area, not just the broken ones. Also, when I reboot the broken icons are back.

---

### Post by jonatanschroeder on 2010-12-06
Here's a screenshot.

---

### Post by shoot2kill on 2010-12-06
are they not workspace icons? how many workspaces do you have enabled?

I maybe totally wrong but worth a shot. lol

---

### Post by wilee-nilee on 2010-12-06
> **jonatanschroeder said:**
> This removes all the icons from the notification area, not just the broken ones. Also, when I reboot the broken icons are back.

My 32 bit maverick has been buggy in two ways one, the one your having, only just the regular Icons, usually just the static window selector only showing half of the icon.

The other is the whole desktop having a strange split to the screen with a line across the top. Various versions of the desktop gone wild so to speak

I have two commands that fix these, the first I gave you for the panel.

Not really sure what the problems are and just found Maverick stable otherwise, and it is only one OS I have XP and W7 and mint 10 in a virtual, so I haven't really worried about this.

There are a lot of changes going on with the desktop in general so I figured with so many independent teams involved, that you get what you pay for so to speak, and I payed nothing.

There are so many open source distros available I either fix what I'm using or just use another.

Mint 10 seems like a nice setup, at least in the Vbox.

---

### Post by jonatanschroeder on 2010-12-06
> **shoot2kill said:**
> are they not workspace icons? how many workspaces do you have enabled?

I maybe totally wrong but worth a shot. lol

I don't remember seeing a workspace icon in the notification area before, but I assume they would move to a different workspace if you click on them, wouldn't they? Also, I have 4 workspaces (Ubuntu default), but there are three icons.

---

### Post by 101011010010 on 2010-12-06
Hello.
What happens when you change to another theme?

---

### Post by jonatanschroeder on 2010-12-06
> **wilee-nilee said:**
> My 32 bit maverick has been buggy in two ways one, the one your having, only just the regular Icons, usually just the static window selector only showing half of the icon.

The other is the whole desktop having a strange split to the screen with a line across the top. Various versions of the desktop gone wild so to speak

I have two commands that fix these, the first I gave you for the panel.

Not really sure what the problems are and just found Maverick stable otherwise, and it is only one OS I have XP and W7 and mint 10 in a virtual, so I haven't really worried about this.

There are a lot of changes going on with the desktop in general so I figured with so many independent teams involved, that you get what you pay for so to speak, and I payed nothing.

There are so many open source distros available I either fix what I'm using or just use another.

Mint 10 seems like a nice setup, at least in the Vbox.

I don't get your point. I'm a happy Linux user since 1999 and a happy Ubuntu user since about 2005, so I'm not complaining about anything, I'm just looking for a solution if someone has one. Could we please stay on topic here? Does anyone know if there is a way to remove only the buggy icons (or their respective programs) without messing with the other active programs in the notification area?

---

### Post by jonatanschroeder on 2010-12-06
> **101011010010 said:**
> Hello.
What happens when you change to another theme?

Most themes will show exactly the same three icons. Some themes (e.g. high contrast) will show a different icon, but still a broken-representation icon.

---

### Post by wilee-nilee on 2010-12-06
> **jonatanschroeder said:**
> I don't get your point. I'm a happy Linux user since 1999 and a happy Ubuntu user since about 2005, so I'm not complaining about anything, I'm just looking for a solution if someone has one. Could we please stay on topic here? Does anyone know if there is a way to remove only the buggy icons (or their respective programs) without messing with the other active programs in the notification area?

I didn't say you were complaining or unhappy did I. I only stated what I do to deal with this. This I think is a problem some are having could be any number of reasons why.

My point is if it can't be fixed there are other distros out there. I like Ubuntu, but is only one of 100's of platforms.

---

