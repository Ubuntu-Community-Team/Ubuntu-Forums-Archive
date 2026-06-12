---
title: "Unsolved problem (file sharing between two systems)"
date: 2010-07-15
forum: General Help
---

### Post by Mthbk1 on 2010-07-15
I had posted my issue with filesharing between two ubuntu systems (ubuntu 9.04 on PC & Ubuntu 10.04 on Laptop) [here]("http://ubuntuforums.org/showthread.php?t=1528372") i.e in the networking section of this website which still remains unsolved.
Please solve this problem as I am having a hard time in data collection from my PC (approx 200 gb of softwares & 80 gb of videos) with a 4 gb pendrive :(

[I've just got a cross-over cable as my medium for connection]

---

### Post by bobcollard on 2010-07-15
Try Samba.

---

### Post by endotherm on 2010-07-15
ok, here is the easiest possible solution. it;s not really for persistent regular use (use samba for regular filesharing if you have the need), but will get you going quickly. be careful if the boxes are connected to the internet as this config is not safe enough to be exposed to the public network. 

these instructions assume you already have a network between the two machines. post back if that is not the case. it also assumes that you are using the same username and password on both boxes. 

ok, on the system you want to get data from, install openssh-server with 
```
sudo apt-get install openssh-server
```

after the install is complete, reboot (not technically required, but why not...)

now go to the machine you wish to access the data on. 
open a nautilus window to anywhere ("places -> home" for instance). 
hit Ctrl + L to put nautilus in location mode (so you can type in a path)
then enter 
```
ssh://<IPaddressOfServer>
``` and hit enter. you will be prompted for a password. provide it. now the nautilus window will show you the / partition on the server box. 

hth and let us know if you have any problems with it.

---

### Post by ajgreeny on 2010-07-15
To use endotherm's solution is probably best for the occasional file transfer and is also the way I do it with my wife's machine.

You do not need to have the same username and password on both machines; as long as you know the password of the machine you are connecting to it can be done.

I use the menu item Places->Connect to Server, and in the box that appears enter "ssh" in the top dropdown box, enter the username@ip_address in the second, and tick the "Add Bookmark" button.

If you have the user and ip correct you will get a password dialog box appear, and will be connected, though the first time an error message will appear that tells you it can be ignored as it is the first time of connecting.

There is a lot more info on ssh connections and increasing their security here:-
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by meburke on 2010-07-15
Uhh..., I´ve been a UNIX user for years and there have always been a dozen ways to network *NIX systems and share resources. SSH, Telnet, remote login (rlogin), Samba, NIS, VPN and lots more. The fact is, if you set up your /etc/hosts file right, you can see the resources on other systems just as if they were mounted filesystem on your local system even if they reside on a remote system across the country. I´ve got clients with farms in South Texas and New Mexico who enter transactions where they are, get their accounting processed in Houston, and print receipts in their warehouse. It takes a bit of planning, but I´d start with a good book on UNIX networking and go from there.

---

### Post by endotherm on 2010-07-15
> **meburke said:**
> Uhh..., I´ve been a UNIX user for years and there have always been a dozen ways to network *NIX systems and share resources. SSH, Telnet, remote login (rlogin), Samba, NIS, VPN and lots more. The fact is, if you set up your /etc/hosts file right, you can see the resources on other systems just as if they were mounted filesystem on your local system even if they reside on a remote system across the country. I´ve got clients with farms in South Texas and New Mexico who enter transactions where they are, get their accounting processed in Houston, and print receipts in their warehouse. It takes a bit of planning, but I´d start with a good book on UNIX networking and go from there.
that is true, but the op seems both frustrated and confused, so I am trying not to overload them with options. the ssh install is basically a 2 step process, and has very few boundrary conditions, so it seems like the best bet to make the op happy. if you know an easier way, please let us know.

---

### Post by Mthbk1 on 2010-07-16
> **endotherm said:**
> that is true, but the op seems both frustrated and confused, so I am trying not to overload them with options. the ssh install is basically a 2 step process, and has very few boundrary conditions, so it seems like the best bet to make the op happy. if you know an easier way, please let us know.

Thanx for the reply, I am going to try it right now & report back with my progress :) & yes, u've interpreted my situation rightly 'frustrated'

---

