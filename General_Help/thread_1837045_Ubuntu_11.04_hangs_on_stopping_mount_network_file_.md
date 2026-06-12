---
title: "Ubuntu 11.04 hangs on stopping mount network file system"
date: 2011-09-01
forum: General Help
---

### Post by pollus on 2011-09-01
Hi guys.

I installed Ubuntu a few days ago and everything was working fine. yesterday I added 2 graphic cards into my system and uisntalled the driver for them (ATI) it looked like it took it. After I bounced the box it goes as far as "stopping mount network file system" and then it stops. 

If I press control alt delete it says ok stopping this stopping that and restarting....

Any ideas what might have gone wrong?

My disk is a 250 GB devided into 3 partitions mounted at /; /home; /opt
I have a swap partition of 8 GB as well.

Any help would be appreciated.

Thank you.

pollus

---

### Post by kimr1508 on 2011-09-09
If you find a solution please let me know.

I have the same issue on Kubuntu 11.10 beta1.


Kim

---

### Post by choel on 2011-09-11
> **pollus said:**
> Hi guys.

I installed Ubuntu a few days ago and everything was working fine. yesterday I added 2 graphic cards into my system and uisntalled the driver for them (ATI) it looked like it took it. After I bounced the box it goes as far as "stopping mount network file system" and then it stops. 

If I press control alt delete it says ok stopping this stopping that and restarting....

Any ideas what might have gone wrong?

My disk is a 250 GB devided into 3 partitions mounted at /; /home; /opt
I have a swap partition of 8 GB as well.

Any help would be appreciated.

Thank you.

pollus


Are you sure it stops? Have a similar problem but after 4-5 mins it continue to boot. Can't figure out what it is doh, but i think it could be samba. Gonna look in to it today and get back.

---

### Post by as2000 on 2011-09-11
Have you checked the logs? Often you can pinpoint what was going on at that moment.

---

### Post by choel on 2011-09-11
Ok, think I figured it out now, 
For me it just delays 2-3 min before it continues with the boot. The delay is caused by "Failsafe boot delay" which starts right after "Stopping mount network drivers". 

Have a look in /etc/init/failsafe.conf 
and change "sleep 120" to "sleep 1" as described in this bug report. 
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/845914](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/845914)

Don't know why this started after last update. :/


[EDIT]
Just found another fix for the problem. As described in this bug report.
[https://bugs.launchpad.net/ubuntu/+s...rt/+bug/839595](https://bugs.launchpad.net/ubuntu/+s...rt/+bug/839595)

Changing in "/etc/network/interfaces" also works. 

As described in the bug report by Scott Moser (smoser)
> 
I suspect that you have a interface listed there as 'auto' that is not
plugged in. If that is the case, the correct solution for you is to
remove that line or comment it out. To be clear, I suspect you have
something like:
auto eth0
iface eth0 inet dhcp

but your eth0 is not plugged in.


---

### Post by IanVaughan on 2011-10-29
> **choel said:**
> 
Have a look in /etc/init/failsafe.conf 
and change "sleep 120" to "sleep 1" as described in this bug report. 

A quick grep of this file only showed sleeps of 20, 40 and 59

> **choel said:**
> 
Changing in "/etc/network/interfaces" also works. 

After looking in my file, I was shocked to see
```
auto lo
iface lo inet loopback
```
Where is my eth0 gone?

Ok, so I was trying to remove unity, by doing to following 
Install gnome-session-fallback gdm
Purge lightdm

But still!?

---

### Post by IanVaughan on 2011-10-29
After making that change, it hung on [Stopping System V runlevel compatibility]("http://ubuntuforums.org/newreply.php?do=newreply&p=11351284")
So I've added more info there.

---

