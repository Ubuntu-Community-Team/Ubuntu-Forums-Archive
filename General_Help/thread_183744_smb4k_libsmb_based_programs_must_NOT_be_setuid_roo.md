---
title: "smb4k: libsmb based programs must NOT be setuid root"
date: 2006-05-28
forum: General Help
---

### Post by itsmeagain on 2006-05-28
Hi got a small problem with smb4k can any body help?
I have Ubuntu 5.10 running in VMware 5.0, the program runs fine I can use Network Servers and connect to remote machines XP and servers
I decided to install smb4k with Synaptic Package Manager.  I start the program and I can see the remote hard-disks, when I try to mount a hard-disk I enter the user name and password and get the error message "libsmb based programs must NOT be setuid root".  Note: I am using the correct user name and password
I have not got a clue what this error message means.
Using a terminal I have given the following commands but still no good
sudo chmod +s /usr/bin/smbmnt
sudo chmod +s /usr/bin/smbumount
Both of these two commands where excepted and returned with no errors

Thanks

---

### Post by superdexter on 2006-06-09
After I installed the samba package here is how you setup the smb4k program. I ran the following commands:

sudo chmod +s /usr/bin/smbmnt
sudo chmod 777 /usr/bin/smbumount
sudo chmod +s /usr/bin/smbumount
sudo smbpasswd -a USERNAME

Be sure to add your own username and setup a password for it. You should be able to mount and unmount shares

That should get the results you are looking for.

--disclaimer * This is what worked for me.

---

