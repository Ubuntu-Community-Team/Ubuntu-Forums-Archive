---
title: "Ubuntu 11.04 Update problems"
date: 2011-05-04
forum: General Help
---

### Post by BadboyXD on 2011-05-04
Keep getting this error when I go to my update ubuntu:
[COLOR=Blue]
Could not initialize the package information[/COLOR]

[COLOR=Blue]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/COLOR]

Anyone know how to fix this?

---

### Post by BadboyXD on 2011-05-04
Fixed the problem, shoulda know this would fix it lol.
sudo dpkg --configure -a
sudo apt-get update

All good.

---

### Post by nslegacy163 on 2011-05-10
I have the same problem but your solution didn't solve it for me...any other suggestions?

---

### Post by Kromel on 2011-05-10
I have the same results as nslegacy163.  So far, my google search skills appear to be lacking in finding a solution.

---

### Post by nslegacy163 on 2011-05-10
> **Kromel said:**
> I have the same results as nslegacy163.  So far, my google search skills appear to be lacking in finding a solution.

 I fixed mine last night with

 ```
sudo rm /var/lib/apt/lists/* -vf
 sudo apt-get update
```

I don't know why it didn't work the first time I tried it but I messed around on it for a bit and retried and it worked. You might want to try:
 
 ```
 sudo dpkg --clear-avail
 sudo dpkg --configure -a
 sudo apt-get clean
 sudo apt-get update
```

I don't know if it has "unfixed" it self like the originator's post had but once I was able to "sudo apt-get update" I let it run and then went straight to the update manager and let that run as well. That took about 10 mins with all the updates I hadn't been able to get, and I'm hoping that it had a fix!

---

### Post by unapendeza on 2011-05-11
> **nslegacy163 said:**
> I fixed mine last night with

 ```
sudo rm /var/lib/apt/lists/* -vf
 sudo apt-get update
```I don't know why it didn't work the first time I tried it but I messed around on it for a bit and retried and it worked. You might want to try:
 
 ```
 sudo dpkg --clear-avail
 sudo dpkg --configure -a
 sudo apt-get clean
 sudo apt-get update
```I don't know if it has "unfixed" it self like the originator's post had but once I was able to "sudo apt-get update" I let it run and then went straight to the update manager and let that run as well. That took about 10 mins with all the updates I hadn't been able to get, and I'm hoping that it had a fix!

I've encountered the same problem. There are multiple threads about this but they all offer the same solution as the ones you gave above. Both have worked for me, however every time I try to update the repositories the problem "unfixes" itself. Has this happened for anyone else?

---

### Post by deethu gopinath on 2011-05-18
Hi Guys,
This will fix it. Worked for me :)

sudo rm /var/lib/apt/lists/* -
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

---

### Post by samarthshah on 2011-10-18
> **deethu gopinath said:**
> Hi Guys,
This will fix it. Worked for me :)

sudo rm /var/lib/apt/lists/* -
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
hi,
I have tried it but i got an error message.
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
rm: cannot remove `-': No such file or directory
after
[B]sudo rm /var/lib/apt/lists/* -
[/B]
and 
E: Malformed line 63 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
after 
[B]sudo apt-get update
[/B]
Can you please help me out?

Thanks.

---

