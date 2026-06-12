---
title: "No Network after VMWare copy/clone Ubuntu 9.10"
date: 2009-11-06
forum: General Help
---

### Post by fireflytech on 2009-11-06
I tried posting a reply to the relevant topic below but I got permission denied.

<a href="http://ubuntuforums.org/showthread.php?t=333349">No Network after VMWare copy/clone</a>

Anyway, that solution for Ubuntu 6.x doesn't work for 9.10.

The solution to fix networking after a vmware copy/clone in Ubuntu 9.10 is to delete some files under udev and restart

```

# rm -fr /etc/udev/rules.d/70-*
# shutdown -r now

```

And networking will work again after the system comes back up.

The files get refreshed on boot and insert the new mac address from your vware .vmx file.


Update:

This also works if your networking is broken in virtualbox after vm copy

Update 2:

This also works for Ubuntu 10.04

---

### Post by vegemite4me on 2009-12-11
This method worked for me with Ubuntu 7.10.

---

### Post by msfz751 on 2009-12-12
Thanks for posting this solution.
This worked for me with on an Ubuntu 8.1 client running on Vmware Server 2.0 on top of a Ubuntu 9.04 host.
Alfonso R. Reyes

---

### Post by fireflytech on 2010-02-02
This solution also works for Virtualbox networking problems.

Follow these instructions to fix broken Virtualbox vm after copy.

---

### Post by paradiddle on 2010-05-27
Hello everybody! I'm fairly new to Ubuntu, linux and virtualbox. The samething happened to me. 

I don't know what Udev is so basically I used the Sudo command to what Fireflytech suggested (minus the #).  I don't know if it was the right way to do it but it worked. 
sudo rm -fr /etc/udev/rules.d/70-*
sudo shutdown -r now

---

### Post by wvrent on 2010-06-02
What about UUIDs in the fstab?  Don't you find they are messed up as well?  I know my swap doesn't mount.

---

