---
title: "Error: Waiting for other software managers to quit"
date: 2010-03-20
forum: General Help
---

### Post by lsk3993 on 2010-03-20
Ok, so I'm getting exactly the same error described here: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/464020](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/464020) and according to the people on there, doing "sudo dpkg --configure -a" fixes the problem...
However when I try this I get
> dpkg: status database area is locked by another process

I've tried restarting but that doesn't fix the problem...
I'm still an Ubuntu newbie so any help is really appreciated, thanks!

---

### Post by MelDJ on 2010-03-20
try in terminal:
sudo pkill apt

---

### Post by lsk3993 on 2010-03-20
> **MelDJ said:**
> try in terminal:
sudo pkill apt
Ok, well that got rid of the error message at first but then I got the ddclient setup page in terminal when doing "sudo dpkg --configure -a".

(I had been trying to set up ddclient with terminal before in order to automatically update my dynamic ip for OpenDNS but I didn't know what to put for the ddclient settings so I gave up on it.)

I closed the window and now I get the same error (dpkg: status database area is locked by another process).

Not being able to use the software centre isn't the biggest problem ever but it would be nice to be able to use it again...

---

### Post by lsk3993 on 2010-03-20
Maybe the real problem is setting up ddclient actually... perhaps that's what's preventing software centre from working since I never finished doing it?

---

### Post by lsk3993 on 2010-03-21
BUMP, help please... anyone?

---

### Post by MelDJ on 2010-03-21
tried the command again and restart your computer?

---

### Post by lsk3993 on 2010-03-21
> **MelDJ said:**
> tried the command again and restart your computer?
Just tried it now, still not working :(

---

### Post by lsk3993 on 2010-03-21
Sorry to have to bump this again but this is really becoming a nuisance now since I can't install or uninstall anything at the moment... I can't find a solution anywhere else, help please! I'm relying on you guys :P

---

### Post by Helkaluin on 2010-03-21
> **lsk3993 said:**
> Ok, well that got rid of the error message at first but then I got the ddclient setup page in terminal when doing "sudo dpkg --configure -a".

I suspect that correctly configuring ddclient is exactly the thing you should try. The man page of dpkg states that:
```
--configure package...|-a|--pending
Reconfigure  an  unpacked  package.  If -a or --pending is given
instead of package, all unpacked but unconfigured  packages  are
configured.
```
which gives me the suspicion that the bug is caused by unconfigured packages.

EDIT: The bug report page also indicates that another possible cause is a messed up package cache. You may want to try: ```
sudo apt-get clean
```

---

### Post by lsk3993 on 2010-03-22
> **Helkaluin said:**
> I suspect that correctly configuring ddclient is exactly the thing you should try. The man page of dpkg states that:
```
--configure package...|-a|--pending
Reconfigure  an  unpacked  package.  If -a or --pending is given
instead of package, all unpacked but unconfigured  packages  are
configured.
```which gives me the suspicion that the bug is caused by unconfigured packages.

EDIT: The bug report page also indicates that another possible cause is a messed up package cache. You may want to try: ```
sudo apt-get clean
```
Thank you so much! Running **sudo apt-get clean **and then **sudo dpkg --configure -a **worked perfectly. Thanks again!

---

### Post by shebaw on 2010-03-26
I had the same problem and it fixed it for me too. 

P.S Why don't you flag the thread as SOLVED?

---

### Post by lsk3993 on 2010-03-26
> **shebaw said:**
> I had the same problem and it fixed it for me too. 

P.S Why don't you flag the thread as SOLVED?
Sorry is it not already marked as solved? Or did an admin do that for me or something?

---

### Post by lsk3993 on 2010-03-26
> **shebaw said:**
> I had the same problem and it fixed it for me too. 

P.S Why don't you flag the thread as SOLVED?
It's always nice to see other people solving problems from the threads you make :P

Also, is it not already marked as solved? Or did an admin do that for me  just now or something?

---

### Post by shebaw on 2010-03-27
I'm sure it wasn't marked as solved, anyways I'm sorry if you already marked it solved.

---

### Post by santi_ on 2010-04-08
Well, not solved for me and I have no idea what business it has trying to reconfigure LILO:
sudo apt-get clean
me@ubuntuME:~$ sudo dpkg --configure -a 
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
ERROR lilo fails for new /boot/initrd.img-2.6.31-19-generic:

Warning: LBA32 addressing assumed
Warning: /dev/sdd3 is not on the first disk
Added Karmic9.10
Added vmlinuzSlack13
Added LinuxOLD
Fatal: Default image doesn't exist.
dpkg: subprocess installed post-installation script returned error exit status 1

---

