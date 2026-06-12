---
title: "Migrate ubuntu Hardy, Lucid LTS &amp; Dapper releases to vsphere 5"
date: 2012-08-15
forum: General Help
---

### Post by NetWizKid on 2012-08-15
Greetings,

I am new to the forum, I have been asked to migrate ubuntu Hardy, Lucid LTS & Dapper releases to vsphere 5 - can anyone give me a heads up on this process.  

I have migrated many Windows systems and a few Linux but this is the first that the releases seem to be very important.  Any help you can provide will be greatly appreciated.  Thank you in advance.  :confused:

---

### Post by nothingspecial on 2012-08-15
Question moved to it's own thread.

---

### Post by TheFu on 2012-08-15
This question might get a better answer inside the Virtualization forums.  I'll take a stab, though I stopped using VMware ESX at 4.02 due to licensing costs. We switched to KVM or LXC for all our VMs and have been extremely happy.

Anyway the process we use is to:

[LIST=1]
[*]Backup the entire source server. However you do this today is probably fine.  I've been happy using rdiff-backup.
[*]Create a new VM inside your VMware infrastructure with the correct disk, networking, CPU counts and RAM.
[*]Using which ever OS installer that matches the source server, install a minimal Ubuntu server with that OS.  For 10.04 source servers, install 10.04 from an ISO. Be certain you get the 32/64-bitness perfect.
[*]Install to the new VM from the backup.
[/LIST]
That's it.  There might be some issues around the specific hardware - usually the /etc/udev stuff is easily corrected.  Mount points could be wrong, but at this stage you just wanted all the apps and OS to boot, not necessarily work.


The next steps are where you correct any specific NIC or storage issues. The more complicated these are, the more difficulty you will have.


For small VMs - less than 20G of storage, this process should be pretty easy.  After you load the base OS, you could use rsync between the two servers - just be certain to stop any DBMS related services on the source machine first.



Before you do all this work, I would **strongly suggest** that you **upgrade the older servers** to at least** 10.04** and for the simpler servers, just get to **12.04** ****before** **you do these migrations.  12.04 is very stable, so you want to get on it sooner than later so you can avoid the upgrade process.  A case could be made to do it after the migration to VMs - you'd have more flexibility, that is certain.


Regardless,** anything older than 10.04 really needs to be updated to a support LTS server release.  **Hardy and Dapper definitely need to be upgraded to newer releases now. I think hardy support ends in about 6 months. Dapper hasn't been supported for a few yrs.


VMware used to have a tool to migrate p2v, but I thought that was Microsoft only because the other OSes didn't have the same complexities of licenses tied to the hardware. I have never bothered to google for an answer for Linux migrations. Never needed that.

---

