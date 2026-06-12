---
title: "System freezes when launching certain applications"
date: 2011-11-17
forum: General Help
---

### Post by sonoftherighthand on 2011-11-17
I've spent a couple days trying to find a solution on my own, but haven't been able to come up with anything.

When I start up any application in Wine(I've tried Adobe Digital Editions, Notepad, and Configure Wine so far), the screen freezes black with only the cursor visible but not movable. I can't even use CRL+ALT+F1 to go over to the terminal.

I've checked the system logs and haven't found anything obvious, and Wine doesn't have a log file as far as I can tell.

Just today I tried starting up KTorrent and it did the same thing. I haven't yet gone starting up other random applications to see which ones might cause the same error.

Since using Wine last, I've upgraded from Ubuntu 10.04 to 10.10.

I'd appreciate any help.

---

### Post by sonoftherighthand on 2011-11-23
Here's a little update.

I upgraded to 11.04 and switched to lubuntu (my computer is a System76 Starling netbook). Digital Editions ran in Wine for me after that, but only once. Now it's back to the same old black screen, frozen cursor, and locked system.

Even a little nudge toward discovering the problem would be greatly appreciated.

---

### Post by oldtimer7777 on 2011-11-23
> **sonoftherighthand said:**
> Here's a little update.

I upgraded to 11.04 and switched to lubuntu (my computer is a System76 Starling netbook). Digital Editions ran in Wine for me after that, but only once. Now it's back to the same old black screen, frozen cursor, and locked system.

Even a little nudge toward discovering the problem would be greatly appreciated.

I don't have a solution but an alternative...  You can install VMware, and install whatever applications you want to run in Ubuntu like this:

[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

It works the same as Wine, but faster/better.

---

### Post by sonoftherighthand on 2011-11-23
Thanks for the response. Looks promising. I do have a couple of concerns/questions:

1. If it's running the whole OS as a virtual machine, will it be restrictively slow on my netbook?

2. It looks like I need to get windows to use this, which I can't buy right now and am not willing to find a way to get a cracked copy.

I guess I'm frustrated because things used to work perfectly for me and broke when I upgraded.

I think my next line of attack is going to be checking which libraries are shared by Wine and KTorrent, since both were triggering identical problems.

---

### Post by Mr Nemo on 2011-11-23
1. Yes the VM OS will probably be slower on your machine, but that depends on how powerful of a computer you have and what kind of settings you use to create the VM. The VM OSs I use are a little slower but they are not crippled.


Unfortunately wine isn't perfect and might not run a good number of programs you want to use or might not work at all. Try to use linux alternatives instead.

Also, I know how you feel right now. I've had the same experience with wine. Frustrating right?

---

