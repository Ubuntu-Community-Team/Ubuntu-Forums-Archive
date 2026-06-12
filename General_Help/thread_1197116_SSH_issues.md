---
title: "SSH issues"
date: 2009-06-25
forum: General Help
---

### Post by Tyke91 on 2009-06-25
I'm having some issues connecting to my computer with SSH. It was working fine 3 nights ago, but now whenever I try to ssh to my IP address, I am given
```
~$ ssh -v {the IP addy of my router}
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to {this is my ip addy} port 22.
debug1: Connection established.
debug1: identity file /home/mykola/.ssh/identity type -1
debug1: identity file /home/mykola/.ssh/id_rsa type -1
debug1: identity file /home/mykola/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent

```

where it promptly hangs.

I've told firestarter to turn iptables off and I think I've forwarded my ports correctly (screenshot attached). 
[ATTACH]118981[/ATTACH]

here is my output from ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1f:bc:07:e9:96  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:bcff:fe07:e996/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42064262 (42.0 MB)  TX bytes:2431449 (2.4 MB)
          Interrupt:252 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1f:bc:07:e9:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28214 (28.2 KB)  TX bytes:28214 (28.2 KB)

```


any ideas/suggestions? 

I've tried editing my /etc/ssh/ssh_config as stated here [http://www.nabble.com/ssh-connection-stop-at-%22debug1:-SSH2_MSG_KEXINIT-sent%22---problem-with-linux-2.6-and-vista-td13237600.html](http://www.nabble.com/ssh-connection-stop-at-%22debug1:-SSH2_MSG_KEXINIT-sent%22---problem-with-linux-2.6-and-vista-td13237600.html) 

but it hasn't done anything.


any help? :confused: This is especially strange because it was working only a few days ago.

---

