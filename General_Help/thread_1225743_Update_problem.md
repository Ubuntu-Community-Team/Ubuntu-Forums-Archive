---
title: "Update problem"
date: 2009-07-28
forum: General Help
---

### Post by shankru85 on 2009-07-28
Hi,

I have been receiving this error while trying to update. This has happened suddenly. Previously it used to work fine. 


shankar@shankar-desktop:~$ sudo apt-get update
[sudo] password for shankar: 
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
shankar@shankar-desktop:~$ 


When I try to give a reload in synaptic package manager, i get the following error. Not sure what is happening. Please help 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


And then again the same error is printed 

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory



Everything was perfectly working..

---

### Post by t4thfavor on 2009-07-28
Have you rebooted the machine, it sounds like theres an orphaned process locking something synaptic needs.

---

### Post by philcamlin on 2009-07-28
reboot your pc and try again

that always fixes it for me :popcorn:

wow 3 times today im getting beat out by a second :P

---

### Post by shankru85 on 2009-07-29
Yeah guys... Thanks. That worked. :popcorn:

---

