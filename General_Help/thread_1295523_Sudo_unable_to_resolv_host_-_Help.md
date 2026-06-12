---
title: "Sudo: unable to resolv host - Help"
date: 2009-10-19
forum: General Help
---

### Post by the111dan on 2009-10-19
Hi there
I get "unable to resolv host" when I use "sudo" comand in terminal and none of the Administration app's start when I click them in the gui, only when I start them from the terminal with "sudo".

I have found this problem discussed in previous posts but none of the solutions work for me.
my /etc/hosts file says:

"127.0.0.1       localhost
127.0.1.1       dan-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"

dan-desktop is actualy the name of the computer, nothing changed there as I read in the other posts

This problem appeared after I installed wicd, completely removed network manager and deleted NetworkManager folder from /etc and then reinstalled Network Manager. All the operations were made with synaptic except for the removal of /etc/NetworkManager which was done by me.

---

### Post by mac9416 on 2009-10-19
The /etc/hosts looks good. Could you post your /etc/hostname? Maybe it doesn't match.

---

### Post by the111dan on 2009-10-19
/etc/hostname

"dan-desktop"

---

### Post by the111dan on 2009-10-22
problem solved by itself after a series of updates
still don't know the real reason, but now it's working perfectly

---

