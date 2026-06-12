---
title: "General questions"
date: 2010-05-18
forum: General Help
---

### Post by P.T. on 2010-05-18
Hello,

As I went through my log files yesterday, some questions raised. Hopefully someone can help me.

1)
```
Unknown OutputIN= OUT=vmnet1 SRC=172.16.99.1 DST=172.16.99.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Unknown OutputIN= OUT=vmnet8 SRC=192.168.211.1 DST=192.168.211.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
```I figure these are because of VMware player, which I use for some windows programs.
Is there any way to disable this from constantly happening? As my logs are full of these. Could Virtualbox be a solution?

2)
```
avahi-daemon[621]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.x.x.
avahi-daemon[621]: IP_ADD_MEMBERSHIP failed: No buffer space available
```Someone told me avahi was for network discovery, but why does it give me "No buffer space available"?

3)
```
wpa_supplicant[1334]: WPA: Could not verify EAPOL-Key MIC - dropping packet

```This happens every now and then after I login. My wireless won't connect since the handshake went wrong in some way. Obviously my wireless won't go up at a such time. Usually I can find a couple of these together in my logs.
Why is this happening?

4)
```
sudo: pam_sm_authenticate: Called
sudo: pam_sm_authenticate: username = [name]
sudo: pam_sm_authenticate: /home/name is already mounted
```Yesterday I found quite some of these, today I can't find that many. What is pam_sm_authenticate, and why does it try to mount my home folder?

Also, I have some random logouts. Can they be related to this? In the logs it looked like 5 failed login attempts at TTY2 (I really don't know where those came from).

5)
```
Clocksource tsc unstable (delta = -185205212 ns)
```For what I've read this was a known problem. This could be solved by adding clocksource=hpet to my GRUB. I've also read that it is unwise to edit GRUB by hand. How can I add this rule to GRUB2?

6)
Also, when I looked at GRUB I found a rule "search --no-floppy" and "insmod ext2". What do both of those mean?


Quite some questions I guess. But it's never wrong to try and learn something right?

---

### Post by P.T. on 2010-05-22
Answers I've found so far

1)
Disabling the vmware service will stop the virtual network adapters. The downside is that vmware player is no longer usable and will give a couple of errors.
I'm not sure if virtualbox does a better job.

3)
This could be because of my Atheros wifi card. I've read somewhere that there is a modified kernel available, but I'm not sure what my wifi card's version is.
Besides, I'm a little scared by the idea of another kernel that is not an official one.

4)
Still in the dark about this. Could it have something to do with SSL? Where can I check this?

5)
According to [this post]("http://ubuntuforums.org/showthread.php?t=1195275") I should put the option in /etc/default/grub at the line with 'GRUB_CMDLINE_LINUX ="" '. This way it would become
```
GRUB_CMDLINE_LINUX="clocksource=hpet"
```can anyone tell me if this is correct?

6)
insmod ext2:
Apparently ext2 is a module that enables the use of ext2, 3 and 4. It can't be changed to ext4 because there is no such module.
[http://ubuntuforums.org/showthread.php?t=1460756](http://ubuntuforums.org/showthread.php?t=1460756)

--no-floppy:
This tells GRUB2 not to look for a floppy drive.
[http://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation](http://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation)

---

### Post by schiotz on 2010-05-24
> **P.T. said:**
> Answers I've found so far

1)
Disabling the vmware service will stop the virtual network adapters. The downside is that vmware player is no longer usable and will give a couple of errors.
I'm not sure if virtualbox does a better job.


I am running vmware workstation occationally, but does not want to start the service when I do not use it.  I use this script installed as /usr/local/bin/vmware :

```
#! /bin/bash

export VMWARE_USE_SHIPPED_GTK=yes
grep vmnet /proc/modules > /dev/null || (sudo /etc/init.d/vmware start; sleep 3)
/usr/bin/vmware
sudo /etc/init.d/vmware stop

```and I have set up sudo to allow me to start and stop the service without giving a password.  Perhaps you can adapt this to your needs.

/Jakob

---

