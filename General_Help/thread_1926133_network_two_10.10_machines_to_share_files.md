---
title: "network two 10.10 machines to share files"
date: 2012-02-15
forum: General Help
---

### Post by lanman89 on 2012-02-15
I have a pair of Ubuntu 10.10 boxes. I just want to be able to retrieve files from one to the other. I'm VERY new to Ubuntu, actually linux of any flavor.

I followed some procedures that appeared to be more ubuntu/linux related and now have samba installed. The two computers do not see each other at all. I'm sure this has been asked a hundred times. If you can point me to an already answered thread, I would be appreciative.

one box is wireless to a router, the other directly connected to the same router.

---

### Post by jacob.david on 2012-02-15
There are list of steps to be completed. To start with,
Find out the IP address of the 2 boxes. you can run /sbin/ifconfig to find this out. First try to ping the boxes and make sure you can reach each other. (ping <IP Address>).
Assuming you can reach each other successfully and you have samba installed and configured on both the boxes. You can simply run the below command to mount
nautilus smb://<IP of the machine to be mounted>/share

In case if nautilus is not installed you can install it using 
sudo apt-get install nautilus.

Try these and post back the results. There are few other things like setting up samba users, shares, permission etc.

---

