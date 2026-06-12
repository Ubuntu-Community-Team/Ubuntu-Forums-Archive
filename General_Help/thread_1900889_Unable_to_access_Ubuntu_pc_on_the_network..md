---
title: "Unable to access Ubuntu pc on the network."
date: 2011-12-27
forum: General Help
---

### Post by curtastrophe on 2011-12-27
OK, here's the story:

I have a machine running 11.x that I had  built some time ago. It's been running Ubuntu since 8.x and has been  upgraded with each release via the update manager. This particular  machine is used basically as a headless unit. It houses a few hard  drives that can usually be accessed by the other laptops in the house  for documents, pictures, etc. 

I've never really had a problem with it until a few months ago, I believe. 

The  problem I'm having is that the pc goes to sleep at some point even  though it's configured not to (power management, screen saver, etc are  all disabled). I can't access it through the public shares by ip OR  name. I have to physically log into the machine, connect to the internet  and browse to a laptop before a laptop can find it on the network. Even  then, I have to connect by IP address first before name resolution will  work.

I have two questions:
1. How do I keep this machine on the network so that it's always accessible? Preferably without installing Ubuntu server.
2. How can I turn off the DHCP client on the machine and set it to a static ip address?

Can  anyone help or have gone through something similar? I know I'm probably  leaving something out. Let me know and I'll answer questions as best as  I am able.

Thanks!

---

### Post by 73ckn797 on 2011-12-27
This assumes you have Samba installed and the drives are set for sharing?

---

### Post by curtastrophe on 2011-12-27
Yes. I remember in the earlier versions you had to manually install and configure sharing with Samba, which I had done. But I believe it became native somewhere around 10.x but I can't say for sure. But to the point, samba had worked in the past without an issue.

---

### Post by routed on 2011-12-27
For your second question you can set it up with static addressing through the GUI or you can modify the configuration file located at /etc/network/interfaces

---

### Post by Synoc on 2011-12-27
if I were you, I'd assign static IP addresses from your DHCP settings on your router, otherwise that IP address could end up being assigned to another computer and you will have IP conflicts.

Find the LAN settings, or perhaps DHCP settings, and assign the computer an address reservation.

This MIGHT be the problem you are having.

---

### Post by 73ckn797 on 2011-12-27
> **curtastrophe said:**
> Yes. I remember in the earlier versions you had to manually install and configure sharing with Samba, which I had done. But I believe it became native somewhere around 10.x but I can't say for sure. But to the point, samba had worked in the past without an issue.
I have had to install Samba from the repos to get connected with other computers in my house, both on 10.04 and 11.10.

---

### Post by sdowney717 on 2011-12-27
> I have had to install Samba from the repos to get connected with other computers in my house, both on 10.04 and 11.10.
really which ones?

---

### Post by curtastrophe on 2011-12-27
I've got the NIC set to a static IP now. Name resolution still doesn't work... seemingly ever. That's not a huge deal. But it seems the pc still 'sleeps' periodically which requires me to plug in a monitor and inputs to wake it up so it can be accessed. That is problematic for a family attempting to access homework, pics and the like when I'm not around. 

Anyone have any ideas?

Thanks!

---

### Post by 73ckn797 on 2011-12-28
> **sdowney717 said:**
> really which ones?
Your response puzzles me. Which ones? Both as I mentioned. 

After loading either version on any of the computers (4) and selecting the share feature for the /public folder I am told that I do not have the correct package installed, so I have to either let it do that or I installed Samba before starting the procedure.

---

### Post by Morbius1 on 2011-12-28
> **curtastrophe said:**
> I've got the NIC set to a static IP now. Name resolution still doesn't work... seemingly ever. 
I don't have an answer to the bigger question of how and why your server goes to sleep and can't wake up but if you have a static ip address you no longer need name resolution to work. 

Have the client access the share by ip address not by name.

---

