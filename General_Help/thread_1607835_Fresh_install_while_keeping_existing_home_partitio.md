---
title: "Fresh install while keeping existing /home partition issues..."
date: 2010-10-28
forum: General Help
---

### Post by Kyllerss on 2010-10-28
I posted this bug report which so far has gotten no traction ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665224](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665224)) so I am hoping someone here may be able to point me in the right direction. 

To sum up, while I *can* sudo most operations, I receive permission errors when I try to invoke programs that require sudo rights (eg. System -> Administration -> Additional Drivers, or System -> Administration -> Users and Groups). These programs start up fine, but instead of popping-up the password dialog when I try to change any settings I simply get a permission error dialog box.

Here is some more background information about how I chose to install 10.10. I installed 10.10 over an existing 10.04 installation. The 10.04 install had a /home partition, which I kept. All other partitions I formatted during the installation. During the installation of 10.10 I set the installer to re-use the same admin user account I had on 10.04.

For the most part, everything works fine. I did have to delete a number of cache hidden directories, but overall all is well. The one lingering problem is the permissions issue I mentioned above. 

This seems to me to be related to some 10.04 permission uid/gid changing in 10.10. Does anyone have any idea as to what I should look for to find out how to have these programs request the admin password?

---

