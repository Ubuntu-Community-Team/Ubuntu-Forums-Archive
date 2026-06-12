---
title: "Recreating Microwulf"
date: 2010-02-13
forum: General Help
---

### Post by elysium_nl on 2010-02-13
Hello all,
 

 I'm a newby to Linux and I'm trying to create a Microwulf with four nodes ([http://www.calvin.edu/~adams/research/microwulf/](http://www.calvin.edu/~adams/research/microwulf/)).
 For this I'm using four Asus M2N-VM DVI motherboards, with AMD Athlon 64 X2 5200+ processor and 4 GB RAM. The motherboard has a Nvidia 1G nic, so I installed (like the original Microwulf) an Intel 1G PCI-e nic. On the first node as the third nic I use an Intel 1G PCI nic, a 250GB SATA hard drive and a SATA DVD drive.
 As the OS I'm using on the first node Ubuntu 64 9.10 desktop and for the other nodes Ubuntu 64 9.10 server. For the internal network I assigned the first node first nic 192.168.182.1 and the second nic 192.168.183.1 and the third nic is on dhcp for my own network at home. For the other nodes I'm using 192.168.182.2-4 and 192.168.183.2-4.
 To boot a server node I'm using PXELinux. And that's were the trouble starts. The node looks for the connection and boots of the desktops /tftpboot/ folder. After a while the server shows the recovery menu. And that's it, it just stops there, even when I select “resume”.
 I'm lost why the server won't boot up correctly. So please can somebody give me a hint where to look.


Renee

 

 Below is the last part of syslog:
 

 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   27.771264] eth1: no IPv6 routers present [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   27.771269] nfs: server 192.168.182.1 not responding, still trying [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   27.771278] nfs: server 192.168.182.1 not responding, still trying [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   27.771287] nfs: server 192.168.182.1 not responding, still trying [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   28.820016] nfs: server 192.168.182.1 not responding, still trying [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   46.890015] nfs: server 192.168.182.1 not responding, still trying [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   88.856506] nfs: server 192.168.182.1 OK [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   88.856523] nfs: server 192.168.182.1 OK [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   88.856549] nfs: server 192.168.182.1 OK [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   88.856575] nfs: server 192.168.182.1 OK [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   88.856600] nfs: server 192.168.182.1 OK [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:51 microwulf-node1 kernel: [   89.120078] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input5 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:52 microwulf-node1 kernel: [   99.831045] type=1505 audit(1266082012.574:7): operation="profile_replace" pid=805 name=/sbin/dhclient3 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:52 microwulf-node1 kernel: [   99.831284] type=1505 audit(1266082012.584:8): operation="profile_replace" pid=805 name=/usr/lib/NetworkManager/nm-dhcp-client.action [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:52 microwulf-node1 kernel: [   99.831412] type=1505 audit(1266082012.584:9): operation="profile_replace" pid=805 name=/usr/lib/connman/scripts/dhclient-script [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:52 microwulf-node1 kernel: [   99.910894] type=1505 audit(1266082012.654:10): operation="profile_replace" pid=807 name=/usr/bin/freshclam [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:52 microwulf-node1 kernel: [   99.990911] type=1505 audit(1266082012.734:11): operation="profile_replace" pid=808 name=/usr/sbin/tcpdump [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 rpc.statd[716]: Caught signal 15, un-registering and exiting. [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 init: upstart-udev-bridge main process ended, respawning [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 init: udev main process ended, respawning [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 init: portmap main process (703) killed by TERM signal [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 init: portmap main process ended, respawning [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 init: statd main process ended, respawning [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 init: rsyslog-kmsg main process (759) killed by TERM signal [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 init: rsyslog-kmsg main process ended, respawning [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:57 microwulf-node1 kernel: Kernel logging (proc) stopped. [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:58 microwulf-node1 kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started. [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:58 microwulf-node1 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1035" x-info="http://www.rsyslog.com"] (re)start [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:58 microwulf-node1 rsyslogd: rsyslogd's groupid changed to 103 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:58 microwulf-node1 rsyslogd: rsyslogd's userid changed to 101 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=1]Feb 13 11:26:58 microwulf-node1 kernel: [  105.828214] udev: starting version 147 [/SIZE][/FONT]

---

### Post by elysium_nl on 2010-02-15
Ok, problem solved.
According the original handout of the microwulf, you need to change BOOT=local to BOOT=nfs in /etc/initramfs-tools/initramfs.conf. But you also need to change MODULES to MODULES=netboot. After that the node's worked nicely.
Renee

---

