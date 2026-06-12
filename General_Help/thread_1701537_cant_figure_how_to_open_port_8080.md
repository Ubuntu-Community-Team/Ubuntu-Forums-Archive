---
title: "cant figure how to open port 8080"
date: 2011-03-06
forum: General Help
---

### Post by sdowney717 on 2011-03-06
I allow in and out for 80 and 8080
I configure router for these ports
I assume the ip it shows to open is that of my PC attached to the router?
I check but says 
Error: I could not see your service on xx ip address on port (8080)

scott@scott-desktop:~$ sudo ufw status
[sudo] password for scott: 
WARN: / is world writable!
WARN: / is group writable!
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
8080/tcp                   ALLOW       Anywhere

8080/tcp                   ALLOW OUT   Anywhere
80/tcp                     ALLOW OUT   Anywhere

scott@scott-desktop:~$

---

### Post by lithopsian on 2011-03-06
Is anything listening on port 8080?

---

### Post by drdos2006 on 2011-03-06
IMPORTANT!!
Hide your public IP address from CanYouSeeMe.org before posting.

Does your ISP block any ports ?

From the machine 192.168.0.101 run the following and post back here.
To list listening devices and ports
sudo netstat -lnp

To list firewall settings
sudo iptables -L

List running processes and the ports open for those processes.
sudo rpcinfo -p

To check what outbound connections you have running.
sudo lsof -i -P -n

To check for open ports on the network
sudo nmap -sV 192.168.0.101

regards

---

### Post by sdowney717 on 2011-03-06
192.168.1.101 is my lan ip


```
scott@scott-desktop:~$ sudo netstat -lnp
[sudo] password for scott: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      12402/apache2   
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      2644/perl       
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1698/dnsmasq    
tcp        0      0 127.0.0.1:42678         0.0.0.0:*               LISTEN      12526/GoogleTalkPlu
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1237/cupsd      
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      2433/master     
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      12011/dropbox   
tcp        0      0 127.0.0.1:5984          0.0.0.0:*               LISTEN      1748/beam.smp   
tcp        0      0 127.0.0.1:2947          0.0.0.0:*               LISTEN      2459/gpsd       
tcp        0      0 192.168.1.101:3306      0.0.0.0:*               LISTEN      1477/mysqld     
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      11988/vino-server
tcp6       0      0 ::1:631                 :::*                    LISTEN      1237/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      1039/smbd       
tcp6       0      0 ::1:2947                :::*                    LISTEN      2459/gpsd       
tcp6       0      0 :::139                  :::*                    LISTEN      1039/smbd       
tcp6       0      0 :::5900                 :::*                    LISTEN      11988/vino-server
udp        0      0 0.0.0.0:47511           0.0.0.0:*                           1219/avahi-daemon: 
udp        0      0 192.168.1.101:51662     0.0.0.0:*                           2269/hamachid   
udp        0      0 192.168.122.1:53        0.0.0.0:*                           1698/dnsmasq    
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1698/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1332/dhclient   
udp        0      0 0.0.0.0:17500           0.0.0.0:*                           12011/dropbox   
udp        0      0 5.72.24.124:123         0.0.0.0:*                           1693/ntpd       
udp        0      0 192.168.122.1:123       0.0.0.0:*                           1693/ntpd       
udp        0      0 192.168.1.101:123       0.0.0.0:*                           1693/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1693/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1693/ntpd       
udp        0      0 5.255.255.255:137       0.0.0.0:*                           1647/nmbd       
udp        0      0 5.72.24.124:137         0.0.0.0:*                           1647/nmbd       
udp        0      0 192.168.1.255:137       0.0.0.0:*                           1647/nmbd       
udp        0      0 192.168.1.101:137       0.0.0.0:*                           1647/nmbd       
udp        0      0 192.168.122.255:137     0.0.0.0:*                           1647/nmbd       
udp        0      0 192.168.122.1:137       0.0.0.0:*                           1647/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1647/nmbd       
udp        0      0 5.255.255.255:138       0.0.0.0:*                           1647/nmbd       
udp        0      0 5.72.24.124:138         0.0.0.0:*                           1647/nmbd       
udp        0      0 192.168.1.255:138       0.0.0.0:*                           1647/nmbd       
udp        0      0 192.168.1.101:138       0.0.0.0:*                           1647/nmbd       
udp        0      0 192.168.122.255:138     0.0.0.0:*                           1647/nmbd       
udp        0      0 192.168.122.1:138       0.0.0.0:*                           1647/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1647/nmbd       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1219/avahi-daemon: 
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           2644/perl       
udp        0      0 0.0.0.0:1900            0.0.0.0:*                           2269/hamachid   
udp6       0      0 ::1:123                 :::*                                1693/ntpd       
udp6       0      0 fe80::609a:9bff:fe2:123 :::*                                1693/ntpd       
udp6       0      0 fe80::222:15ff:fe54:123 :::*                                1693/ntpd       
udp6       0      0 :::123                  :::*                                1693/ntpd       
udp6       0      0 :::49318                :::*                                1219/avahi-daemon: 
udp6       0      0 :::5353                 :::*                                1219/avahi-daemon: 
raw        0      0 0.0.0.0:1               0.0.0.0:*               7           2269/hamachid   
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     4437104  12290/chrome        /tmp/orbit-scott/linc-3002-0-1949a18b99ab6
unix  2      [ ACC ]     STREAM     LISTENING     4443471  12562/gnome-termina /tmp/orbit-scott/linc-3112-0-1420e2b52a8fb
unix  2      [ ACC ]     STREAM     LISTENING     4435666  12011/dropbox       /home/scott/.dropbox/command_socket
unix  2      [ ACC ]     STREAM     LISTENING     9216     1790/uml_switch     /var/run/uml-utilities/uml_switch.ctl
unix  2      [ ACC ]     STREAM     LISTENING     4443765  12598/update-notifi /tmp/orbit-scott/linc-3136-0-55e0deb0b1474
unix  2      [ ACC ]     STREAM     LISTENING     4435718  12011/dropbox       /home/scott/.dropbox/iface_socket
unix  2      [ ACC ]     STREAM     LISTENING     7939     1219/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     3979271  1237/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     12402    2433/master         private/tlsmgr
unix  2      [ ACC ]     STREAM     LISTENING     4431772  11864/gnome-keyring /tmp/keyring-14mmfe/control
unix  2      [ ACC ]     STREAM     LISTENING     12049    2287/vmware-usbarbi /var/run/vmware/usbarbitrator-socket
unix  2      [ ACC ]     STREAM     LISTENING     9234     1477/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     3937624  15996/kio_http_cach /tmp/ksocket-scott/kio_http_cache_cleaner
unix  2      [ ACC ]     STREAM     LISTENING     6044     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     12406    2433/master         private/rewrite
unix  2      [ ACC ]     STREAM     LISTENING     12410    2433/master         private/bounce
unix  2      [ ACC ]     STREAM     LISTENING     7742     1190/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     12414    2433/master         private/defer
unix  2      [ ACC ]     STREAM     LISTENING     4430363  11793/X             @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     1039100  2317/hald           @/var/run/hald/dbus-vhA0TDXfaH
unix  2      [ ACC ]     STREAM     LISTENING     14309    2673/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     14312    2673/pulseaudio     /home/scott/.pulse/c5cf650c106dab20f6fd38f74ab47905-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     4430364  11793/X             /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     12418    2433/master         private/trace
unix  2      [ ACC ]     STREAM     LISTENING     12422    2433/master         private/verify
unix  2      [ ACC ]     STREAM     LISTENING     12426    2433/master         public/flush
unix  2      [ ACC ]     STREAM     LISTENING     12430    2433/master         private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     4432068  11883/gnome-session /tmp/.ICE-unix/11883
unix  2      [ ACC ]     STREAM     LISTENING     12434    2433/master         private/proxywrite
unix  2      [ ACC ]     STREAM     LISTENING     12438    2433/master         private/smtp
unix  2      [ ACC ]     STREAM     LISTENING     12442    2433/master         private/relay
unix  2      [ ACC ]     STREAM     LISTENING     12446    2433/master         public/showq
unix  2      [ ACC ]     STREAM     LISTENING     12450    2433/master         private/error
unix  2      [ ACC ]     STREAM     LISTENING     12454    2433/master         private/retry
unix  2      [ ACC ]     STREAM     LISTENING     12458    2433/master         private/discard
unix  2      [ ACC ]     STREAM     LISTENING     12462    2433/master         private/local
unix  2      [ ACC ]     STREAM     LISTENING     4432040  11932/dbus-daemon   @/tmp/dbus-WJ9OaUVKz8
unix  2      [ ACC ]     STREAM     LISTENING     12466    2433/master         private/virtual
unix  2      [ ACC ]     STREAM     LISTENING     1039095  2317/hald           @/var/run/hald/dbus-lKw7I3Gc8O
unix  2      [ ACC ]     STREAM     LISTENING     12470    2433/master         private/lmtp
unix  2      [ ACC ]     STREAM     LISTENING     12474    2433/master         private/anvil
unix  2      [ ACC ]     STREAM     LISTENING     12478    2433/master         private/scache
unix  2      [ ACC ]     STREAM     LISTENING     4432027  11928/ssh-agent     /tmp/ssh-KQMOL11883/agent.11883
unix  2      [ ACC ]     STREAM     LISTENING     12482    2433/master         private/maildrop
unix  2      [ ACC ]     STREAM     LISTENING     12486    2433/master         private/uucp
unix  2      [ ACC ]     STREAM     LISTENING     12490    2433/master         private/ifmail
unix  2      [ ACC ]     STREAM     LISTENING     4432108  11937/gconfd-2      /tmp/orbit-scott/linc-2ea1-0-7f948976856af
unix  2      [ ACC ]     STREAM     LISTENING     12494    2433/master         private/bsmtp
unix  2      [ ACC ]     STREAM     LISTENING     12498    2433/master         private/scalemail-backend
unix  2      [ ACC ]     STREAM     LISTENING     4430569  11791/gdm-simple-sl @/tmp/gdm-session-EeEVnmEV
unix  2      [ ACC ]     STREAM     LISTENING     4432454  11883/gnome-session /tmp/orbit-scott/linc-2e6b-0-165d0220886b6
unix  2      [ ACC ]     STREAM     LISTENING     12502    2433/master         private/mailman
unix  2      [ ACC ]     STREAM     LISTENING     4430427  11791/gdm-simple-sl @/tmp/gdm-greeter-nCxQanxa
unix  2      [ ACC ]     STREAM     LISTENING     4432067  11883/gnome-session @/tmp/.ICE-unix/11883
unix  2      [ ACC ]     STREAM     LISTENING     8394     1402/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     4432523  11864/gnome-keyring /tmp/keyring-14mmfe/ssh
unix  2      [ ACC ]     STREAM     LISTENING     4432650  11864/gnome-keyring /tmp/keyring-14mmfe/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     4432690  11946/gnome-setting /tmp/orbit-scott/linc-2eaa-0-152d98b9c5c2c
unix  2      [ ACC ]     STREAM     LISTENING     4432703  11944/gnome-power-m /tmp/orbit-scott/linc-2ea8-0-2c9cd8e4c86c1
unix  2      [ ACC ]     STREAM     LISTENING     12395    2433/master         public/cleanup
unix  2      [ ACC ]     STREAM     LISTENING     11994    2269/hamachid       /var/run/logmein-hamachi/ipc.sock
unix  2      [ ACC ]     STREAM     LISTENING     4432964  11988/vino-server   /tmp/orbit-scott/linc-2ed4-0-54b720e43ada1
unix  2      [ ACC ]     STREAM     LISTENING     4433368  11989/nm-applet     /tmp/orbit-scott/linc-2ed5-0-57a87223e084d
unix  2      [ ACC ]     STREAM     LISTENING     4433477  11997/gnome-panel   /tmp/orbit-scott/linc-2edd-0-52b11f99ec347
unix  2      [ ACC ]     STREAM     LISTENING     4433622  12007/evolution-ala /tmp/orbit-scott/linc-2ee7-0-3a344e47a3408
unix  2      [ ACC ]     STREAM     LISTENING     14435    2722/gconf-helper   /tmp/orbit-scott/linc-aa2-0-61aa0942491b3
unix  2      [ ACC ]     STREAM     LISTENING     4433678  12005/nautilus      /tmp/orbit-scott/linc-2ee5-0-1cfd0268b7f4e
unix  2      [ ACC ]     STREAM     LISTENING     4434792  12134/gtk-window-de /tmp/orbit-scott/linc-2f66-0-7ef4b876d24a4
unix  2      [ ACC ]     STREAM     LISTENING     4434204  11990/python        /tmp/orbit-scott/linc-2ed6-0-629230c46605
unix  2      [ ACC ]     STREAM     LISTENING     4434215  12002/python        /tmp/orbit-scott/linc-2ee2-0-68b68e564859a
unix  2      [ ACC ]     STREAM     LISTENING     4434238  12084/e-calendar-fa /tmp/orbit-scott/linc-2f34-0-4bce6a2d65d0d
unix  2      [ ACC ]     STREAM     LISTENING     4434382  12113/gnome-screens /tmp/orbit-scott/linc-2f3f-0-1da2fcba64348
unix  2      [ ACC ]     STREAM     LISTENING     4434391  12103/metacity      /tmp/orbit-scott/linc-2f47-0-1e0c8f7667cf2
unix  2      [ ACC ]     STREAM     LISTENING     12521    2459/gpsd           /var/run/gpsd.sock
unix  2      [ ACC ]     STREAM     LISTENING     4434470  12108/bonobo-activa /tmp/orbit-scott/linc-2f4c-0-38f9f87a73aba
unix  2      [ ACC ]     STREAM     LISTENING     4434567  12123/trashapplet   /tmp/orbit-scott/linc-2f5b-0-239969ab78964
unix  2      [ ACC ]     STREAM     LISTENING     4434589  12122/wnck-applet   /tmp/orbit-scott/linc-2f5a-0-ea7f24a7fe39
unix  2      [ ACC ]     STREAM     LISTENING     4434619  12112/e-addressbook /tmp/orbit-scott/linc-2f50-0-4796af3900e6
unix  2      [ ACC ]     STREAM     LISTENING     4435457  12194/fish-applet-2 /tmp/orbit-scott/linc-2fa2-0-7f19bc174753a
unix  2      [ ACC ]     STREAM     LISTENING     4435461  12188/gweather-appl /tmp/orbit-scott/linc-2f9c-0-5a2726d4476ca
unix  2      [ ACC ]     STREAM     LISTENING     4435470  12190/indicator-app /tmp/orbit-scott/linc-2f9e-0-685601bc4826a
unix  2      [ ACC ]     STREAM     LISTENING     4437089  12290/chrome        /tmp/.com.google.chrome.l8GZTO/SingletonSocket
unix  2      [ ACC ]     STREAM     LISTENING     4435487  12195/geyes_applet2 /tmp/orbit-scott/linc-2fa3-0-12561fb14a09c
unix  2      [ ACC ]     STREAM     LISTENING     4435499  12196/multiload-app /tmp/orbit-scott/linc-2fa4-0-669a90454b59d
unix  2      [ ACC ]     STREAM     LISTENING     4435515  12192/notification- /tmp/orbit-scott/linc-2fa0-0-f1efb5e50d94
unix  2      [ ACC ]     STREAM     LISTENING     4435525  12191/clock-applet  /tmp/orbit-scott/linc-2f9f-0-487969e151a12
unix  2      [ ACC ]     STREAM     LISTENING     4435595  12189/indicator-app /tmp/orbit-scott/linc-2f9d-0-5599ac375c516
unix  2      [ ACC ]     STREAM     LISTENING     4435895  12257/indicator-me- /tmp/orbit-scott/linc-2fe1-0-42981d6d84750
unix  2      [ ACC ]     STREAM     LISTENING     4435908  12254/notify-osd    /tmp/orbit-scott/linc-2fde-0-25b77d6986a62
unix  2      [ ACC ]     STREAM     LISTENING     4435942  12262/indicator-ses /tmp/orbit-scott/linc-2fe6-0-94f2a39ae24

```

```

scott@scott-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
scott@scott-desktop:~$ 

```

```
scott@scott-desktop:~$ sudo rpcinfo -p
rpcinfo: can't contact portmapper: RPC: Remote system error - Connection refused
scott@scott-desktop:~$ 

```

```
scott@scott-desktop:~$ sudo lsof -i -P -n
COMMAND     PID     USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
smbd       1039     root   24u  IPv6    8113      0t0  TCP *:445 (LISTEN)
smbd       1039     root   25u  IPv6    8115      0t0  TCP *:139 (LISTEN)
avahi-dae  1219    avahi   13u  IPv4    7944      0t0  UDP *:5353 
avahi-dae  1219    avahi   14u  IPv6    7945      0t0  UDP *:5353 
avahi-dae  1219    avahi   15u  IPv4    7946      0t0  UDP *:47511 
avahi-dae  1219    avahi   16u  IPv6    7947      0t0  UDP *:49318 
cupsd      1237     root    5u  IPv6 3979269      0t0  TCP [::1]:631 (LISTEN)
cupsd      1237     root    6u  IPv4 3979270      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient   1332     root    5u  IPv4    8310      0t0  UDP *:68 
mysqld     1477    mysql   10u  IPv4    9233      0t0  TCP 192.168.1.101:3306 (LISTEN)
nmbd       1647     root    9u  IPv4    8914      0t0  UDP *:137 
nmbd       1647     root   10u  IPv4    8915      0t0  UDP *:138 
nmbd       1647     root   11u  IPv4    8917      0t0  UDP 192.168.122.1:137 
nmbd       1647     root   12u  IPv4    8918      0t0  UDP 192.168.122.255:137 
nmbd       1647     root   13u  IPv4    8919      0t0  UDP 192.168.122.1:138 
nmbd       1647     root   14u  IPv4    8920      0t0  UDP 192.168.122.255:138 
nmbd       1647     root   15u  IPv4    8921      0t0  UDP 192.168.1.101:137 
nmbd       1647     root   16u  IPv4    8922      0t0  UDP 192.168.1.255:137 
nmbd       1647     root   17u  IPv4    8923      0t0  UDP 192.168.1.101:138 
nmbd       1647     root   18u  IPv4    8924      0t0  UDP 192.168.1.255:138 
nmbd       1647     root   21u  IPv4   18602      0t0  UDP 5.72.24.124:137 
nmbd       1647     root   22u  IPv4   18603      0t0  UDP 5.255.255.255:137 
nmbd       1647     root   23u  IPv4   18604      0t0  UDP 5.72.24.124:138 
nmbd       1647     root   24u  IPv4   18605      0t0  UDP 5.255.255.255:138 
ntpd       1693      ntp   16u  IPv4    9066      0t0  UDP *:123 
ntpd       1693      ntp   17u  IPv6    9067      0t0  UDP *:123 
ntpd       1693      ntp   18u  IPv6    9071      0t0  UDP [fe80::222:15ff:fe54:faa6]:123 
ntpd       1693      ntp   19u  IPv6    9072      0t0  UDP [fe80::609a:9bff:fe2f:4ce3]:123 
ntpd       1693      ntp   20u  IPv6    9074      0t0  UDP [::1]:123 
ntpd       1693      ntp   21u  IPv4    9075      0t0  UDP 127.0.0.1:123 
ntpd       1693      ntp   22u  IPv4    9076      0t0  UDP 192.168.1.101:123 
ntpd       1693      ntp   23u  IPv4    9077      0t0  UDP 192.168.122.1:123 
ntpd       1693      ntp   24u  IPv4   21105      0t0  UDP 5.72.24.124:123 
dnsmasq    1698   nobody    5u  IPv4    9080      0t0  UDP *:67 
dnsmasq    1698   nobody    6u  IPv4    9087      0t0  TCP 192.168.122.1:53 (LISTEN)
dnsmasq    1698   nobody    7u  IPv4    9088      0t0  UDP 192.168.122.1:53 
beam.smp   1748  couchdb   10u  IPv4   10716      0t0  TCP 127.0.0.1:5984 (LISTEN)
hamachid   2269     root    8u  IPv4   12180      0t0  TCP 192.168.1.101:48687->64.94.18.75:12975 (ESTABLISHED)
hamachid   2269     root    9u  IPv4   12275      0t0  UDP 192.168.1.101:51662 
hamachid   2269     root   11u  IPv4   12290      0t0  UDP *:1900 
master     2433     root   12u  IPv4   12389      0t0  TCP *:25 (LISTEN)
gpsd       2459   nobody    4u  IPv4   12527      0t0  TCP 127.0.0.1:2947 (LISTEN)
gpsd       2459   nobody    5u  IPv6   12528      0t0  TCP [::1]:2947 (LISTEN)
miniserv.  2644     root    5u  IPv4   13317      0t0  TCP *:10000 (LISTEN)
miniserv.  2644     root    6u  IPv4   13318      0t0  UDP *:10000 
vino-serv 11988    scott   17u  IPv6 4433611      0t0  TCP *:5900 (LISTEN)
vino-serv 11988    scott   18u  IPv4 4433612      0t0  TCP *:5900 (LISTEN)
dropbox   12011    scott   14u  IPv4 4435746      0t0  TCP 192.168.1.101:38926->208.43.202.53:443 (CLOSE_WAIT)
dropbox   12011    scott   19u  IPv4 4436004      0t0  TCP 192.168.1.101:58290->208.43.202.51:443 (CLOSE_WAIT)
dropbox   12011    scott   20u  IPv4 4435950      0t0  UDP *:17500 
dropbox   12011    scott   23u  IPv4 4435954      0t0  TCP *:17500 (LISTEN)
dropbox   12011    scott   25u  IPv4 4444045      0t0  TCP 192.168.1.101:34805->173.193.134.216:443 (ESTABLISHED)
dropbox   12011    scott   26u  IPv4 4446112      0t0  TCP 192.168.1.101:41486->174.36.30.106:80 (ESTABLISHED)
gweather- 12188    scott   20w  IPv4 4499555      0t0  TCP 192.168.1.101:33698->72.246.94.51:80 (CLOSE_WAIT)
gweather- 12188    scott   24r  IPv4 4499557      0t0  TCP 192.168.1.101:33699->72.246.94.51:80 (CLOSE_WAIT)
clock-app 12191    scott   23w  IPv4 4499553      0t0  TCP 192.168.1.101:33697->72.246.94.51:80 (CLOSE_WAIT)
chrome    12290    scott  108r  IPv4 4513515      0t0  TCP 192.168.1.101:40870->74.125.226.108:80 (ESTABLISHED)
chrome    12290    scott  109u  IPv4 4445864      0t0  TCP 192.168.1.101:52187->74.125.226.119:443 (ESTABLISHED)
chrome    12290    scott  160u  IPv4 4438461      0t0  TCP 192.168.1.101:33252->72.246.94.34:80 (ESTABLISHED)
chrome    12290    scott  163u  IPv4 4438860      0t0  TCP 192.168.1.101:33268->72.246.94.34:80 (ESTABLISHED)
chrome    12290    scott  165u  IPv4 4513731      0t0  TCP 192.168.1.101:51444->74.125.226.105:80 (ESTABLISHED)
chrome    12290    scott  166u  IPv4 4438861      0t0  TCP 192.168.1.101:33269->72.246.94.34:80 (ESTABLISHED)
chrome    12290    scott  176u  IPv4 4438862      0t0  TCP 192.168.1.101:33270->72.246.94.34:80 (ESTABLISHED)
chrome    12290    scott  184u  IPv4 4438696      0t0  TCP 192.168.1.101:42595->74.125.226.116:443 (ESTABLISHED)
chrome    12290    scott  185u  IPv4 4438863      0t0  TCP 192.168.1.101:33271->72.246.94.34:80 (ESTABLISHED)
chrome    12290    scott  187u  IPv4 4438864      0t0  TCP 192.168.1.101:33272->72.246.94.34:80 (ESTABLISHED)
apache2   12402 www-data    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
apache2   12487 www-data    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
chrome    12521    scott   30w  IPv4 4443097      0t0  TCP 127.0.0.1:54686->127.0.0.1:42678 (ESTABLISHED)
ubuntuone 12524    scott   18u  IPv4 4443258      0t0  TCP 192.168.1.101:52023->174.129.193.12:443 (ESTABLISHED)
GoogleTal 12526    scott   16u  IPv4 4443019      0t0  TCP 127.0.0.1:42678 (LISTEN)
GoogleTal 12526    scott   17u  IPv4 4443098      0t0  TCP 127.0.0.1:42678->127.0.0.1:54686 (ESTABLISHED)
apache2   14293     root    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
apache2   18730 www-data    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
apache2   18731 www-data    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
apache2   18732 www-data    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
apache2   18733 www-data    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
apache2   18734 www-data    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
apache2   19396 www-data    3u  IPv4  209541      0t0  TCP *:80 (LISTEN)
scott@scott-desktop:~$ 

```

```
scott@scott-desktop:~$ sudo nmap -sV 192.168.1.101

Starting Nmap 5.21 ( http://nmap.org ) at 2011-03-06 17:26 EST
Nmap scan report for scott-desktop (192.168.1.101)
Host is up (0.0000080s latency).
Not shown: 993 closed ports
PORT      STATE SERVICE     VERSION
25/tcp    open  smtp        Postfix smtpd
80/tcp    open  http        Apache httpd 2.2.16 ((Ubuntu))
139/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
3306/tcp  open  mysql       MySQL 5.1.49-1ubuntu8.1
5900/tcp  open  vnc         VNC (protocol 3.7)
10000/tcp open  http        MiniServ 0.01 (Webmin httpd)
Service Info: Host:  scott-desktop

Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.18 seconds
scott@scott-desktop:~$ 


```

---

### Post by sdowney717 on 2011-03-06
I think i got it working. 
I told Apache2  to listen to port 8080
and I told the router top DMZ the 192.168.1.101 ip

Now open port check sees me.
Is there a way to do this without dong the DMZ router ip assignment?

---

### Post by sdowney717 on 2011-03-06
now if I goto my IP address which is on the web, I see my index.html file I put in my public_html folder
edit, I tried changing file names, now nothing shows up.

I tried loading several PHP pages I made in that folder, but nothing is happening.
DOES it ALWAYS need to start at index.html?
OR
should you be able to goto 
ipadress:8080/somefile.php ?

ALL these PHP pages I can run from 
localhost/somepage.php

---

### Post by junapp on 2011-03-06
> **sdowney717 said:**
> 
DOES it ALWAYS need to start at index.html?


You may want to read up on the DirectoryIndex directive in Apache:
[http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex](http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex)

---

