---
title: "resolv.conf reset after reboot"
date: 2011-09-29
forum: General Help
---

### Post by satimis on 2011-09-29
Hi all,

Ubuntu 1110 64 bit

After reboot all entries on /etc/resolv.conf are gone.  Please advise how to fix this problem instead of making it 444?

TIA

B.R.
satimis

---

### Post by dcstar on 2011-09-30
> **satimis said:**
> Hi all,

Ubuntu 1110 64 bit

After reboot all entries on /etc/resolv.conf are gone.  Please advise how to fix this problem instead of making it 444?


Don't use DHCP.

---

### Post by satimis on 2011-09-30
> **dcstar said:**
> Don't use DHCP.

Hi,

No, I'm running static IP

$ cat /etc/network/interfaces```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
address 192.xxx.xxx.xxx
network 192.xxx.xxx.xxx
netmask 255.255.255.0
broadcast 192.xxx.xxx.xxx
gateway 192.xxx.xxx.xxx
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

The OS is running on a VM of VirtualBox

remark:
other VMs running Ubuntu1010/1004 don't have this problem.

B.R.
satimis

---

### Post by dcstar on 2011-09-30
> **satimis said:**
> Hi all,

Ubuntu 1110 64 bit
.........

11.10 is beta software. The whole point of development software is to report problems in the development forum so they can be fixed before release.

You are not supposed to post any issues with development software in these forums.

---

### Post by xscott on 2011-10-19
im sry im new to this page
anyway i need some help

i have a linux ubuntu 10.10 OS
my problem is one of the files that is mounted to my profile. i cant access the file if i need to reboot
the resolv.conf resets or something along those lines

i have no past experiance with coding and want to figure out how to do it myself so i dont have to have my dad come down every time to reset it 

i know wat the problem is well kinda

the domain name when i was setting up my computer was mispelt 
instead of unix4u.us i put unxi4u.us
i dont know how to get to that so i can change it 

im sry i dont know if any of that makes any sense its easy to explain in my head but i dont really know much about it to give u any details 

thx for ur time and patients helping me

---

### Post by xscott on 2011-10-19
> **xscott said:**
> im sry im new to this page
anyway i need some help

i have a linux ubuntu 10.10 OS
my problem is one of the files that is mounted to my profile. i cant access the file if i need to reboot
the resolv.conf resets or something along those lines

i have no past experiance with coding and want to figure out how to do it myself so i dont have to have my dad come down every time to reset it 

i know wat the problem is well kinda

the domain name when i was setting up my computer was mispelt 
instead of unix4u.us i put unxi4u.us
i dont know how to get to that so i can change it 

im sry i dont know if any of that makes any sense its easy to explain in my head but i dont really know much about it to give u any details 

thx for ur time and patients helping me


plz advise 
i didnt mean to post this to a reply im not trying to reply to the question but to ask my own as i said idk how to post a new thread 
sry for any inconvenience

---

