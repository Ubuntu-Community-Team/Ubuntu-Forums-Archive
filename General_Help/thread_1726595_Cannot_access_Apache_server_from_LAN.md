---
title: "Cannot access Apache server from LAN"
date: 2011-04-11
forum: General Help
---

### Post by StrykerGT on 2011-04-11
I'm having a problem when I try to connect to my apache2 server from any client in my network using the .local address with the firewall on. I opened the port 5353 UDP but I still can't connect. The only way I can connect is disabling the firewall which I don't like to do on the server. What I'm doing wrong?

---

### Post by CharlesA on 2011-04-11
Apache uses TCP port 80 by default.

---

### Post by StrykerGT on 2011-04-11
I opened port 80, 8080, 21 and 5353. If I type the ip address of the server it work without problems but if I use server.local it won't connect.

---

### Post by crispy_420 on 2011-04-11
That is a DNS issue not an apache/firewall problem. Do you use your own local DNS server, my guess is no. No quick fix to meet your needs I think. You could also add a DNS server to the same box as your apache server if you really wanted.

---

### Post by StrykerGT on 2011-04-11
> **crispy_420 said:**
> That is a DNS issue not an apache/firewall problem. Do you use your own local DNS server, my guess is no. No quick fix to meet your needs I think. You could also add a DNS server to the same box as your apache server if you really wanted.

I don't think is a DNS issue because if I disable the firewall I can connect from any device using server.local without any problems.

---

### Post by CharlesA on 2011-04-11
> **StrykerGT said:**
> I opened port 80, 8080, 21 and 5353. If I type the ip address of the server it work without problems but if I use server.local it won't connect.
Why do you have port 5353 open? DNS uses UDP 53.

---

### Post by StrykerGT on 2011-04-11
> **CharlesA said:**
> Why do you have port 5353 open? DNS uses UDP 53.

I read that I need that port open for the zeroconf service. I also opened 53 UDP and still can't connect. But if I disable the firewall it works flawlessly.

---

### Post by CharlesA on 2011-04-11
It would be a good start to see what all is listening for connections by running this:

```
sudo netstat -nlp
```

---

### Post by StrykerGT on 2011-04-11
> **CharlesA said:**
> It would be a good start to see what all is listening for connections by running this:

```
sudo netstat -nlp
```

Here is the output.

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1221/cupsd      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1410/mysqld     
tcp6       0      0 :::80                   :::*                    LISTEN      1548/apache2    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1221/cupsd      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1229/avahi-daemon: 
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1446/dhclient   
udp        0      0 0.0.0.0:59602           0.0.0.0:*                           1229/avahi-daemon: 
udp6       0      0 :::39466                :::*                                1229/avahi-daemon: 
udp6       0      0 :::5353                 :::*                                1229/avahi-daemon: 
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     11755    1966/dbus-daemon    @/tmp/dbus-tP9ddiXGX4
unix  2      [ ACC ]     STREAM     LISTENING     6968     1151/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     29569    4394/dbus-daemon    @/tmp/dbus-sJqyszG4I0
unix  2      [ ACC ]     STREAM     LISTENING     7502     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     14008    2131/unity-window-d /tmp/orbit-stryker/linc-853-0-7542dee465ec2
unix  2      [ ACC ]     STREAM     LISTENING     13097    2142/unity-panel-se /tmp/orbit-stryker/linc-85e-0-19b7049b9f42
unix  2      [ ACC ]     STREAM     LISTENING     13131    2177/indicator-sess /tmp/orbit-stryker/linc-881-0-16665cb0d90da
unix  2      [ ACC ]     STREAM     LISTENING     14278    2181/indicator-date /tmp/orbit-stryker/linc-885-0-2f59f96bb732
unix  2      [ ACC ]     STREAM     LISTENING     8667     1379/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     30600    4397/gconfd-2       /tmp/orbit-root/linc-112d-0-6dae3a0a16acf
unix  2      [ ACC ]     STREAM     LISTENING     30606    4389/nautilus       /tmp/orbit-root/linc-1125-0-7571814417e9b
unix  2      [ ACC ]     STREAM     LISTENING     8699     1465/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     48253    5870/gnome-terminal /tmp/orbit-stryker/linc-16ee-0-2531cb011a663
unix  2      [ ACC ]     STREAM     LISTENING     11229    1996/gnome-settings /tmp/orbit-stryker/linc-7cc-0-47da7b7babe77
unix  2      [ ACC ]     STREAM     LISTENING     11239    1908/gnome-keyring- /tmp/keyring-Hf8vAz/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     11159    1908/gnome-keyring- /tmp/keyring-Hf8vAz/ssh
unix  2      [ ACC ]     STREAM     LISTENING     15693    2222/python         /tmp/orbit-stryker/linc-8ae-0-2d23320f6494b
unix  2      [ ACC ]     STREAM     LISTENING     8666     1379/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     13461    2039/nm-applet      /tmp/orbit-stryker/linc-7f7-0-3ddf7706178bb
unix  2      [ ACC ]     STREAM     LISTENING     8564     1221/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     12318    2010/compiz         /tmp/orbit-stryker/linc-7da-0-1764f60a831c6
unix  2      [ ACC ]     STREAM     LISTENING     13243    2203/geoclue-master /tmp/orbit-stryker/linc-89b-0-2314c4431a0e1
unix  2      [ ACC ]     STREAM     LISTENING     10926    1962/ssh-agent      /tmp/ssh-EBGEBpHz1927/agent.1927
unix  2      [ ACC ]     STREAM     LISTENING     10335    1324/gdm-simple-sla @/tmp/gdm-session-ZLSpKsTA
unix  2      [ ACC ]     STREAM     LISTENING     11776    1927/gnome-session  /tmp/.ICE-unix/1927
unix  2      [ ACC ]     STREAM     LISTENING     13311    2180/indicator-me-s /tmp/orbit-stryker/linc-884-0-66fe8ad6242f0
unix  2      [ ACC ]     STREAM     LISTENING     11795    1971/gconfd-2       /tmp/orbit-stryker/linc-7b3-0-16f03c90441fc
unix  2      [ ACC ]     STREAM     LISTENING     15508    2141/unity-applicat /tmp/orbit-stryker/linc-85d-0-6d15797e5d4e8
unix  2      [ ACC ]     STREAM     LISTENING     11799    1927/gnome-session  /tmp/orbit-stryker/linc-787-0-c8c9c974ac29
unix  2      [ ACC ]     STREAM     LISTENING     10246    1324/gdm-simple-sla @/tmp/gdm-greeter-sowviYYd
unix  2      [ ACC ]     STREAM     LISTENING     12321    2013/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     12323    2013/pulseaudio     /home/stryker/.pulse/3fc81ff47734cfcfd499afd900000006-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     12081    2017/gconf-helper   /tmp/orbit-stryker/linc-7e1-0-328a688d8be6e
unix  2      [ ACC ]     STREAM     LISTENING     13530    2041/gnome-power-ma /tmp/orbit-stryker/linc-7f9-0-7b0baed63925b
unix  2      [ ACC ]     STREAM     LISTENING     12589    2054/notify-osd     /tmp/orbit-stryker/linc-806-0-49846a59978f7
unix  2      [ ACC ]     STREAM     LISTENING     13542    2032/nautilus       /tmp/orbit-stryker/linc-7f0-0-74682760af60d
unix  2      [ ACC ]     STREAM     LISTENING     12616    2043/evolution-alar /tmp/orbit-stryker/linc-7fb-0-1dfcd88499d6
unix  2      [ ACC ]     STREAM     LISTENING     12688    2094/gnome-screensa /tmp/orbit-stryker/linc-81c-0-5c2756061b287
unix  2      [ ACC ]     STREAM     LISTENING     8616     1373/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     12713    2071/e-calendar-fac /tmp/orbit-stryker/linc-817-0-63df4671f511
unix  2      [ ACC ]     STREAM     LISTENING     12781    2086/e-addressbook- /tmp/orbit-stryker/linc-826-0-79ec2ab096610
unix  2      [ ACC ]     STREAM     LISTENING     9920     1465/bluetoothd     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     16203    2332/update-notifie /tmp/orbit-stryker/linc-91c-0-2f6457a1a878d
unix  2      [ ACC ]     STREAM     LISTENING     8690     1410/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     10779    1908/gnome-keyring- /tmp/keyring-Hf8vAz/control
unix  2      [ ACC ]     STREAM     LISTENING     8439     1229/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     11775    1927/gnome-session  @/tmp/.ICE-unix/1927
```

---

### Post by StrykerGT on 2011-04-11
Any idea what could be the problem? I'm really new on the Linux world. 

I tried editing the ports.conf file and the output now is. But I still have this issue.

Thanks for the help


```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      6977/apache2    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1221/cupsd      
tcp        0      0 0.0.0.0:5353            0.0.0.0:*               LISTEN      6977/apache2    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1410/mysqld     
tcp6       0      0 ::1:631                 :::*                    LISTEN      1221/cupsd      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1229/avahi-daemon: 
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1446/dhclient   
udp        0      0 0.0.0.0:59602           0.0.0.0:*                           1229/avahi-daemon: 
udp6       0      0 :::39466                :::*                                1229/avahi-daemon: 
udp6       0      0 :::5353                 :::*                                1229/avahi-daemon: 
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     11755    1966/dbus-daemon    @/tmp/dbus-tP9ddiXGX4
unix  2      [ ACC ]     STREAM     LISTENING     6968     1151/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     29569    4394/dbus-daemon    @/tmp/dbus-sJqyszG4I0
unix  2      [ ACC ]     STREAM     LISTENING     7502     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     14008    2131/unity-window-d /tmp/orbit-stryker/linc-853-0-7542dee465ec2
unix  2      [ ACC ]     STREAM     LISTENING     13097    2142/unity-panel-se /tmp/orbit-stryker/linc-85e-0-19b7049b9f42
unix  2      [ ACC ]     STREAM     LISTENING     13131    2177/indicator-sess /tmp/orbit-stryker/linc-881-0-16665cb0d90da
unix  2      [ ACC ]     STREAM     LISTENING     14278    2181/indicator-date /tmp/orbit-stryker/linc-885-0-2f59f96bb732
unix  2      [ ACC ]     STREAM     LISTENING     8667     1379/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     30600    4397/gconfd-2       /tmp/orbit-root/linc-112d-0-6dae3a0a16acf
unix  2      [ ACC ]     STREAM     LISTENING     30606    4389/nautilus       /tmp/orbit-root/linc-1125-0-7571814417e9b
unix  2      [ ACC ]     STREAM     LISTENING     8699     1465/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     48253    5870/gnome-terminal /tmp/orbit-stryker/linc-16ee-0-2531cb011a663
unix  2      [ ACC ]     STREAM     LISTENING     11229    1996/gnome-settings /tmp/orbit-stryker/linc-7cc-0-47da7b7babe77
unix  2      [ ACC ]     STREAM     LISTENING     48382    5933/firefox-bin    /tmp/orbit-stryker/linc-172d-0-14d862631bb3f
unix  2      [ ACC ]     STREAM     LISTENING     52497    6707/thunderbird-bi /tmp/orbit-stryker/linc-1a33-0-3359bab177755
unix  2      [ ACC ]     STREAM     LISTENING     11239    1908/gnome-keyring- /tmp/keyring-Hf8vAz/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     11159    1908/gnome-keyring- /tmp/keyring-Hf8vAz/ssh
unix  2      [ ACC ]     STREAM     LISTENING     15693    2222/python         /tmp/orbit-stryker/linc-8ae-0-2d23320f6494b
unix  2      [ ACC ]     STREAM     LISTENING     8666     1379/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     13461    2039/nm-applet      /tmp/orbit-stryker/linc-7f7-0-3ddf7706178bb
unix  2      [ ACC ]     STREAM     LISTENING     8564     1221/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     12318    2010/compiz         /tmp/orbit-stryker/linc-7da-0-1764f60a831c6
unix  2      [ ACC ]     STREAM     LISTENING     13243    2203/geoclue-master /tmp/orbit-stryker/linc-89b-0-2314c4431a0e1
unix  2      [ ACC ]     STREAM     LISTENING     10926    1962/ssh-agent      /tmp/ssh-EBGEBpHz1927/agent.1927
unix  2      [ ACC ]     STREAM     LISTENING     10335    1324/gdm-simple-sla @/tmp/gdm-session-ZLSpKsTA
unix  2      [ ACC ]     STREAM     LISTENING     11776    1927/gnome-session  /tmp/.ICE-unix/1927
unix  2      [ ACC ]     STREAM     LISTENING     13311    2180/indicator-me-s /tmp/orbit-stryker/linc-884-0-66fe8ad6242f0
unix  2      [ ACC ]     STREAM     LISTENING     11795    1971/gconfd-2       /tmp/orbit-stryker/linc-7b3-0-16f03c90441fc
unix  2      [ ACC ]     STREAM     LISTENING     15508    2141/unity-applicat /tmp/orbit-stryker/linc-85d-0-6d15797e5d4e8
unix  2      [ ACC ]     STREAM     LISTENING     11799    1927/gnome-session  /tmp/orbit-stryker/linc-787-0-c8c9c974ac29
unix  2      [ ACC ]     STREAM     LISTENING     10246    1324/gdm-simple-sla @/tmp/gdm-greeter-sowviYYd
unix  2      [ ACC ]     STREAM     LISTENING     12321    2013/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     12323    2013/pulseaudio     /home/stryker/.pulse/3fc81ff47734cfcfd499afd900000006-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     12081    2017/gconf-helper   /tmp/orbit-stryker/linc-7e1-0-328a688d8be6e
unix  2      [ ACC ]     STREAM     LISTENING     13530    2041/gnome-power-ma /tmp/orbit-stryker/linc-7f9-0-7b0baed63925b
unix  2      [ ACC ]     STREAM     LISTENING     12589    2054/notify-osd     /tmp/orbit-stryker/linc-806-0-49846a59978f7
unix  2      [ ACC ]     STREAM     LISTENING     13542    2032/nautilus       /tmp/orbit-stryker/linc-7f0-0-74682760af60d
unix  2      [ ACC ]     STREAM     LISTENING     12616    2043/evolution-alar /tmp/orbit-stryker/linc-7fb-0-1dfcd88499d6
unix  2      [ ACC ]     STREAM     LISTENING     12688    2094/gnome-screensa /tmp/orbit-stryker/linc-81c-0-5c2756061b287
unix  2      [ ACC ]     STREAM     LISTENING     8616     1373/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     53155    6792/npviewer.bin   @/org/wrapper/NSPlugins/libflashplayer.so/6779-1
unix  2      [ ACC ]     STREAM     LISTENING     12713    2071/e-calendar-fac /tmp/orbit-stryker/linc-817-0-63df4671f511
unix  2      [ ACC ]     STREAM     LISTENING     12781    2086/e-addressbook- /tmp/orbit-stryker/linc-826-0-79ec2ab096610
unix  2      [ ACC ]     STREAM     LISTENING     9920     1465/bluetoothd     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     16203    2332/update-notifie /tmp/orbit-stryker/linc-91c-0-2f6457a1a878d
unix  2      [ ACC ]     STREAM     LISTENING     8690     1410/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     10779    1908/gnome-keyring- /tmp/keyring-Hf8vAz/control
unix  2      [ ACC ]     STREAM     LISTENING     8439     1229/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     11775    1927/gnome-session  @/tmp/.ICE-unix/1927

```

---

### Post by CharlesA on 2011-04-11
I still think it's a DNS issue.

Try this: Add the name you want to access the machine with to another machines /etc/hosts file and then try to connect that way. If it connects, it's a problem with name resolution.

Also, telling apache to listen on TCP port 5353 isn't going to do anything.

---

### Post by StrykerGT on 2011-04-11
> **CharlesA said:**
> I still think it's a DNS issue.

Try this: Add the name you want to access the machine with to another machines /etc/hosts file and then try to connect that way. If it connects, it's a problem with name resolution.

Also, telling apache to listen on TCP port 5353 isn't going to do anything.

I tried with a Windows 7 laptop and nothing. The second I disable the firewall it works. 

How I can specify UDP 5353 on Apache to start listening.

Sorry to keep bothering but I really want this to work. Thanks.

---

### Post by CharlesA on 2011-04-11
Apache isn't the problem since it works with the ip address.

It's more then likely a problem with the zeroconf name resolution daemon - avahi. I don't use it since I use dnsmasq.

Did you add the hostname to the c:\windows\system32\drivers\etc\hosts file?

---

### Post by 5149.5 on 2011-04-11
You'll be be better off concentrating on TCP 80 and forgetting UDP 5353.

---

### Post by 5149.5 on 2011-04-11
> **StrykerGT said:**
> If I type the ip address of the server it work without problems but if I use server.local it won't connect.

DNS issue like Charles keeps telling you. You have probably confused yourself by changing more than one thing at a time and drawing a false conclusion.

---

### Post by StrykerGT on 2011-04-11
Ok thanks.

---

