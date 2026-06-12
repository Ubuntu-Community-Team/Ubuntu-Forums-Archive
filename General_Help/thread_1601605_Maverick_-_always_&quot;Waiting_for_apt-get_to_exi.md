---
title: "Maverick - always &quot;Waiting for apt-get to exit&quot; !!"
date: 2010-10-20
forum: General Help
---

### Post by tamer_radi on 2010-10-20
Hi, I've upgraded to Maverick Meerkat few days ago and it gone well

The problem is .. 
Software Center is unable to install any program, it just shows "Waiting for apt-get to exit" , and never moves on
though I can still install programs using apt-get from command line

Today, Ubuntu update failed because of the same problem
the Update Manager isn't showing any updates to install
and clicking the "Check" button shows the same message > Waiting for apt-get to exit

So I closed the update manager and opened my Terminal and typed ```
sudo apt-get update
```
I got this:
> E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/



PS: there is a note ,**I don't know if it is related or not**, I noticed also that my CPU is always busy ( range from 60% to 100% ) , even when I am not opening anything , gnome-system-monitor process is eating up the remaining CPU

Any help ?? 
Thanks in advance

---

### Post by sikander3786 on 2010-10-20
A dumb question at first but did you restart your PC and recheck?

Also make sure any other package manager like Synaptic or Update Manager, Software Center, apt-get are not running simultaneously. Only one will work at a time.

---

### Post by TBABill on 2010-10-20
Next time it happens try
```
sudo apt-get upgrade
```
 
It may be telling you it downloaded updates and needs to finish the process or needs to install the ones it already downloaded? I know mine won't let me do anything if the indicator in the upper right turns red, meaning you must restart to finish the install or update process already underway.

---

### Post by tamer_radi on 2010-10-20
Well, the problem solved itself :D
I opened the Update Manager, and clicked "Check"
instead of showing "waiting for apt-get to exit"
the Manager told me to insert the Ubuntu CD ! then it updated some programs ( kernel was one of them ) and screen flickered several times , and desktop effects stopped to work also
after the update , I restarted , and everything is OK now !

---

### Post by Jebtrix on 2010-10-20
..insert the Ubuntu CD? Never seen that. I'm guessing maybe you have the Ubuntu CDROM set as an active software source? I'd uncheck that otherwise every apt-get update will look for the cdrom.

---

### Post by sikander3786 on 2010-10-21
> **Jebtrix said:**
> ..insert the Ubuntu CD? Never seen that. I'm guessing maybe you have the Ubuntu CDROM set as an active software source? I'd uncheck that otherwise every apt-get update will look for the cdrom.
+1

You can edit the Software Sources from Software Center > Edit > Software Sources and uncheck the CD-ROM.

---

### Post by deepee on 2010-10-25
> **sikander3786 said:**
> A dumb question at first but did you restart your PC and recheck?

Also make sure any other package manager like Synaptic or Update Manager, Software Center, apt-get are not running simultaneously. Only one will work at a time.

Yep, that did the trick. I re-booted, then went to Update Manager, got the stuff thataway. Before that, the apt-get message hung things up when clicking on that red icon. Thanks as always to the Ubuntu community.

---

### Post by baobab33 on 2011-12-08
In this situation, I don't know why but it actually seems that the aptitude lock has not been removed from the previous update/upgrade

So, you just remove it doing this :
```
sudo rm /var/cache/apt/archives/lock
```

and it does the trick !

---

