---
title: "Vmware loads into background on system start - how do I stop this?"
date: 2006-06-01
forum: General Help
---

### Post by Sammi on 2006-06-01
My topic pretty much sums it up.

I installed vmware server and ever since I have had a process running in the background called "Vmware-vmx", which takes up about 90 MB's of RAM. It shows up even though I don't run vmware server itself.

I can't find an option in the program itself to keep it from booting with the system and it doesn't show up in either BUM or System -> Preferences -> Sessions -> Startup programs.

Is it even possible to stop this process? Does anybody know how?

---

### Post by blackjack6.21.91 on 2006-06-01
Go to system --> preferences --> sessions and delete all of your sessions.  Decheck the "automatically save changes to session" thing

---

### Post by JoWilly on 2006-06-01
You should be able to stop the vmware processes with "sudo /etc/init.d/vmware stop"  (you can also use start/restart/status).

If you don't want it to automatically start at boot remove it from your runlevel.

---

### Post by Sammi on 2006-06-05
Thx for the replies. Fixed it on my own though :wink:=D>

Just didn't find the right option inside Vmware to change.

I did this:
Launched Vmware
Selected the tab for my XP virtual machine(which is the only vm I have)
Clicked on the "Edit virtual machine settings" button
Clicked the "Options" tab in the newly opened window
Clicked "Startup/Shutdown"
Then I changed the "On host startup:" option from "Power on virtual machine" to "Don't power on virtual machine"

Simple. Just didn't find the right option to change. Sry :roll:

---

### Post by Jose Catre-Vandis on 2006-11-12
If it helps anyone, vmware-server is set to start in three parts of the runlevels. In order to prevent it loading its modules on boot, remove the file links to /etc/init.d/vmware from the following folders:

/etc/rc2.d/S90vmware
/etc/rc3.d/S90vmware
/etc/rc5.d/S90vmware

As Jowilly says, you can simply start up the services by typing

/etc/init.d/vmware start

---

### Post by d3athp3nguin on 2008-02-23
I know this is an old thread, but I couldn't help adding my two cents- if you're forgetful like me and you want to have the vmware services start up automatically ONLY when you open VMware yourself, you can edit the menu entry and add the /etc/init.d/vmware start command to the VMware application shortcut.

For example, I changed my VMware link to perform this command (in KDE, right-click the menu entry or shortcut, and edit its properties.  Look for a "command" entry.):

sudo /etc/init.d/vmware start && /usr/bin/vmplayer

The && will make sure that the VMware services are successfully started before running VMware, so the program won't poo a brick when looking for services.  Note that the services will keep running after you close VMware player, but it's still better than having them add to your startup time and overhead.

Sure, you could make a bash script to get even fancier- but I like to Keep It Simple...Seriously.

---

### Post by dcstar on 2008-02-23
> **d3athp3nguin said:**
> I know this is an old thread, but I couldn't help adding my two cents- if you're forgetful like me and you want to have the vmware services start up automatically ONLY when you open VMware yourself, you can edit the menu entry and add the /etc/init.d/vmware start command to the VMware application shortcut.
.........
Sure, you could make a bash script to get even fancier- but I like to Keep It Simple...Seriously.

I know that you don't need the services if you only run local, but for the small time gain of not starting them at boot-up - and Linux will swap out the apps to free up memory if it needs to - I don't really see it as worth the trouble.

Anything that makes things non-standard runs the risk of breaking if a subsequent update restores part of the original settings that will now conflict with the modifications - and if you aren't 100% aware of what you originally did and what you can now do to fix it, you can end up wasting a lot of time "fixing" things.

---

