---
title: "Deleting .ICEauthority on boot a good solution?"
date: 2009-11-15
forum: General Help
---

### Post by Sak on 2009-11-15
Hey everybody,

I've been running into this problem frequently since changing to 9.10, and the only solution I've found is to keep deleting my .ICEauthority file.

The situation is that boot goes normally, and I get to GDM just fine, but after logging in, and the top panel appears (I've removed the bottom panel and use GnomeDo's new docky) the entire desktop locks, even though I can cruise around it with the mouse cursor.  

After a bit of looking around, I found a solution here:

[https://answers.launchpad.net/ubuntu/+question/538]("https://answers.launchpad.net/ubuntu/+question/538")

The problem is, that this situation occurs about half the time I try to log in since moving from 9.04 to 9.10 (didn't use the upgrade, ran through a fresh install and wiped the partitions).  From what I understand here:

[http://ubuntuforums.org/showthread.php?t=206985]("http://ubuntuforums.org/showthread.php?t=206985")

.ICEauthority can go bad when you launch an app from the command line using sudo instead of gksudo.  I seldom do that, but I do launch apps from GnomeDO, and one one in particular (Freemind, which I use daily) I launch via a shell script.  It's entirely possible that this is causing my .ICEauthority to get all funky.

So after all that juicy exposition, the solution I've come up with is to simply add

rm /home/sak/.ICEauthority

to my /etc/rc.local

which nicely deletes the file for me on every boot.  Otherwise I have to reboot to get rid of the bad login, at GDM I hit ctr-f1, login, rm the .ICEauthority and cr-f7 back to GDM and can login normally again.

And now my question:

Is it such a good idea to be deleting the .ICEauthority file on every boot?  

I know it's a kludge until, hopefully, someone figures out what's actually causing the problem and a fix up-stream happens, but it seems to be working for me.  Any thoughts on another possible solution?

---

### Post by fluffman86 on 2009-11-15
I don't know of a better solution, but as long as removing it isn't causing any problems like instability, loss of settings [s]or nausea[/s], I don't see a problem.

---

### Post by Sak on 2009-11-15
Yeah, as far as I can tell, it's not causing any problems to delete it on each boot.  I had to often enough anyway when I couldn't use my desktop after login, so deleting it each boot is a solution to the nausea caused by it becoming frequently corrupt.  Still, I wasn't 100% sure what the file was used for, or if there may be some other, hidden, detriment to my workaround.

---

