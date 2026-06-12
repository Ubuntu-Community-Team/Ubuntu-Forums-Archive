---
title: "possible ubuntu/gnome virus?"
date: 2010-06-01
forum: General Help
---

### Post by plutoniumpenguin on 2010-06-01
I'm on a clean Ubuntu (Lucid) installation.  With no obvious (i.e. deliberate) changes in the preferences, my computer will, on boot up, open an infinite number of "windows" (they are not true windows, but are designated as such on the bottom panel).  I looked in the system monitor for the responsible process, but the process in question stops/starts itself with such rapidity that it is impossible to kill it.  Even removing the bottom panel completely does not solve this problem (i.e. the process still keeps going, but you just don't have any visual evidence).  Has anybody else come across this problem?  If so, is there any sort of solution?  It doesn't seem to be doing any real harm to the system, I only bring up the possibility of a virus because, well, I can't imagine what utility could possibly come from it.

---

### Post by QIII on 2010-06-01
What process is it -- or can you even get that by watching the system monitor.

---

### Post by mkvnmtr on 2010-06-01
That happen to me from time to time. I always find that something has fallen and come to rest on the keyboard. Thus my virus is operator induced. You might have a stuck key if your desk is not as messy as mine.

---

### Post by plutoniumpenguin on 2010-06-01
The process is not marked with any kind of name; all I see is a blue diamond.  The process ID seems to change every time it is stopped and started again.  I don't really have any confidence that the system monitor is giving me real time information on this situation --- in fact I think the opposite is true, because immediately after boot-up the proliferation of these bogus "windows" is far more rapid (on the order of, say, 50 per second --- very rough guess) than the speed at which the processes are observed to stop/start in the system monitor (on the order of 1 sec).  

Oh, yeah, I have tried unplugging the keyboard --- no change.  So I'm pretty confident it's not any "stuck keys".

---

### Post by plutoniumpenguin on 2010-06-01
I have no idea how to mark the thread as "solved", but I've managed to fix it.  Here's what happened:

Yesterday I changed the gconf settings /apps/nautilus/preferences/show_desktop to 'false', instead of the default 'true'.  No problem, until I rebooted the computer.  I tried rebooting the computer several times, always with the same outcome.  Anyways, simply setting the gconf value back to it's default solved the problem.  I guess this should be bug-reported or something.

---

