---
title: "sbackup not working after switch to lucid"
date: 2010-06-06
forum: General Help
---

### Post by DrScum on 2010-06-06
With 9.04 I was using simple backup as backup utility. After upgrading to 10.04 it is no longer working. I have uninstalled and reinstalled the packages, can start the program change settings, save settings, add files and delete files, save settings and so on.
When I select "backup now" I get a message that a process is started in the background but that's it. no backing up occurs since even after a long time nothing shows up in the destination directory.

Any ideas what's going on?

---

### Post by quini on 2010-06-13
It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/550261]("https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/550261")

Consider subscribing to it.

Also, in the meantime you may have a look at PyBackPack:

[http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html")


Hope that helps  ;)

---

### Post by hhoyt on 2010-06-13
Same problem here.

sudo sbackupd

circumvented it for me.

Might just be me, but my testing seems to indicate sbackup is NOT a good system recovery solution. I would recommend you clonezilla all your partitions and then use sbackup for your periodic data backups.
(DEFINITELY does not hurt to have b/u redundancy !)

Cheers, Howard

---

### Post by quini on 2010-06-14
"sudo sbackupd" also works for me!

Thanks!  ;)

---

### Post by DrScum on 2010-06-14
To hhoyt:

I second your suggestion. My strategy is (was) using sbackup for periodical backups and having clonezilla images on external HD's.

---

### Post by hhoyt on 2010-06-14
> **DrScum said:**
> To hhoyt:

I second your suggestion. My strategy is (was) using sbackup for periodical backups and having clonezilla images on external HD's.

Yes, Personally, I would always want a bare metal backup handy for system recovery.
I realize sbsckup is the 'soup du jour' of rsync variants (also easiest to install), however I recommend folks try fwbackups --for the simple reason that it provides you with a LOG of what happened.

Cheers, Howard

---

### Post by johnzollo on 2010-06-21
Woooo!!!!!!!!!! Yet another Ubuntu bug!

---

### Post by DrScum on 2010-06-22
The solution is nssbackup. Nssbackup replaces sbackup. 

See bug thread [https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/550261](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/550261)
in particular KilleBob's reply "as far as I know sbackup is discontinued, instead use nssbackup [https://launchpad.net/nssbackup](https://launchpad.net/nssbackup)
it's compatible with sbackup image files" 

to install nssbackup add the following PPA to your system 
ppa:nssbackup-team/ppa
and install nssbackup using synaptic package mgr or software center. 
Ssbackup will be uninstalled in the process.

---

### Post by johnzollo on 2010-06-22
> **DrScum said:**
> The solution is nssbackup. Nssbackup replaces sbackup. 



That is not a solution -- it is a replacement.

---

