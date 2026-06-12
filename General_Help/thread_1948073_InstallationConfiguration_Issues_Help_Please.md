---
title: "Installation/Configuration Issues Help Please"
date: 2012-03-27
forum: General Help
---

### Post by bxdobs on 2012-03-27
Attempting to install a stable version of UBUNTU in VM PLAYER (Ver 4.0.2 build-591240) under XP Pro SP3 on an i7 Lenovo 
laptop. 

I need the ability to telnet from XP into UBUNTU to run a proprietary UNIX character base application. Would also be useful to have access to the UNIX file system from XP preferably using Samba. 

Searching through online posts get me close but fall short because there appear to be missing details ... most posts on this subject are several years old so kind of hard to do a follow up.

Help would be appreciated ... 

I am open to starting with a fresh iso of UBUNTU or even possibly using VirtualBox instead of VMWARE Player provided I can end up with the ability to telnet into the VM and be able set up a file system share (using samba) 

SO FAR I have:

1st attempt: started with an older version (sorry didn't look at the version prior to starting) of UNBUNTU which has been running in VM for several years ... I let it update several times ... ended up at version 11.04 ... this version crashed on reboot with a grub prompt ... applied suggested fixes but now crashed on reboot with a grub rescue prompt ... finding no solutions, ended up having to dump the VM image

2nd attempt: ubuntu-11.10-desktop-i386.iso installed and updated but this install apparently had no access to a unix shell ... appeared to be a GUI only install??? ... totally unusable ... dumped VM image

3rd attempt: ubuntu-10.04.1-desktop-i386.iso installed and updated ... this has the following issues:

1) cannot get the xinetd restart to run ... wants some extra switches?
Usage: xinetd [-d] [-f config_file] [-filelog filename] [-syslog facility] [-reuse] [-limit proc_limit] [-pidfile filename] [-logprocs limit] [-shutdownprocs limit] [-cc interval]

2) telnet and ssh from XP both fail with no connection ... using ifconfig obtained the ip address: 
telnet <ip address>
no connection
telnet <ip address> 22
no connection 

3) Samba4 installs but wont accept the smb.conf file (fails due to unknown parameter "PASSWD PROGRAM"

4) installed teamviewer 7 and it can connect from XP to VM but not the other way around (opens in infinite loops) ... while this allows file transfers I would prefer shared access.

5) VM Player also appears to be causing the laptop to freeze for several seconds at a time when either switching back and forth between XP and the VM and or Closing the VM.

---

### Post by bxdobs on 2012-03-27
Update ... just figured out a solution to issue 1) telnet and xinetd: 

a) this version of UBUNTU appears to require using: service xinetd reload

b) VMWARE generates 2 NETWORK CONNECTIONS in XP :
   VMnet1 and VMnet8 ... I found while these were enabled one of my client sites wasn't accesible as the IP addresses conficted ... as such I had disabled both of these connections ... with them enabled Telnet now works ... now I will have to find a new solution for the site with the IP conflict.

---

