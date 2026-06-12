---
title: "sshfs - error messages - not working after upgrade!"
date: 2011-09-01
forum: General Help
---

### Post by mbuell on 2011-09-01
I had ubuntu 9.1 on a "server" machine for my home lan. My linux box sshfs'd quite faithfully into that system. My windows boxes could all see and get to the samba share. So, all was good.

Until - the dreaded upgrade. I didn't actually allow the upgrade - I've been through this a couple of times. I backed up /usr, and /home, and did a fresh install to 10.04 LTS. 

Now I can not sshfs to mount a drive, as I am accustomed to do. And, in a separate issue, my windows box does not see the machine on the network. I think that really IS a separate issue, but maybe it will get me a little sympathy! :D

Back to business - sshfs. I installed the ssh mega package, and fuse-utils is installed. Ssh seems to work - but I am not 100% sure of that, since I don't know what to look for to guarantee it is working. 

When I just do sshfs me@198.54.0.5:/share /myclient/myshare - which is what I've been doing for over a year - it won't connect, and I get a message> read: Connection reset by peer 

So, I googled for a few hours, and came up with:
*Uninstall and reinstall ssh. I uninstalled ssh, then reinstalled. I rebooted. The client settings have not changed - and used to work. 
*Is fuse installed? The server has fuse installed, and running. No good. 
*Port blocked? I have firestarter installed to manage iptables. Port 22 is open. And, it doesn't matter if firestarter turns the firewall off - same problem. 
*Config files? On the client I blew away ~/.ssh/known_hosts to re-recognize the new installation. It wasn't that. I checked my ssh_config, and my sshd_config (/etc/ssh). They are identical to what they used to be. Not that.
I also found this to give me a little more to go on:
> sshfs -o sshfs_debug hiero@172.16.0.4 /media/uthor
which tells me > SSHFS version 2.2
missing host
see `sshfs -h' for usage

which gives me pretty much the same links. 


There isn't anything else suggested in the other forum answers google found for me. 

Can anybody help?

---

### Post by mbuell on 2011-09-02
Solved. At least, the sshfs is solved!

This problem seems to have been a result of several factors - but a combination of the firewall, the ssh de-installation, and the ssh host key. 

The ssh installation got messed up when I uninstalled. The installer gave me some confused-sounding messages - but I think that some part of lsh got uninstalled and not reinstalled as part of the process yesterday. I'm going to guess that my timing was bad, and I when turned off the firewall before, one of the other factors was still causing an issue. 

Today, I checked the iptables rules using iptables -L. There were a bundle of rules, way complicated. So, I shut it down using firestarter. Then, iptables -L shows all ALLOW. I reinstalled lsh (generation 2 ssh utilities?), and logged out and back in. Iptables was still clear. Then I cleared out the ~/.ssh/known_hosts and all the old known_hosts I had renamed. THEN I could successfully ssh in to the machine - and the server said "Welcome". And, now I can sshfs to the file system.

---

