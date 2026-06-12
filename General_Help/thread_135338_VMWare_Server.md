---
title: "VMWare Server"
date: 2006-02-23
forum: General Help
---

### Post by xang on 2006-02-23
All..first to say, fantastic community with this distro~!


I have VMWare server beta installed, thanks to the many helpful tutorials posted in these forums. The Console comes up and I have been able to create a VM, and start it up etc. just fine. When I go in to edit the **global host ** settings, such as to change the amount of RAM (located under Host>Settings>Memory tab in the VMWare server console), the system can reserve for all running VM's (the slider tool just under "Host RAM for all virtual machines", I get the following:

"You don't have the permission to execute this operation"

Likewise I cannot adjust or edit the field in the "Connections" tab either.
I am running the console as a regular user as I have not created a VMware group as of yet. My thought was there is a config file which stores this value and the user I am logged in as does not have access to this file. I cannot locate this file. Any ideas?

---

### Post by andrewsawyer on 2006-02-24
Maybe a stupid question, but you're not running any guests when you try to change the available ram are you? I've found with Server Beta that it has a nasty habbit of auto-loading all my guest OS's each time I reboot my machine.

---

### Post by xang on 2006-02-24
Not currently running any guest OS when I try to adjust the aforementioned settings. Are you able to adjust any of those settings?

---

### Post by andrewsawyer on 2006-02-24
Sorry - I just tried and you're right.  You can't change the *total* memory allowable for all VMs whether you have machines running or not.  However, if you run sudo vmware from terminal, then it will let you change it - it lets me anyway.

---

### Post by xang on 2006-02-24
Ah excellent! Well, I will just change the command on the old custom app launcher icon I created! Cheers!

---

