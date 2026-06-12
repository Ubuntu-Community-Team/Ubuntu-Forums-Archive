---
title: "KVM installation in ubuntu 10.04"
date: 2011-03-13
forum: General Help
---

### Post by HiMannu on 2011-03-13
Hi team,
 
   I was trying to install KVM/qemu on Ubuntu 10.04 x64 server using bridge network. While following the steps mentioned at   [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) 
 
   Everything went thru except the command  
[FONT=Verdana]egrep -c '(vmx|svm)' /proc/cpuinfo    which gave the output '0'.  [/FONT][FONT=Verdana]  I've got i7 with 8CPUs - Intel 950 , 8GB RAM, 500GB HDD[/FONT][FONT=Verdana]When I looked into the [/FONT][FONT=Verdana]BIOS of the server, I was not able to find "Virtualization Technology" Enable/Disable option[/FONT][FONT=Verdana]anywhere on it.  [/FONT][FONT=Verdana]I've got 8 CPUs on this server that can support the VT, but BIOS doesn't... Can this be a problem, I'm unable to run KVM on this system ?[/FONT][FONT=Verdana]Please let me know where is the problem and solution to it ?[/FONT][FONT=Verdana][/FONT]

---

