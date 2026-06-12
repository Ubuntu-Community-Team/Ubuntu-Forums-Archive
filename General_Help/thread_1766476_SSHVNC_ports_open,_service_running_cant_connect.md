---
title: "SSH/VNC ports open, service running cant connect?"
date: 2011-05-24
forum: General Help
---

### Post by ph3d on 2011-05-24
not sure whats going on here but i re installed ubuntu 11.04 two days ago, setup vnc and ssh as normal but now it just times out on both when trying to connect is there a firewall or something in place by default?

ports show as open when scanning my external isp address, ubuntu box is in the dmz so no need for ports being forwarded..

am i missing something?

edit: i also cannot connect via localhost, the above testing i could not connect from my work

2nd edit: i can also netcat to my external ip via ssh/vnc ports and read the banners fine?

---

### Post by CharlesA on 2011-05-24
Post the output of this please:

```
netstat -nl
```

```
sudo iptables -L
```

If the services are listening on those ports and you aren't firewalled, you should be able to connect fine.

Also note: it's not really a good idea to have VNC directly exposed to the internet, as it is unencrypted and is the cause of many boxes being cracked.

---

### Post by ph3d on 2011-05-24
[FONT=monospace]Ok i have disabled vnc for time being. Password was pretty secure though and theres nothing on this box so it will be going back up lol..

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:55940           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp6       0      0 :::57468                :::*                               
udp6       0      0 :::5353                 :::*                               
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     8383     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     10335    /tmp/ssh-MmToEozg1233/agent.1233
unix  2      [ ACC ]     STREAM     LISTENING     10363    /tmp/.ICE-unix/1233
unix  2      [ ACC ]     STREAM     LISTENING     11307    /tmp/orbit-phed/linc-4fb-0-69378198c8744
unix  2      [ ACC ]     STREAM     LISTENING     10388    /tmp/orbit-phed/linc-4d1-0-2bd6219fd2d02
unix  2      [ ACC ]     STREAM     LISTENING     11576    /tmp/keyring-rg5MKg/control
unix  2      [ ACC ]     STREAM     LISTENING     14903    /tmp/orbit-phed/linc-609-0-33d82e824d40
unix  2      [ ACC ]     STREAM     LISTENING     16141    /tmp/orbit-phed/linc-649-0-66ce41d3e310e
unix  2      [ ACC ]     STREAM     LISTENING     16348    /tmp/orbit-phed/linc-65d-0-3de6cfd55504
unix  2      [ ACC ]     STREAM     LISTENING     11610    /tmp/keyring-rg5MKg/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     11613    /tmp/keyring-rg5MKg/ssh
unix  2      [ ACC ]     STREAM     LISTENING     11282    @/tmp/dbus-Ad7vQMlt4p
unix  2      [ ACC ]     STREAM     LISTENING     11633    /tmp/orbit-phed/linc-508-0-2d20ae901e4fb
unix  2      [ ACC ]     STREAM     LISTENING     10664    /tmp/orbit-phed/linc-513-0-6bdd54feced4d
unix  2      [ ACC ]     STREAM     LISTENING     10628    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     10630    /home/phed/.pulse/c941f4c13a286d2e95264a350000000a-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     10644    /tmp/orbit-phed/linc-523-0-1a70fa5cc8a27
unix  2      [ ACC ]     STREAM     LISTENING     12184    /tmp/orbit-phed/linc-52d-0-6ecf726ddce
unix  2      [ ACC ]     STREAM     LISTENING     12251    /tmp/orbit-phed/linc-539-0-84b519793483
unix  2      [ ACC ]     STREAM     LISTENING     10850    /tmp/orbit-phed/linc-543-0-173c6802ba51c
unix  2      [ ACC ]     STREAM     LISTENING     10871    /tmp/orbit-phed/linc-541-0-1e5af0e0c19e3
unix  2      [ ACC ]     STREAM     LISTENING     12380    /tmp/orbit-phed/linc-53e-0-2b1e58f5d16a7
unix  2      [ ACC ]     STREAM     LISTENING     10920    /tmp/orbit-phed/linc-560-0-15993346be01
unix  2      [ ACC ]     STREAM     LISTENING     12530    /tmp/orbit-phed/linc-567-0-45bab19c27ada
unix  2      [ ACC ]     STREAM     LISTENING     10984    /tmp/orbit-phed/linc-56c-0-3670cba2549ea
unix  2      [ ACC ]     STREAM     LISTENING     12881    /tmp/orbit-phed/linc-573-0-3218c02ea9bf
unix  2      [ ACC ]     STREAM     LISTENING     12898    /tmp/orbit-phed/linc-583-0-2f1e9b20ee627
unix  2      [ ACC ]     STREAM     LISTENING     12906    /tmp/orbit-phed/linc-577-0-223ef899f0dc9
unix  2      [ ACC ]     STREAM     LISTENING     11133    /tmp/orbit-phed/linc-57c-0-56527b96f0f43
unix  2      [ ACC ]     STREAM     LISTENING     12915    /tmp/orbit-phed/linc-584-0-5780a1dbf3639
unix  2      [ ACC ]     STREAM     LISTENING     11139    /tmp/orbit-phed/linc-57f-0-517af6f2f367b
unix  2      [ ACC ]     STREAM     LISTENING     13132    /tmp/orbit-phed/linc-5ae-0-25b5f1af962c1
unix  2      [ ACC ]     STREAM     LISTENING     13431    /tmp/orbit-phed/linc-5b0-0-1e2835079bff2
unix  2      [ ACC ]     STREAM     LISTENING     13265    /tmp/orbit-phed/linc-5c6-0-3b94d986d422b
unix  2      [ ACC ]     STREAM     LISTENING     6713     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     6377     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     8002     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     8382     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8519     @/tmp/gdm-session-FxDZyTVI
unix  2      [ ACC ]     STREAM     LISTENING     10362    @/tmp/.ICE-unix/1233
unix  2      [ ACC ]     STREAM     LISTENING     9666     @/tmp/gdm-greeter-iXsceWxN
unix  2      [ ACC ]     STREAM     LISTENING     7660     /var/run/dbus/system_bus_socket

phed@evolution5:~$ sudo iptables -L
[sudo] password for phed: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
phed@evolution5:~$ 


phed@evolution5:~$ nmap phed.pwnz.org

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-05-24 19:12 BST
Nmap scan report for my.dns.org (82.*.*.*)
Host is up (0.046s latency).
rDNS record for 82.*.*.*: .*.*.*.cable.virginmedia.com
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 0.77 seconds
phed@evolution5:~$ 

phed@evolution5:~$ ssh my.dns.org

Connection closed by 82.*.*.*
```[/FONT]

---

### Post by ph3d on 2011-05-24
ok the only thing i think causing this is possibly me installing 10.10 as i had a disc handy then just doing a upgrade straight away, downloading 11.04 now and will reburn and install and repost how it goes

---

### Post by CharlesA on 2011-05-24
Well ssh is listening and nmap shows it open.

You said you weren't able to ssh via localhost, right?

Have you tried from a different machine?

Try connecting like this and post the output:

```
ssh -vvv user@host
```

---

### Post by ph3d on 2011-05-24
hi mate, thanks for the help, it would not work from a external or internal machine just seemed to hang and then timeout even though both ports where showing as open and as above i could netcat to the port and see the banner, i have now re-installed fresh and all seems to be working fine, i am able to vnc/ssh from a remote host and local now..

so putting it down to a bum install, 

cheers again!

how do i now mark this as solved?

---

### Post by CharlesA on 2011-05-24
Glad you got it working, even tho it needed a clean install.

Don't forgot to mark the thread as solved from thread tools. :)

---

