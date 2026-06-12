---
title: "non-stop IO when box is idle"
date: 2009-08-07
forum: General Help
---

### Post by doas777 on 2009-08-07
About a week ago, i noticed that after one of my jaunty boxes was idle (monitors in standby)  for an hour or so, that the IO light on my case started going non-stop. I can hear the disks spinning. 

if I wiggle the mouse, the activity instantly stops. as soon as i am in a position to monitor the situation, the problem disapears, just to come back next time I'm not looking.

any ideas on how best to track down the process causing the IO activity?

---

### Post by dcstar on 2009-08-07
> **doas777 said:**
> About a week ago, i noticed that after one of my jaunty boxes was idle (monitors in standby)  for an hour or so, that the IO light on my case started going non-stop. I can hear the disks spinning. 

if I wiggle the mouse, the activity instantly stops. as soon as i am in a position to monitor the situation, the problem disapears, just to come back next time I'm not looking.

any ideas on how best to track down the process causing the IO activity?

To **"track"** down the problem perhaps removing the **tracker** package may help?

---

### Post by doas777 on 2009-08-07
lol. 
that seems logical, especially as I just migrated several terabytes to that box. I don't really need it indexed, so, wouldn't loose much. i'll look into it immediatly. 
Thanks!

[COLOR=Black]Update:[/COLOR] Apparently tracker and beagle are not in jaunty by default, and I don't appear to have them installed (though mabey it's another package indexing; not seeing much on google).

any other ideas?

---

### Post by doas777 on 2009-08-10
azureus/Vuze updater (which doesn't work on ubuntu anyway). my guess is that the update was seeding while the updater was sitting waiting for input.

so, lesson learned:
DPMS = false + iotop

---

### Post by mcduck on 2009-08-10
There are some other apps that use databases as well, for example the "locate"-command does database-based searches of your files so it has to update it's database every now and then.

(This shouldn't be even close tho the annoyance more complicated search tools like Tracker and Beagle can cause, since locate only works with filenames and doesn't read the contents of the files like Tracker and Beagle do, and doesn't do any real-time monitoring of the files either. Usually you don't even notice it working but since you have recently added *lots* of stuff to the system it now has quite a bit of reading to do..)

If you can't find any other reason for the I/O, then I bet it's locate. In that case my recommendation is to run "sudo updatedb" and let it do it's work when it's most convenient for you. After it's read through your new stuff it shouldn't bother you any more (unless you decide to add couple of terabytes of new stuff to the system :D)

---

### Post by touchlikefire on 2009-08-24
Hey mate,

I had this problem occur a few times with a few different boxes. I'm going to wager a guess that its the **Remote Desktop** software that is causing the high CPU usage.

I'm using a non-standard menu, so I can't check for you, but off the top of my head I think its something like **System -> Preferences -> Remote Desktop**.  Make sure that the settings are **disabled** (unticked).

There's a bug with the remote desktop that causes the CPU to race. I'm not sure why, but I had a nightmare reinstalling my server because of it, only to find out the solution was as simple as disabling remote desktop.

---

### Post by doas777 on 2009-08-25
interesting. I hadn;t considered that. I was able to track the problem to the auto updater for azureus, auto-seeding the update package. 

Luckily I've been checking out freenx so I haven;t been using vnc any more.

have fun

---

