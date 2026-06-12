---
title: "Can´t change priority"
date: 2011-10-23
forum: General Help
---

### Post by TooNick on 2011-10-23
Hi
When I try to change the priority with System monitor I can only make the 'nice' value higher, but when I try to make it lower (higher priority) it says: Can't change priority's process with pid 2841 to -5. Access denied. 
What should I do? I already reinstalled Ubuntu because I was getting a lot of errors, but even this doesn't help.

---

### Post by wyth on 2011-11-04
Yeah, this seems to be something new in 11.10 -- System Monitor won't change something to a higher priority unless you're running it as root. Kind of annoying. I thought maybe there was a user privilege issue, but that doesn't seem to be the case.

Probably the easiest thing to do, for now, is open gnome-system-monitor as root (from a terminal):
```
gksu gnome-system-monitor
```

---

### Post by BuddyThirteen on 2012-02-25
> **wyth said:**
> Yeah, this seems to be something new in 11.10 -- System Monitor won't change something to a higher priority unless you're running it as root. Kind of annoying. I thought maybe there was a user privilege issue, but that doesn't seem to be the case.

Probably the easiest thing to do, for now, is open gnome-system-monitor as root (from a terminal):
```
gksu gnome-system-monitor
```
Sorry to bump an old topic, but I figured it was better than starting a new thread.

I tried  this, but it creates another problem: The program whose priority I wish to change (Banshee) isn't listed in this version of the system monitor. So I can change priority but I can't see it, or I can see it but can't change priority. So I'm stuck using sys-mon to find the ID and then using terminal to renice?

Does anyone know if this was intentionally gimped (because users can't be trusted with their own systems) or if this is a bug?

---

### Post by Barhilton on 2012-06-09
To get System Monitor to display other things when you're using it as root, go to the 'view' menu, and then select 'All Processes'.

---

### Post by leelium on 2013-06-09
> **BuddyThirteen said:**
> Sorry to bump an old topic, but I figured it was better than starting a new thread.

I tried  this, but it creates another problem: The program whose priority I wish to change (Banshee) isn't listed in this version of the system monitor. So I can change priority but I can't see it, or I can see it but can't change priority. So I'm stuck using sys-mon to find the ID and then using terminal to renice?

Does anyone know if this was intentionally gimped (because users can't be trusted with their own systems) or if this is a bug?

you can make a shortcut with gksu gnome-system-monitor and it will always launch it with root privileges and set view all processes.

---

