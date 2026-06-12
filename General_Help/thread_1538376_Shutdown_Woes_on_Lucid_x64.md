---
title: "Shutdown Woes on Lucid x64"
date: 2010-07-25
forum: General Help
---

### Post by psych1610 on 2010-07-25
I've been having shut down woes on Lucid x64, fully updated as of this evening with 2.6.32-24 kernel.

Every so often, sporadically, (and it seems without reason) Lucid will hang when shutting down or restarting. I've disabled splash and quiet in /etc/default/grub so I can see what the heck is happening and it appears 99% of the time this does occur unattended-upgrades is to blame with the specific error being something like "Checking for running unattended-upgrades:* Asking all remaining processess to terminate"

I can hit esc and move past this, but it will just hang somewhere else. This seems to be the main cause. I've disabled unattended-upgrades (I think) in Synaptic -> Settings -> Repositories -> Updates and unchecked "Check for Updates" completely.

I found this bug: [https://bugs.launchpad.net/unattended-upgrades/+bug/434835](https://bugs.launchpad.net/unattended-upgrades/+bug/434835) which seems similar except that if I continuously hit esc it will complete the desired action (either shutdown or restart) and come back up successfully.

Other reports which indicate this is actually solved, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418509?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418509?comments=all)
Does anyone have a solution for this that maybe just hasn't been pushed? I've read through the forum searches and I know shut down issues are common, I just want to try one last time. Someone has to have solved this. If it weren't for this, my lucid experience would be practically flawless.

I'd appreciate any light that can be shed on this. Willing to do just about anything to try and resolve it.

---

### Post by psych1610 on 2010-07-26
Just formatted and started from scratch. Still experiencing this.. bump.. please?

---

### Post by dalamauf on 2010-07-27
Exact the same for me. I installed last kernel 2.6.32-24 and VirtualBox on friday noon and the next day Apache did not start from the init.d script, the same for nxserver, and a usual command like "shutdown -h now" did not work also!!! I will try to study this "unattended upgrades" to check if it is the same issue. Would be helpful if anybody else could assert if it is a bug in this kernel.







AMD Phenom with Ubuntu 64bits 10.04.1 LTS

---

### Post by sanu01 on 2010-08-01
I have the same issue on 32 bit kernel  2.6.32-24-generic. 

Before the upgrade all was working fine. Now when i reboot i get this error
 checking for runing unattended upgrades

and have to cold reboot. 

Please help.

---

### Post by dalamauf on 2010-08-05
After installing Lucid  x64 in a Virtual Machine and check both settings (virtual and Real Workstation) I found one own wrong init.d script. After fixed it everything even the shutdown command works fine one more time.

(it is very strange that a wrong script could collapse a whole system, isn't it?)


Sorry for inconveniences.

---

### Post by LowSky on 2010-08-05
> **dalamauf said:**
> After installing Lucid  x64 in a Virtual Machine and check both settings (virtual and Real Workstation) I found one own wrong init.d script. After fixed it everything even the shutdown command works fine one more time.

(it is very strange that a wrong script could collapse a whole system, isn't it?)


Sorry for inconveniences.

Can you explain what you fixed, it can potentially help others.

Thanks.

---

### Post by dalamauf on 2010-08-30
Sure, I had this init script in /etc/init.d

#svnserver
#!/bin/sh
svnserve -d --foreground -r /media/magatzem/subversion_repo


As you can see this script does not have the classic script skeleton structure with a stop/start block.
After update system level start/stop scripts with this command:

sudo update-rc.d svnserve defaults

this server worked after every new start but others like apache or nxserver did not start anymore and what it was worse I could not execute "shutdown -h now" never more. 

Solution: to fix this script with a right structure.

---

