---
title: "Thunderbird fails to read folders on samba mounted drive"
date: 2009-11-22
forum: General Help
---

### Post by Stolea on 2009-11-22
I use Thunderbird on ubuntu and windoze across two networked computers.
The home directory is on the windoze machine.
In order to share the mailfolders across the two machines (shop and office). I have set up a permanently mounted samba share in /media/samba on the (shop) ubuntu machine. This has worked perfectly in the past. Since doing a clean install for 9.10 the /media/samba folder shows all the files and I can work with documents etc with open office. However Tbird's account settings can see the relevant folder in the /media/samba/tbird/mailfolder folder, but somehow cannot read the files.
To add a twist to this, if I run the other computer (office) in Ubuntu mode and because it has samba installed on it, Thunderbird on the  (shop) machine can read the folders!

I am beginning to think that this has something to do with 9.10, because if I hook up a spare computer that runs 9.04 with identical configurations, Thunderbird can use the /media/samba/tbird/mailfolder folder.

Can anyone help with this?

---

### Post by in8sworld on 2009-11-23
I think I may be having the same problem.  I have a dual boot 8.10 / 9.10 and the Mail directory is on a CIFS share on a remote Windows 2003 server in a Windows domain.  In 9.10 its as if the folder is invisible to Tb 2.0.0.23 (mounted directory /mnt/users/me/mail with CIFS using a .credentials file) because my sig is also in that folder and that won't come up when writing a New message either.  In 8.10 all works fine, I can even get the mail fine from a windows machine I set up as a test.  I can access files fine using nautilus.

I found a solution? here:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/478509](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/478509)
I've been able to access the folders by adding 
noserverino option to my fstab line.

---

### Post by Stolea on 2009-11-23
I have come across a note in [https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") that reads:

> sudo chown root .smbcredentials
sudo chmod 600 .smbcredentials 

this will ensure that only root can access this file.

Note: Regretfully as from version 3.3.2-1ubuntu3.2 (October 2009) this approach is no longer possible together with the "user" option. A security fix prevents reading the credentials file if you don't have read access to it. You will have to pin the packages at version 3.3.2-1ubuntu3 or 3.3.2-1ubuntu3.1 to continue using this approach as non-root.

I think that this may be the case for the 9.10 version. Could somebody please clarify if this is so.

---

