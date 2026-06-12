---
title: "'Kill unresponsive program' in xfce?"
date: 2009-06-29
forum: General Help
---

### Post by t0p on 2009-06-29
When I was using gnome on my hardy machine, one of the applets on my top panel was the one to 'kill an unresponsive program' - you click the icon, position the cross-hairs over the window of the app you want to kill, then click it - Bam! Process destroyed!

But my old machine is sluggish, so I decided to use xubuntu-desktop.  The xfce gui is a little snappier than gnome, so I'm thinking about making the switch permanent.  But I want that 'kill unresponsive program' tool on my top panel!

I know I can terminate processes through System Monitor, but that involves more clicks and scrolling and stuff. And that's another thing!  In gnome I could put a System Monitor launcher on the top panel, and it would open the monitor that's available in **System > Administration > System Monitor**.  But in xfce, I added 'system monitor' to the panel and it gave me a crappy display showing cpu, memory, swap and uptime.  I want the unresponsive-program-killer *and* the system monitor from gnome!  How can I get 'em?

---

### Post by sisco311 on 2009-06-29
You are looking for xkill. Add a new launcher to the panel and type xkill in the command field. I think the default keyboard shortcut for xkill is Ctrl+Alt+Esc.

---

### Post by ajgreeny on 2009-06-29
Ctrl+Alt+Esc is for kde if I remember correctly, but either way, xkill in terminal will do it, so no real bother.

---

### Post by utnubuuser on 2009-06-29
xfce-xfapplet-pluggin in synaptic?

---

### Post by t0p on 2009-06-29
Thanks all!  I went for **xkill**.  Later, when I have a moment to myself, I shall check out that xfce-xfapplet thing, to see if it can give me the system monitor I want.

---

### Post by kerry_s on 2009-06-29
for the unresponsive programs if you press the close button several times it should give you a pop up asking if you want to kill it. doesn't always work though, i use "gpe-taskmanager" as a backup, it only shows the running programs so it's easy to spot & kill the 1 you want, it will even kill root programs. it's so simple you can't go wrong.

---

