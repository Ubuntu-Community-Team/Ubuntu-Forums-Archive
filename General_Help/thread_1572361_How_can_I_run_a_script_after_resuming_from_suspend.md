---
title: "How can I run a script after resuming from suspend?"
date: 2010-09-11
forum: General Help
---

### Post by Xenphor on 2010-09-11
I'm running Ubuntu 10.04.

What I want to do is have the xboxdrv (xbox userspace driver) run after I resume from suspend. I created a script for it to run at boot and that worked out fine but I can't figure out how to enable it after I resume. I found something that described how to resume a module from suspend and it was to be placed in /etc/pm/sleep.d. That script looked like this:

#!/bin/bash
case $1 in
resume)
/sbin/modprobe ath_pci
;;
thaw)
/sbin/modprobe ath_pci
;;
esac

That was for a wireless module to load after a suspend. What I did was replaced /sbin/modprobe ath_pci with the location of the xboxdrv at /usr/bin xboxdrv; unfortunately, that didn't work. I actually tried pointing it to my script that runs at boot but that also didn't work. 

Is there anyway I can just write a simple script that will run after I resume?

edit: Okay I also tried putting a script in another place at /etc/acpi/resume.d/xbox.sh; I had to create the folder resume.d. There I put the same script that I use at startup (which works fine) and it still won't work.

---

### Post by flood8496 on 2010-09-12
I am in the same boat. I did notice that the script in /etc/pm/sleep.d/ does run because there is a fresh process of xboxdrv running in the background but the controller does not connect up to the PC after suspend with that new process running.

Anyone else have any experience with reloading xboxdrv after resume?

---

### Post by darklegion on 2010-10-01
> **flood8496 said:**
> I am in the same boat. I did notice that the script in /etc/pm/sleep.d/ does run because there is a fresh process of xboxdrv running in the background but the controller does not connect up to the PC after suspend with that new process running.

Anyone else have any experience with reloading xboxdrv after resume?

You have to kill the old xboxdrv instance before running the new one. You should be able to put "killall xboxdrv && xboxdrv &" in a script somewhere.

---

