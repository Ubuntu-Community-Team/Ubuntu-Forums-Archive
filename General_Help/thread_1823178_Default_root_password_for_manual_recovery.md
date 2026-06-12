---
title: "Default root password for manual recovery"
date: 2011-08-11
forum: General Help
---

### Post by scavmartin on 2011-08-11
Hi All,

I have an ubuntu 11.10 installed on a esxi server. Today we rebooted it and it could not mount the NFS shares as it appears to be trying to mount before the interface is up. This would not be an issue as if I could login I could change the init order. My issue is that the server never finishes to start up, even when I press "S" to skip the mounting it only seems to take affect for one of the two failed mounts. In this starte the server does repsond to ping but I cannot ssh into it.

Due to this I tried to press "M" for manual recovery, unfortunately this then prompts me for the root users password. No password was ever set for the root user as we utilize sudo as that is now default in ubuntu so no one has ever logged in or changed the root password. In this scenario as this is how ubuntu's default install is done what do I enter for the root password in the manual recovery mode?

I am really stuck here as "S" does not actually skip the mounting and complete the startup cycle, or it cannot get the "S" through the vmware console interface, although I can always get it to skip the first mount, I never cannot get it to say to skip the second mount point (see scrrenshot) even when holding down "S" during the whole boot. And the "M" gets me nowhere as I cannot get passed the root password, the "M" is also hard to time for it to work if it is not hit exactly when that line shows it does not work (I assume similar issue to skipping the second mount). Also when I press ctrl-d when in the manual recovery process the server just sits there and does not continue to boot.

The mounts in question are NFS and are not needed to boot the OS, they are needed to start apache but that should not prevent ubuntu from starting.

I am not a linux newbie and I have been using debian\ubuntu for 10 years. I know how to fix the issue for future reboots, but I cannot access my system to fix it.

Please help!!

Thanks,
Shaun

---

### Post by haqking on 2011-08-11
> **scavmartin said:**
> Hi All,

I have an ubuntu 11.10 installed on a esxi server. Today we rebooted it and it could not mount the NFS shares as it appears to be trying to mount before the interface is up. This would not be an issue as if I could login I could change the init order. My issue is that the server never finishes to start up, even when I press "S" to skip the mounting it only seems to take affect for one of the two failed mounts. In this starte the server does repsond to ping but I cannot ssh into it.

Due to this I tried to press "M" for manual recovery, unfortunately this then prompts me for the root users password. No password was ever set for the root user as we utilize sudo as that is now default in ubuntu so no one has ever logged in or changed the root password. In this scenario as this is how ubuntu's default install is done what do I enter for the root password in the manual recovery mode?

I am really stuck here as "S" does not actually skip the mounting and complete the startup cycle, or it cannot get the "S" through the vmware console interface, although I can always get it to skip the first mount, I never cannot get it to say to skip the second mount point (see scrrenshot) even when holding down "S" during the whole boot. And the "M" gets me nowhere as I cannot get passed the root password, the "M" is also hard to time for it to work if it is not hit exactly when that line shows it does not work (I assume similar issue to skipping the second mount). Also when I press ctrl-d when in the manual recovery process the server just sits there and does not continue to boot.

The mounts in question are NFS and are not needed to boot the OS, they are needed to start apache but that should not prevent ubuntu from starting.

I am not a linux newbie and I have been using debian\ubuntu for 10 years. I know how to fix the issue for future reboots, but I cannot access my system to fix it.

Please help!!

Thanks,
Shaun


I can only assume a root password has been set and enabled if it is asking for one, other than that is should be your own credentials if you have sudo permission

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by scavmartin on 2011-08-11
Hi All,

The root password was never set ever. We have a user "isovera" that was the default user created during install and has sudo privileges. We never added any other user nor did we set the root password.

If what you said is true what user account should be prompted upon entering "M" for manual recovery?

I saw this as just an oversight in ubuntu and I assumed that message had come from before ubuntu did not have you set the root password upon install. And the oversight being that no root password is being set so it should have been changed to allow the default or sudo users to login, which would then change the prompt to a username, and password instead of just password.

I can assure you for this install no root password has been set, if I can gain access I would happily prove it with /etc/shadow

Thanks,
Shaun

---

### Post by fqowehf on 2011-08-11
Try using fakeroot. To install, run:

apt-get install fakeroot.

if you dont trust me, then use: sudo [command]

---

### Post by haqking on 2011-08-11
> **NullCity said:**
> Try using fakeroot. To install, run:

apt-get install fakeroot.

if you dont trust me, then use: sudo [command]

How is he gonna do that, he cant login to a prompt to do it, and the system is not booting so i am assuming not network connectivity.

---

### Post by haqking on 2011-08-11
The image you show does not show anything asking for root ?

can you post the prompt ?

---

### Post by sisco311 on 2011-08-11
sulogin is patched in Ubuntu. If the root account password is locked, you aren't prompted for any password just dropped directly in the root shell. 

Try to boot into recovery mode and fix the issue from there.

---

