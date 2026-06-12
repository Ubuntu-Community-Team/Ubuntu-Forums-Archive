---
title: "not able to login, start gdm"
date: 2010-02-05
forum: General Help
---

### Post by jnklarson on 2010-02-05
Hello, new user, just installed last evening. Ran fine, then did update. rebooted computer, see logo, but login screen is dark black rectangle, can see anything.
 
Trying to power down computer yields message that gdm-simple-greeter.desktop is not repsonding.
 
Tried do CTRL-ALT F2 (found in forum)
and issue commands
sudo /etc/init.d/dgm stop
dpkg-reconfigure gdm - but get error message "/usr/sbin/dpkg-reconfigure must be run as root"
 
So, I can run command line, but no gdm.
Any ideas? And I am a neophite with Linux.
 
Thanks in advance

---

### Post by rnerwein on 2010-02-05
hi 
where is your sudo at dpkg-reconfigure .....

sudo dpkg-reconfigure gdm 

ciao

---

### Post by jnklarson on 2010-02-05
My newbieness is going to show now...
 
sudo dpkg-reconfigure gdm did not return anything, is it supposed to?
And it did not fix the problem.
 
Tried following the instructions from this [http://ubuntuforums.org/showthread.php?t=1325901](http://ubuntuforums.org/showthread.php?t=1325901)
 
which amounts to issuing these commands...only in my case it is sda5.
 
[B]sudo bash
mount /dev/sda6 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda
update-grub[/B]

got the following error message when running update-grub
"grep:  proc/mounts:  no such file or directory  cannot find list of partitions"
 
Am I even going down the right path here?

---

### Post by jnklarson on 2010-02-06
Can anyone throw me a bone?

---

