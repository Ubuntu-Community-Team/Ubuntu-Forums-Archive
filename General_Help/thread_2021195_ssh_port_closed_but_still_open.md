---
title: "ssh port closed but still open"
date: 2012-07-08
forum: General Help
---

### Post by mrjahvi on 2012-07-08
i am using lucid 10.04 amd64 with ssh post closed by iptables also fail2ban. Pcflank says everything is locked and good but GRC [ShieldsUP!] firewall  says port 22 is open. Now this happens every time in public wifi. Is this normal?

---

### Post by efflandt on 2012-07-08
If you are on public WiFi, you are behind a broadband router, and if port 22 goes to the router or forwarded to somewhere else at that location that likely has nothing to do with you.

Why would you be running sshd and totally block it?  I have mine configured to accept keys only, not any passwords.  So crackers can try guessing usernames and passwords all day and night without getting in.

An IPCop server I have at work for a squid proxy has ssh on a different port, so it does not get hit with probes for port 22.

---

### Post by mrjahvi on 2012-07-09
Why would you be running sshd ? im not... i would like to close it. did everything i can to keep the port closed. but it still is open. all service ports are blocked

---

### Post by Cheesehead on 2012-07-09
> **mrjahvi said:**
> ssh post closed by iptables .... port 22 is open. Is this normal?

Not really. Perhaps your ssh port is not as closed as you think.

1) Find out if an application is really opening port 22. Try the [FONT="Courier New"]netstat[/FONT] command:
```
$ sudo netstat -tulpn | grep 22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      512/sshd        
tcp6       0      0 :::22                   :::*                    LISTEN      512/sshd             
```
In this example, look at the port number (:22) and the last column (512/sshd). You can see that sshd (openssh_server, PID #512) is listening on port 22.

Once you figure out which application has the port open, we can show you how to disable it at startup.

2) Check your firewall rules using the [FONT="Courier New"]iptables[/FONT] command:
```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```
In this example, you can see that the firewall is turned on, but blocks nothing. This is, by the way, the default for Ubuntu.

Once you figure out exactly which ports you want to block with a firewall, we can show you how. It's only neccessary to block certain open ports - ports that an application is listening upon.

---

### Post by SeijiSensei on 2012-07-09
If you don't want the machine to listen for SSH requests, don't run the openssh server.  At a terminal prompt type:

```

sudo service ssh stop
sudo chkconfig -s ssh off

```

Now the server is shutdown and won't be restarted at boot.

However there's a [bug]("http://ubuntuforums.org/showthread.php?t=2006290") in 12.04 that will interfere with this.  To fix it run,

```

cd /sbin
sudo ln -s ../usr/lib/insserv/insserv

```

then use chkconfig as I describe above.  The bug appears to be [fixed]("https://bugs.launchpad.net/ubuntu/+source/chkconfig/+bug/1000834"), so this problem may not recur in 12.04.1 which will be released soon.

---

### Post by mrjahvi on 2012-07-09
thank you for the response i will try these out   im trying out a different version  of linux today on a back up hdd. i couldt use the  1st command but tried this        # netstat --tcp
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 guest-reg-56-28.a:52548 ord08s05-in-f17.1e:http ESTABLISHED
tcp        0      0 guest-reg-56-28.a:35985 ie-in-f191.1e100.n:http ESTABLISHED
tcp        0      0 guest-reg-56-28.a:53225 [www.grc.com:http](www.grc.com:http)        ESTABLISHED
tcp        0      0 guest-reg-56-28.a:35980 ie-in-f191.1e100.n:http ESTABLISHED
tcp        0      0 guest-reg-56-28.a:59481 [www.grc.com:https](www.grc.com:https)       ESTABLISHED
tcp        0      0 guest-reg-56-28.a:59477 [www.grc.com:https](www.grc.com:https)       ESTABLISHED
tcp        0      0 guest-reg-56-28.a:35990 ie-in-f191.1e100.n:http ESTABLISHED
tcp        0      0 guest-reg-56-28.a:53227 [www.grc.com:http](www.grc.com:http)        ESTABLISHED
tcp        0      0 guest-reg-56-28.a:53229 [www.grc.com:http](www.grc.com:http)        ESTABLISHED
tcp        0      0 guest-reg-56-28.a:59483 [www.grc.com:https](www.grc.com:https)       ESTABLISHED
tcp        0      0 guest-reg-56-28.a:59482 [www.grc.com:https](www.grc.com:https)       ESTABLISHED
tcp        0      0 guest-reg-56-28.a:53226 [www.grc.com:http](www.grc.com:http)        ESTABLISHED
tcp        0      0 guest-reg-56-28.a:49018 den03s06-in-f17.1e:http ESTABLISHED
tcp        0      0 guest-reg-56-28.a:53228 [www.grc.com:http](www.grc.com:http)        ESTABLISHED
tcp        0      0 guest-reg-56-28.a:35986 ie-in-f191.1e100.n:http ESTABLISHED
tcp        0      0 guest-reg-56-28.a:42641 ord08s09-in-f10.1e:http ESTABLISHED
tcp        0      0 guest-reg-56-28.a:35981 ie-in-f191.1e100.n:http ESTABLISHED
tcp        0      0 guest-reg-56-28.a:59478 [www.grc.com:https](www.grc.com:https)       ESTABLISHED
tcp        0      0 guest-reg-56-28.a:52547 ord08s05-in-f17.1e:http ESTABLISHED
tcp6       0      0 guest-reg-56-28.a:36292 cds885.ord.llnw.ne:http ESTABLISHED
tcp6       0      0 guest-reg-56-28.a:51570 cds853.ord.llnw.ne:http ESTABLISHED
tcp6       0      0 guest-reg-56-28.a:36291 cds885.ord.llnw.ne:http ESTABLISHED
and this was my result. i plan to switch back so i can work further.

---

### Post by Cheesehead on 2012-07-09
Unfortunately, that netstat output is unhelpful. We really need the -tulpn output from the specific system you are asking about. A different linux will have a different result.

---

### Post by mrjahvi on 2012-07-13
ok i tried your suggestions and this is the output  :       root@irr-irr:/home/jinarr# sudo netstat -tulpn | grep 22
root@irr-irr:/home/jinarr# sudo netstat -tulpn | grep 22
root@irr-irr:/home/jinarr# netstat -tulpn | grep 22
root@irr-irr:/home/jinarr# sudo service ssh stop
ssh: unrecognized service
root@irr-irr:/home/jinarr# sudo chkconfig -s ssh off
sudo: chkconfig: command not found
root@irr-irr:/home/jinarr# cd /sbin
root@irr-irr:/sbin# sudo ln -s ../usr/lib/insserv/insserv
ln: creating symbolic link `./insserv': File exists
root@irr-irr:/sbin# 
 
for some reason no other results given.

---

### Post by mrjahvi on 2012-07-13
here it shows open [IMG]http://i758.photobucket.com/albums/xx229/mrjahvi/Screenshot-10.png[/IMG]

---

### Post by mrjahvi on 2012-07-13
here is my firewall :                                        #!/bin/bash
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
################################################################################                                                                                    iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
 
#Allow loopback
iptables -t filter -A INPUT -i lo -j ACCEPT 
iptables -t filter -A OUTPUT -o lo -j ACCEPT                                                                                                                                                                                                                                                                                                                                
#################################################################
                                                                                                                                                                                                                                                                                         
###########4days test ##########                                                                                                                                   
iptables -A INPUT   -m recent --name portscan --rcheck --seconds 345600 -j DROP
iptables -A FORWARD -m recent --name portscan --rcheck --seconds 345600 -j DROP                                                                               
#                                                                                                                                                                                                                                                                                          
################################################################################
### Don't Allow all ICMP Traffic (optional) - IN, OUT and THROUGH ###                                                                                                # Disable source routing
echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route
echo "0" > /proc/sys/net/ipv4/conf/lo/accept_source_route
echo "0" > /proc/sys/net/ipv4/conf/eth0/accept_source_route
echo "0" > /proc/sys/net/ipv4/conf/ath0/accept_source_route
echo "0" > /proc/sys/net/ipv4/conf/ath1/accept_source_route
echo "0" > /proc/sys/net/ipv4/conf/default/accept_source_route
# Enable TCP SYN Cookie potection
echo "1" > /proc/sys/net/ipv4/tcp_syncookies
# No ICMP Redirect
echo "0" > /proc/sys/net/ipv4/conf/all/accept_redirects
echo "0" > /proc/sys/net/ipv4/conf/lo/accept_redirects
echo "0" > /proc/sys/net/ipv4/conf/eth0/accept_redirects
echo "0" > /proc/sys/net/ipv4/conf/ath0/accept_redirects
echo "0" > /proc/sys/net/ipv4/conf/ath1/accept_redirects
echo "0" > /proc/sys/net/ipv4/conf/default/accept_redirects                                                                                                        echo 0 > /proc/sys/net/ipv6/conf/all/accept_ra
echo 0 > /proc/sys/net/ipv6/conf/default/accept_ra
echo 0 > /proc/sys/net/ipv6/conf/all/autoconf
echo 0 > /proc/sys/net/ipv6/conf/default/autoconf                                                                                                                   echo "0" > /proc/sys/net/ipv6/conf/all/accept_redirects                                                                                                           echo "0" > /proc/sys/net/ipv6/conf/all/forwarding                                                                                                                    echo "0" > /proc/sys/net/ipv6/conf/all/autoconf                                                                                                             ###############
# KERNEL PARAMETER CONFIGURATION
# PREVENT YOU SYSTEM FROM ANSWERING ICMP ECHO REQUESTS
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
# DROP ICMP ECHO-REQUEST MESSAGES SENT TO BROADCAST OR MULTICAST ADDRESSES
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
# DONT ACCEPT ICMP REDIRECT MESSAGES
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
# DONT SEND ICMP REDIRECT MESSAGES
echo 0 > /proc/sys/net/ipv4/conf/all/send_redirects                                                                                                           iptables -A INPUT -p icmp -m icmp --icmp-type echo-request -j DROP
iptables -A INPUT -p icmp --icmp-type any -j DROP   ##
  
################################################################################      #                                                                                  #                                                                                                                                                              ##########Drop invalid packets immediately######################### #                                                                                    #################################################################################
iptables -I INPUT -p icmp --icmp-type redirect -j DROP  ##
iptables -I INPUT -p icmp --icmp-type router-advertisement -j DROP  ##
iptables -I INPUT -p icmp --icmp-type router-solicitation -j DROP  ##
iptables -I INPUT -p icmp --icmp-type address-mask-request -j DROP  ##
iptables -I INPUT -p icmp --icmp-type address-mask-reply -j DROP   ## 
iptables -A INPUT -p icmp --icmp-type 8 -j DROP   ##
iptables -A INPUT -p icmp --icmp-type fragmentation-needed -j DROP                                                                                            iptables -A INPUT -p icmp --icmp-type network-redirect -j DROP                                                                                                iptables -A INPUT -p icmp --icmp-type host-redirect -j DROP                                                                                                   iptables -A INPUT -p icmp --icmp-type source-quench -j DROP  ##                                                                                                                                                                 iptables -A INPUT -p icmp --icmp-type 30 -j DROP                                                                                                             #iptables -A INPUT -p icmp –icmp-type echo-request –j DROP ##                                                                                                       #iptables -A INPUT -p tcp --syn -j DROP                                                                                                                       #iptables -A INPUT -f -j DROP  ##                                                                                                                              #iptables -A INPUT -p icmp -i wlan0-j DROP Bad argument DROP                                                                                                    ##
################################################################################                                                                                                                                                                                                                                                                                          
                                                                                          
                                                                                                                       iptables -A INPUT -p tcp --dport 0,1 -j DROP ##                                                                                                                 iptables -A INPUT -p udp --dport 0,1 -j DROP ##                                                                                                                  #iptables -A INPUT -p tcp --dport 22 -j DROP   ##                                                                                                              iptables -A INPUT -p tcp --dport 20,21,22,23,25,111,113,53,79,119 -j DROP   ##                                                                                iptables -A INPUT -p udp --dport 20,21,22,23,25,111,113,53,79,119 -j DROP ##                                                                                         #iptables -A OUTPUT -p udp --dport 21,22,23 -j DROP    ##                                                                                                            ## block IMAP POP Sendmail Postfix IMAPS" ###                                                                                                                    iptables -A INPUT -p tcp --dport 143,110,993,995,143,1080,1723,2049,5900 -j DROP                                                                                   iptables -A INPUT -p udp --dport 143,110,993,995,143,1080,1723,2049,5900 -j DROP ##                                                                            iptables -A INPUT -p tcp --dport 137 -j DROP    ##
iptables -A INPUT -p tcp --dport 138 -j DROP    ##
iptables -A INPUT -p tcp --dport 139 -j DROP    ##
iptables -A INPUT -p tcp --dport 445 -j DROP    ##
iptables -A INPUT -p udp --dport 137 -j DROP    ##
iptables -A INPUT -p udp --dport 138 -j DROP    ##
iptables -A INPUT -p udp --dport 139 -j DROP    ##
iptables -A INPUT -p udp --dport 445 -j DROP    ##   
iptables -A INPUT -p tcp --dport 135 -j DROP    ##
iptables -A INPUT -p udp --dport 135 -j DROP    ##  ##                                                                                                                                                                iptables -A INPUT -p tcp --dport 5000:5061 -j DROP                                                                                                             iptables -A INPUT -p udp --dport 5000:5061 -j DROP  ##
iptables -A INPUT -p tcp --dport 635 -j DROP   ##
iptables -A INPUT -p udp --dport 635 -j DROP    ##                                                                                                             #iptables -A INPUT -p udp --dport 33434:33523 -j DROP                                                                                                                 # Accept traceroutes
iptables -A INPUT -p udp -m udp --dport 33434:33523 -j DROP
################################################################################                         
#                                                                                                                                                                  
#                                                                                                  ################################################################################                                                                                                                                               ################################################################################                                                                                                                                                                iptables -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP  ##  ##                                                                                                                                                             iptables -A INPUT -p tcp --tcp-flags ALL FIN -j DROP  ##                                                                                                      iptables -A INPUT -p tcp --tcp-flags ACK,FIN FIN -j DROP  ##  ##                                                                                                                                                            iptables -A INPUT -p tcp --tcp-flags SYN,ACK SYN,ACK -j DROP  ##                                                                                              iptables -A INPUT -p tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j DROP                                                                  iptables -A INPUT -p tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,ACK,URG -j DROP   ##   ##                                                                                                                                                              iptables -A INPUT -p tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP   ##                                                                                iptables -A INPUT -p tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG -j DROP   ##                                                             iptables -A INPUT -p udp --tcp-flags FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG -j DROP   ##                                                             iptables -A INPUT -p tcp --tcp-flags FIN,URG,PSH FIN,URG,PSH -j DROP   ##
iptables -A INPUT -p tcp --tcp-flags ACK,PSH PSH -j DROP   ##
iptables -A INPUT -p tcp --tcp-flags ACK,URG URG -j DROP   ##
iptables -A INPUT -p tcp --tcp-flags FIN,RST FIN,RST -j DROP   ##
iptables -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP   ##
iptables -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j DROP   ##
iptables -A INPUT -p tcp --tcp-flags ALL ALL -j DROP       ##  ##                                                                                                                                                            iptables -A INPUT -p tcp --tcp-flags SYN,URG SYN,URG -j DROP        ##
iptables -A INPUT -p tcp --tcp-flags ALL NONE -j DROP       ##  ##                                                                                                                                                            iptables -A INPUT -p tcp --tcp-flags ALL RST,ACK,PSH,URG -j DROP  ##
iptables -A INPUT -p tcp --tcp-flags ALL FIN,PSH,URG -j DROP  ##
iptables -A INPUT -p tcp --tcp-flags ALL SYN,FIN,PSH,URG -j DROP  ##
iptables -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP  ##                                                                                          iptables -A INPUT -p tcp --tcp-flags FIN,ACK FIN -j DROP                                                                                         ##                                                                                                                                                            iptables -A INPUT -p tcp --tcp-flags ALL ACK,RST,SYN,FIN -j DROP ##                                                                                           iptables -A INPUT -p tcp --tcp-flags PSH,ACK PSH -j DROP   ##                                                                                                  iptables -A INPUT -p tcp --tcp-flags FIN,SYN,RST,ACK/RST -j DROP   ## ##                                                                                                                                                               iptables -A INPUT -p tcp --tcp-flags ACK,SYN,FIN,RST,URG,PSH RST -j DROP                                                                                         iptables -A INPUT -p tcp --tcp-flags RST RST -j DROP  ##                                                                                                        iptables -A INPUT -p tcp --tcp-flags  RST,RST -j DROP   ## ##                                                                                                                                                              iptables -A INPUT -p tcp --tcp-flags ALL SYN,ACK,PSH -j DROP  ##                                                                                              iptables -A INPUT -p tcp --tcp-flags FIN,SYN,RST,ACK/SYN -j DROP  ## ##                                                                                                                                                                iptables -A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP   ##    ##                                                                                                                                                             ##
iptables -A INPUT -p icmp --fragment -j DROP      ##
iptables -A INPUT -p icmp -m icmp --icmp-type timestamp-request -j DROP   ##                                                                                          IPTABLES -A INPUT  ICMP -p icmp --icmp-type 0 -j DROP
IPTABLES -A INPUT  ICMP -p icmp --icmp-type 3 -j DROP
IPTABLES -A INPUT  ICMP -p icmp --icmp-type 11 -j DROP                                                                                                               iptables -A INPUT -p tcp --tcp-flags SYN,ACK SYN,ACK -m state --state NEW -j DROP    ##
################################################################################                            
#        
#                                                                                                                                                                                                                                                                                                                                  
################################################################################                                                                                                                                                                                                                                                                                                                                        
iptables -A INPUT -p igmp -j DROP  ## ##                                                                                                                                                                                                                                                                                                                                  
                                                                                                                                                                  
                                                                                                                                                                  
                                     ################################################################################                                                                                                                                                                    #  SSH Remove ######                                                                                                                                            update-rc.d ssh remove                                                                                                                                           update-rc.d sshd remove                                                                                                                                       iptables -P INPUT DROP                                                                                                                                         iptables -A OUTPUT -j DROP

---

### Post by wirelessmonkey on 2012-07-13
Would it be possible to just post the output of
```

sudo iptables -L

```

Please?

---

### Post by mrjahvi on 2012-07-13
sudo lsof -i | grep 22
clock-app  1875 jinarr   22r  IPv4 102356      0t0  TCP guest-reg-57-5.aadl.org:48544->host25.factsmgt.com:www (CLOSE_WAIT)
chromium- 14422 jinarr   24w  IPv4 109435      0t0  TCP guest-reg-57-5.aadl.org:41438->209.17.88.50:www (CLOSE_WAIT)
####################################################################   ### CMD lsof###                                                        /lib/libtasn1.so.3.1.7
chromium- 14486     jinarr  mem       REG                8,4     10224   18350172 /lib/libkeyutils-1.2.so
chromium- 14486     jinarr  mem       REG                8,4     31168   24120721 /usr/lib/libkrb5support.so.0.1
chromium- 14486     jinarr  mem       REG                8,4     14584   18350132 /lib/libcom_err.so.2.1
chromium- 14486     jinarr  mem       REG                8,4    154048   24120715 /usr/lib/libk5crypto.so.3.1
chromium- 14486     jinarr  mem       REG                8,4    803192   24120719 /usr/lib/libkrb5.so.3.3
chromium- 14486     jinarr  mem       REG                8,4    117592   18350241 /lib/libselinux.so.1
chromium- 14486     jinarr  mem       REG                8,4     93000   18353597 /lib/libresolv-2.11.1.so
chromium- 14486     jinarr  mem       REG                8,4     22560   24120113 /usr/lib/libXdmcp.so.6.0.0
chromium- 14486     jinarr  mem       REG                8,4     14488   24120102 /usr/lib/libXau.so.6.0.0
chromium- 14486     jinarr  mem       REG                8,4     14344   18350165 /lib/libgpg-error.so.0.4.0
chromium- 14486     jinarr  mem       REG                8,4     68480   24120194 /usr/lib/libavahi-client.so.3.2.5
chromium- 14486     jinarr  mem       REG                8,4     51608   24120196 /usr/lib/libavahi-common.so.3.5.1
chromium- 14486     jinarr  mem       REG                8,4    663816   24120507 /usr/lib/libgnutls.so.26.14.12
chromium- 14486     jinarr  mem       REG                8,4    213784   24120549 /usr/lib/libgssapi_krb5.so.2.2
chromium- 14486     jinarr  mem       REG                8,4    139528   24120313 /usr/lib/libdbus-glib-1.so.2.1.0
chromium- 14486     jinarr  mem       REG                8,4    450072   24120088 /usr/lib/libORBit-2.so.0.1.0
chromium- 14486     jinarr  mem       REG                8,4     14504   24120876 /usr/lib/libplds4.so
chromium- 14486     jinarr  mem       REG                8,4     34888   24121106 /usr/lib/libxcb-render.so.0.0.0
chromium- 14486     jinarr  mem       REG                8,4     14536   24121104 /usr/lib/libxcb-render-util.so.0.0.0
chromium- 14486     jinarr  mem       REG                8,4     98000   24120329 /usr/lib/libdirect-1.2.so.0.8.0
chromium- 14486     jinarr  mem       REG                8,4     39448   24120406 /usr/lib/libfusion-1.2.so.0.8.0
chromium- 14486     jinarr  mem       REG                8,4    533800   24120331 /usr/lib/libdirectfb-1.2.so.0.8.0
chromium- 14486     jinarr  mem       REG                8,4    362664   24120873 /usr/lib/libpixman-1.so.0.16.4
chromium- 14486     jinarr  mem       REG                8,4     14536   24120473 /usr/lib/libgmodule-2.0.so.0.2400.1
chromium- 14486     jinarr  mem       REG                8,4    172128   24120847 /usr/lib/libpangoft2-1.0.so.0.2800.0
chromium- 14486     jinarr  mem       REG                8,4    727136   24120455 /usr/lib/libgio-2.0.so.0.2400.1
chromium- 14486     jinarr  mem       REG                8,4    133912   24120188 /usr/lib/libatk-1.0.so.0.3009.1
chromium- 14486     jinarr  mem       REG                8,4     10272   24120111 /usr/lib/libXdamage.so.1.1.0
chromium- 14486     jinarr  mem       REG                8,4     10256   24120107 /usr/lib/libXcomposite.so.1.0.0
chromium- 14486     jinarr  mem       REG                8,4     39232   24120109 /usr/lib/libXcursor.so.1.0.2
chromium- 14486     jinarr  mem       REG                8,4     34984   24120135 /usr/lib/libXrandr.so.2.2.0
chromium- 14486     jinarr  mem       REG                8,4     63864   24120123 /usr/lib/libXi.so.6.1.0
chromium- 14486     jinarr  mem       REG                8,4     10496   24120125 /usr/lib/libXinerama.so.1.0.0
chromium- 14486     jinarr  mem       REG                8,4    186440   18350217 /lib/libpcre.so.3.12.1
chromium- 14486     jinarr  mem       REG                8,4    113072   24121108 /usr/lib/libxcb.so.1.1.0
chromium- 14486     jinarr  mem       REG                8,4   1572232   18353608 /lib/libc-2.11.1.so
chromium- 14486     jinarr  mem       REG                8,4     92552   18350103 /lib/libgcc_s.so.1
chromium- 14486     jinarr  mem       REG                8,4    534832   18350091 /lib/libm-2.11.1.so
chromium- 14486     jinarr  mem       REG                8,4   1044008   24117648 /usr/lib/libstdc++.so.6.0.13
chromium- 14486     jinarr  mem       REG                8,4     47048   18350257 /lib/libudev.so.0.6.1
chromium- 14486     jinarr  mem       REG                8,4    165960   18350152 /lib/libexpat.so.1.5.2
chromium- 14486     jinarr  mem       REG                8,4     70912   18350124 /lib/libbz2.so.1.0.4
chromium- 14486     jinarr  mem       REG                8,4    491000   18350161 /lib/libgcrypt.so.11.5.2
chromium- 14486     jinarr  mem       REG                8,4    309200   24120293 /usr/lib/libcups.so.2
chromium- 14486     jinarr  mem       REG                8,4    920968   24120182 /usr/lib/libasound.so.2.0.0
chromium- 14486     jinarr  mem       REG                8,4     22568   24120117 /usr/lib/libXfixes.so.3.1.0
chromium- 14486     jinarr  mem       REG                8,4    158736   18350229 /lib/libpng12.so.0.42.0
chromium- 14486     jinarr  mem       REG                8,4    256768   18350137 /lib/libdbus-1.so.3.4.0
chromium- 14486     jinarr  mem       REG                8,4    248088   24120419 /usr/lib/libgconf-2.so.4.1.5
chromium- 14486     jinarr  mem       REG                8,4     92752   18350274 /lib/libz.so.1.2.3.3
chromium- 14486     jinarr  mem       REG                8,4    135745   18353606 /lib/libpthread-2.11.1.so
chromium- 14486     jinarr  mem       REG                8,4    235368   24120811 /usr/lib/libnspr4.so
chromium- 14486     jinarr  mem       REG                8,4     18744   24120874 /usr/lib/libplc4.so
chromium- 14486     jinarr  mem       REG                8,4    181208   24120977 /usr/lib/libsmime3.so
chromium- 14486     jinarr  mem       REG                8,4    125904   24120821 /usr/lib/libnssutil3.so
chromium- 14486     jinarr  mem       REG                8,4   1271656   24120813 /usr/lib/libnss3.so
chromium- 14486     jinarr  mem       REG                8,4    216832   24120394 /usr/lib/libfontconfig.so.1.4.4
chromium- 14486     jinarr  mem       REG                8,4    547112   24120402 /usr/lib/libfreetype.so.6.3.22
chromium- 14486     jinarr  mem       REG                8,4    302536   24120843 /usr/lib/libpango-1.0.so.0.2800.0
chromium- 14486     jinarr  mem       REG                8,4    532792   24120235 /usr/lib/libcairo.so.2.10800.10
chromium- 14486     jinarr  mem       REG                8,4     52400   24120845 /usr/lib/libpangocairo-1.0.so.0.2800.0
chromium- 14486     jinarr  mem       REG                8,4    113648   24120442 /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
chromium- 14486     jinarr  mem       REG                8,4    707760   24120440 /usr/lib/libgdk-x11-2.0.so.0.2000.1
chromium- 14486     jinarr  mem       REG                8,4   4325736   24120597 /usr/lib/libgtk-x11-2.0.so.0.2000.1
chromium- 14486     jinarr  mem       REG                8,4    905480   18350163 /lib/libglib-2.0.so.0.2400.1
chromium- 14486     jinarr  mem       REG                8,4     18888   24120593 /usr/lib/libgthread-2.0.so.0.2400.1
chromium- 14486     jinarr  mem       REG                8,4    290184   24120509 /usr/lib/libgobject-2.0.so.0.2400.1
chromium- 14486     jinarr  mem       REG                8,4     14696   18353612 /lib/libdl-2.11.1.so
chromium- 14486     jinarr  mem       REG                8,4     31744   18353596 /lib/librt-2.11.1.so
chromium- 14486     jinarr  mem       REG                8,4     73600   24120115 /usr/lib/libXext.so.6.4.0
chromium- 14486     jinarr  mem       REG                8,4     14616   24120139 /usr/lib/libXss.so.1.0.0
chromium- 14486     jinarr  mem       REG                8,4     39400   24120137 /usr/lib/libXrender.so.1.3.0
chromium- 14486     jinarr  mem       REG                8,4   1269216   24120098 /usr/lib/libX11.so.6.3.0
chromium- 14486     jinarr  mem       REG                8,4    136936   18350166 /lib/ld-2.11.1.so
chromium- 14486     jinarr  mem       REG                8,4    275572    6291554 /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
chromium- 14486     jinarr  mem       REG                8,4    123097   25821209 /usr/lib/chromium-browser/locales/en-US.pak
chromium- 14486     jinarr  mem       REG                8,4    256324   24124880 /usr/lib/locale/en_US.utf8/LC_CTYPE
chromium- 14486     jinarr  mem       REG                8,4   1170770   24124769 /usr/lib/locale/en_US.utf8/LC_COLLATE
chromium- 14486     jinarr  mem       REG                8,4        54   24124775 /usr/lib/locale/en_US.utf8/LC_NUMERIC
chromium- 14486     jinarr  mem       REG                8,4      2454   24126623 /usr/lib/locale/en_US.utf8/LC_TIME
chromium- 14486     jinarr  mem       REG                8,4       286   24126624 /usr/lib/locale/en_US.utf8/LC_MONETARY
chromium- 14486     jinarr  mem       REG                8,4        57   24250853 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
chromium- 14486     jinarr  mem       REG                8,4        34   24124732 /usr/lib/locale/en_US.utf8/LC_PAPER
chromium- 14486     jinarr  mem       REG                8,4        77   24124752 /usr/lib/locale/en_US.utf8/LC_NAME
chromium- 14486     jinarr  mem       REG                8,4       155   24126625 /usr/lib/locale/en_US.utf8/LC_ADDRESS
chromium- 14486     jinarr  mem       REG                8,4        59   24126626 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
chromium- 14486     jinarr  mem       REG                8,4        23   24125058 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
chromium- 14486     jinarr  mem       REG                8,4     26048   24118999 /usr/lib/gconv/gconv-modules.cache
chromium- 14486     jinarr  mem       REG                8,4       373   24126627 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
chromium- 14486     jinarr    0r      CHR                1,3       0t0       1194 /dev/null
chromium- 14486     jinarr    1u      REG               0,21    169979   11534420 /home/jinarr/.xsession-errors
chromium- 14486     jinarr    2u      REG               0,21    169979   11534420 /home/jinarr/.xsession-errors
chromium- 14486     jinarr    3u     0000                0,9         0       1161 anon_inode
chromium- 14486     jinarr    4r      REG                8,4   3484478   25821213 /usr/lib/chromium-browser/chrome.pak
chromium- 14486     jinarr    5u     unix 0xffff880221f98c00       0t0      10974 socket
chromium- 14486     jinarr    6u     sock                0,6       0t0      11122 can't identify protocol
chromium- 14486     jinarr    7u     sock                0,6       0t0     114523 can't identify protocol
chromium- 14486     jinarr    8r      REG                8,4    123097   25821209 /usr/lib/chromium-browser/locales/en-US.pak
chromium- 14486     jinarr    9r      CHR                1,9       0t0       1199 /dev/urandom
chromium- 14486     jinarr   10u     unix 0xffff880235e64000       0t0     114477 socket
chromium- 14486     jinarr   11u     sock                0,6       0t0     114524 can't identify protocol
chromium- 14486     jinarr   12r     FIFO                0,8       0t0     114525 pipe
chromium- 14486     jinarr   13w     FIFO                0,8       0t0     114525 pipe
chromium- 14486     jinarr   14u     sock                0,6       0t0     114526 can't identify protocol
chromium- 14486     jinarr   15u     sock                0,6       0t0     114527 can't identify protocol
chromium- 14486     jinarr   16u      REG               0,16    524180      11937 /dev/shm/.org.chromium.Chromium.leI8in (deleted)
chromium- 14486     jinarr   17u      REG               0,16    292294     108597 /dev/shm/.org.chromium.Chromium.eDgMnB (deleted)
chromium- 14486     jinarr   18r      REG               0,21    441089   13238278 /home/jinarr/.config/chromium/Dictionaries/en-US-2-1.bdic
chromium- 14634     jinarr  cwd       DIR                0,3         0      11130 /proc/1998/fdinfo
chromium- 14634     jinarr  rtd       DIR                0,3         0      11130 /proc/1998/fdinfo
chromium- 14634     jinarr  txt       REG                8,4  69518720   25821214 /usr/lib/chromium-browser/chromium-browser
chromium- 14634     jinarr  mem       REG                8,4    123828    6291565 /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf
chromium- 14634     jinarr  mem       REG                8,4    126796    6291536 /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
chromium- 14634     jinarr  mem       REG                8,4    302688    6291528 /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf
chromium- 14634     jinarr  mem       REG                8,4    154264    6291568 /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf
chromium- 14634     jinarr  mem       REG                8,4    206132    6291551 /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf
chromium- 14634     jinarr  mem       REG                8,4    139640    6291570 /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
chromium- 14634     jinarr  mem       REG                8,4    330412    6291534 /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf
chromium- 14634     jinarr  mem       REG                8,4    136032    6291538 /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
chromium- 14634     jinarr  mem       REG                8,4    622280   25167250 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
chromium- 14634     jinarr  mem       REG                8,4    286620    6291552 /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
chromium- 14634     jinarr  mem       REG                8,4    275572    6291554 /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
chromium- 14634     jinarr  DEL       REG               0,16               108597 /dev/shm/.org.chromium.Chromium.eDgMnB
chromium- 14634     jinarr  DEL       REG               0,16                11937 /dev/shm/.org.chromium.Chromium.leI8in
chromium- 14634     jinarr  mem       REG                8,4    424384   24125131 /usr/lib/nss/libfreebl3.so
chromium- 14634     jinarr  mem       REG                8,4    577144   24121000 /usr/lib/libsqlite3.so.0.8.6
chromium- 14634     jinarr  mem       REG                8,4    266384   24125136 /usr/lib/nss/libsoftokn3.so
chromium- 14634     jinarr  mem       REG                8,4   1614016   25821207 /usr/lib/chromium-browser/libffmpegsumo.so
chromium- 14634     jinarr  mem       REG                8,4   3484478   25821213 /usr/lib/chromium-browser/chrome.pak
chromium- 14634     jinarr  mem       REG                8,4     67896   24121013 /usr/lib/libtasn1.so.3.1.7
chromium- 14634     jinarr  mem       REG                8,4     10224   18350172 /lib/libkeyutils-1.2.so
chromium- 14634     jinarr  mem       REG                8,4     31168   24120721 /usr/lib/libkrb5support.so.0.1
chromium- 14634     jinarr  mem       REG                8,4     14584   18350132 /lib/libcom_err.so.2.1
chromium- 14634     jinarr  mem       REG                8,4    154048   24120715 /usr/lib/libk5crypto.so.3.1
chromium- 14634     jinarr  mem       REG                8,4    803192   24120719 /usr/lib/libkrb5.so.3.3
chromium- 14634     jinarr  mem       REG                8,4    117592   18350241 /lib/libselinux.so.1
chromium- 14634     jinarr  mem       REG                8,4     93000   18353597 /lib/libresolv-2.11.1.so
chromium- 14634     jinarr  mem       REG                8,4     22560   24120113 /usr/lib/libXdmcp.so.6.0.0
chromium- 14634     jinarr  mem       REG                8,4     14488   24120102 /usr/lib/libXau.so.6.0.0
chromium- 14634     jinarr  mem       REG                8,4     14344   18350165 /lib/libgpg-error.so.0.4.0
chromium- 14634     jinarr  mem       REG                8,4     68480   24120194 /usr/lib/libavahi-client.so.3.2.5
chromium- 14634     jinarr  mem       REG                8,4     51608   24120196 /usr/lib/libavahi-common.so.3.5.1
chromium- 14634     jinarr  mem       REG                8,4    663816   24120507 /usr/lib/libgnutls.so.26.14.12
chromium- 14634     jinarr  mem       REG                8,4    213784   24120549 /usr/lib/libgssapi_krb5.so.2.2
chromium- 14634     jinarr  mem       REG                8,4    139528   24120313 /usr/lib/libdbus-glib-1.so.2.1.0
chromium- 14634     jinarr  mem       REG                8,4    450072   24120088 /usr/lib/libORBit-2.so.0.1.0
chromium- 14634     jinarr  mem       REG                8,4     14504   24120876 /usr/lib/libplds4.so
chromium- 14634     jinarr  mem       REG                8,4     34888   24121106 /usr/lib/libxcb-render.so.0.0.0
chromium- 14634     jinarr  mem       REG                8,4     14536   24121104 /usr/lib/libxcb-render-util.so.0.0.0
chromium- 14634     jinarr  mem       REG                8,4     98000   24120329 /usr/lib/libdirect-1.2.so.0.8.0
chromium- 14634     jinarr  mem       REG                8,4     39448   24120406 /usr/lib/libfusion-1.2.so.0.8.0
chromium- 14634     jinarr  mem       REG                8,4    533800   24120331 /usr/lib/libdirectfb-1.2.so.0.8.0
chromium- 14634     jinarr  mem       REG                8,4    362664   24120873 /usr/lib/libpixman-1.so.0.16.4
chromium- 14634     jinarr  mem       REG                8,4     14536   24120473 /usr/lib/libgmodule-2.0.so.0.2400.1
chromium- 14634     jinarr  mem       REG                8,4    172128   24120847 /usr/lib/libpangoft2-1.0.so.0.2800.0
chromium- 14634     jinarr  mem       REG                8,4    727136   24120455 /usr/lib/libgio-2.0.so.0.2400.1
chromium- 14634     jinarr  mem       REG                8,4    133912   24120188 /usr/lib/libatk-1.0.so.0.3009.1
chromium- 14634     jinarr  mem       REG                8,4     10272   24120111 /usr/lib/libXdamage.so.1.1.0
chromium- 14634     jinarr  mem       REG                8,4     10256   24120107 /usr/lib/libXcomposite.so.1.0.0
chromium- 14634     jinarr  mem       REG                8,4     39232   24120109 /usr/lib/libXcursor.so.1.0.2
chromium- 14634     jinarr  mem       REG                8,4     34984   24120135 /usr/lib/libXrandr.so.2.2.0
chromium- 14634     jinarr  mem       REG                8,4     63864   24120123 /usr/lib/libXi.so.6.1.0
chromium- 14634     jinarr  mem       REG                8,4     10496   24120125 /usr/lib/libXinerama.so.1.0.0
chromium- 14634     jinarr  mem       REG                8,4    186440   18350217 /lib/libpcre.so.3.12.1
chromium- 14634     jinarr  mem       REG                8,4    113072   24121108 /usr/lib/libxcb.so.1.1.0
chromium- 14634     jinarr  mem       REG                8,4   1572232   18353608 /lib/libc-2.11.1.so
chromium- 14634     jinarr  mem       REG                8,4     92552   18350103 /lib/libgcc_s.so.1
chromium- 14634     jinarr  mem       REG                8,4    534832   18350091 /lib/libm-2.11.1.so
chromium- 14634     jinarr  mem       REG                8,4   1044008   24117648 /usr/lib/libstdc++.so.6.0.13
chromium- 14634     jinarr  mem       REG                8,4     47048   18350257 /lib/libudev.so.0.6.1
chromium- 14634     jinarr  mem       REG                8,4    165960   18350152 /lib/libexpat.so.1.5.2
chromium- 14634     jinarr  mem       REG                8,4     70912   18350124 /lib/libbz2.so.1.0.4
chromium- 14634     jinarr  mem       REG                8,4    491000   18350161 /lib/libgcrypt.so.11.5.2
chromium- 14634     jinarr  mem       REG                8,4    309200   24120293 /usr/lib/libcups.so.2
chromium- 14634     jinarr  mem       REG                8,4    920968   24120182 /usr/lib/libasound.so.2.0.0
chromium- 14634     jinarr  mem       REG                8,4     22568   24120117 /usr/lib/libXfixes.so.3.1.0
chromium- 14634     jinarr  mem       REG                8,4    158736   18350229 /lib/libpng12.so.0.42.0
chromium- 14634     jinarr  mem       REG                8,4    256768   18350137 /lib/libdbus-1.so.3.4.0
chromium- 14634     jinarr  mem       REG                8,4    248088   24120419 /usr/lib/libgconf-2.so.4.1.5
chromium- 14634     jinarr  mem       REG                8,4     92752   18350274 /lib/libz.so.1.2.3.3
chromium- 14634     jinarr  mem       REG                8,4    135745   18353606 /lib/libpthread-2.11.1.so
chromium- 14634     jinarr  mem       REG                8,4    235368   24120811 /usr/lib/libnspr4.so
chromium- 14634     jinarr  mem       REG                8,4     18744   24120874 /usr/lib/libplc4.so
chromium- 14634     jinarr  mem       REG                8,4    181208   24120977 /usr/lib/libsmime3.so
chromium- 14634     jinarr  mem       REG                8,4    125904   24120821 /usr/lib/libnssutil3.so
chromium- 14634     jinarr  mem       REG                8,4   1271656   24120813 /usr/lib/libnss3.so
chromium- 14634     jinarr  mem       REG                8,4    216832   24120394 /usr/lib/libfontconfig.so.1.4.4
chromium- 14634     jinarr  mem       REG                8,4    547112   24120402 /usr/lib/libfreetype.so.6.3.22
chromium- 14634     jinarr  mem       REG                8,4    302536   24120843 /usr/lib/libpango-1.0.so.0.2800.0
chromium- 14634     jinarr  mem       REG                8,4    532792   24120235 /usr/lib/libcairo.so.2.10800.10
chromium- 14634     jinarr  mem       REG                8,4     52400   24120845 /usr/lib/libpangocairo-1.0.so.0.2800.0
chromium- 14634     jinarr  mem       REG                8,4    113648   24120442 /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
chromium- 14634     jinarr  mem       REG                8,4    707760   24120440 /usr/lib/libgdk-x11-2.0.so.0.2000.1
chromium- 14634     jinarr  mem       REG                8,4   4325736   24120597 /usr/lib/libgtk-x11-2.0.so.0.2000.1
chromium- 14634     jinarr  mem       REG                8,4    905480   18350163 /lib/libglib-2.0.so.0.2400.1
chromium- 14634     jinarr  mem       REG                8,4     18888   24120593 /usr/lib/libgthread-2.0.so.0.2400.1
chromium- 14634     jinarr  mem       REG                8,4    290184   24120509 /usr/lib/libgobject-2.0.so.0.2400.1
chromium- 14634     jinarr  mem       REG                8,4     14696   18353612 /lib/libdl-2.11.1.so
chromium- 14634     jinarr  mem       REG                8,4     31744   18353596 /lib/librt-2.11.1.so
chromium- 14634     jinarr  mem       REG                8,4     73600   24120115 /usr/lib/libXext.so.6.4.0
chromium- 14634     jinarr  mem       REG                8,4     14616   24120139 /usr/lib/libXss.so.1.0.0
chromium- 14634     jinarr  mem       REG                8,4     39400   24120137 /usr/lib/libXrender.so.1.3.0
chromium- 14634     jinarr  mem       REG                8,4   1269216   24120098 /usr/lib/libX11.so.6.3.0
chromium- 14634     jinarr  mem       REG                8,4    136936   18350166 /lib/ld-2.11.1.so
chromium- 14634     jinarr  mem       REG                8,4    123097   25821209 /usr/lib/chromium-browser/locales/en-US.pak
chromium- 14634     jinarr  mem       REG                8,4    256324   24124880 /usr/lib/locale/en_US.utf8/LC_CTYPE
chromium- 14634     jinarr  mem       REG                8,4   1170770   24124769 /usr/lib/locale/en_US.utf8/LC_COLLATE
chromium- 14634     jinarr  mem       REG                8,4        54   24124775 /usr/lib/locale/en_US.utf8/LC_NUMERIC
chromium- 14634     jinarr  mem       REG                8,4      2454   24126623 /usr/lib/locale/en_US.utf8/LC_TIME
chromium- 14634     jinarr  mem       REG                8,4       286   24126624 /usr/lib/locale/en_US.utf8/LC_MONETARY
chromium- 14634     jinarr  mem       REG                8,4        57   24250853 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
chromium- 14634     jinarr  mem       REG                8,4        34   24124732 /usr/lib/locale/en_US.utf8/LC_PAPER
chromium- 14634     jinarr  mem       REG                8,4        77   24124752 /usr/lib/locale/en_US.utf8/LC_NAME
chromium- 14634     jinarr  mem       REG                8,4       155   24126625 /usr/lib/locale/en_US.utf8/LC_ADDRESS
chromium- 14634     jinarr  mem       REG                8,4        59   24126626 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
chromium- 14634     jinarr  mem       REG                8,4        23   24125058 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
chromium- 14634     jinarr  mem       REG                8,4     26048   24118999 /usr/lib/gconv/gconv-modules.cache
chromium- 14634     jinarr  mem       REG                8,4       373   24126627 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
chromium- 14634     jinarr    0r      CHR                1,3       0t0       1194 /dev/null
chromium- 14634     jinarr    1u      REG               0,21    169979   11534420 /home/jinarr/.xsession-errors
chromium- 14634     jinarr    2u      REG               0,21    169979   11534420 /home/jinarr/.xsession-errors
chromium- 14634     jinarr    3u     0000                0,9         0       1161 anon_inode
chromium- 14634     jinarr    4r      REG                8,4   3484478   25821213 /usr/lib/chromium-browser/chrome.pak
chromium- 14634     jinarr    5u     unix 0xffff880221f98c00       0t0      10974 socket
chromium- 14634     jinarr    6u     sock                0,6       0t0      11122 can't identify protocol
chromium- 14634     jinarr    7u     sock                0,6       0t0     118003 can't identify protocol
chromium- 14634     jinarr    8r      REG                8,4    123097   25821209 /usr/lib/chromium-browser/locales/en-US.pak
chromium- 14634     jinarr    9r      CHR                1,9       0t0       1199 /dev/urandom
chromium- 14634     jinarr   10u     unix 0xffff8802368afc00       0t0     117960 socket
chromium- 14634     jinarr   11u     sock                0,6       0t0     118004 can't identify protocol
chromium- 14634     jinarr   12r     FIFO                0,8       0t0     118005 pipe
chromium- 14634     jinarr   13w     FIFO                0,8       0t0     118005 pipe
chromium- 14634     jinarr   14u     sock                0,6       0t0     118006 can't identify protocol
chromium- 14634     jinarr   15u     sock                0,6       0t0     118007 can't identify protocol
chromium- 14634     jinarr   16u      REG               0,16    524180      11937 /dev/shm/.org.chromium.Chromium.leI8in (deleted)
chromium- 14634     jinarr   17u      REG               0,16    292294     108597 /dev/shm/.org.chromium.Chromium.eDgMnB (deleted)
chromium- 14634     jinarr   18r      REG               0,21    441089   13238278 /home/jinarr/.config/chromium/Dictionaries/en-US-2-1.bdic
lsof      14667       root  cwd       DIR               0,21     81920   11534363 /home/jinarr/Desktop
lsof      14667       root  rtd       DIR                8,4      4096          2 /
lsof      14667       root  txt       REG                8,4    131312   24117962 /usr/bin/lsof
lsof      14667       root  mem       REG                8,4   1572232   18353608 /lib/libc-2.11.1.so
lsof      14667       root  mem       REG                8,4    136936   18350166 /lib/ld-2.11.1.so
lsof      14667       root  mem       REG                8,4    256324   24124880 /usr/lib/locale/en_US.utf8/LC_CTYPE
lsof      14667       root  mem       REG                8,4     26048   24118999 /usr/lib/gconv/gconv-modules.cache
lsof      14667       root    0u      CHR              136,0       0t0          3 /dev/pts/0
lsof      14667       root    1u      CHR              136,0       0t0          3 /dev/pts/0
lsof      14667       root    2u      CHR              136,0       0t0          3 /dev/pts/0
lsof      14667       root    3r      DIR                0,3         0          1 /proc
lsof      14667       root    4r      DIR                0,3         0     119984 /proc/14667/fd
lsof      14667       root    5w     FIFO                0,8       0t0     119989 pipe
lsof      14667       root    6r     FIFO                0,8       0t0     119990 pipe
lsof      14668       root  cwd       DIR               0,21     81920   11534363 /home/jinarr/Desktop
lsof      14668       root  rtd       DIR                8,4      4096          2 /
lsof      14668       root  txt       REG                8,4    131312   24117962 /usr/bin/lsof
lsof      14668       root  mem       REG                8,4   1572232   18353608 /lib/libc-2.11.1.so
lsof      14668       root  mem       REG                8,4    136936   18350166 /lib/ld-2.11.1.so
lsof      14668       root  mem       REG                8,4    256324   24124880 /usr/lib/locale/en_US.utf8/LC_CTYPE
lsof      14668       root  mem       REG                8,4     26048   24118999 /usr/lib/gconv/gconv-modules.cache
lsof      14668       root    4r     FIFO                0,8       0t0     119989 pipe
lsof      14668       root    7w     FIFO                0,8       0t0     119990 pipe
root@irr-irr:/home/jinarr/Desktop#

---

### Post by mrjahvi on 2012-07-13
root@irr-irr:/home/jinarr# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh 
DROP       icmp --  anywhere             anywhere            icmp address-mask-reply 
DROP       icmp --  anywhere             anywhere            icmp address-mask-request 
DROP       icmp --  anywhere             anywhere            icmp router-solicitation 
DROP       icmp --  anywhere             anywhere            icmp router-advertisement 
DROP       icmp --  anywhere             anywhere            icmp redirect 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            recent: CHECK seconds: 345600 name: portscan side: source 
DROP       icmp --  anywhere             anywhere            icmp any 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
DROP       tcp  --  anywhere             anywhere            tcp dpt:netbios-dgm 
DROP       tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
DROP       tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpt:netbios-ns 
DROP       udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
DROP       udp  --  anywhere             anywhere            udp dpt:netbios-ssn 
DROP       udp  --  anywhere             anywhere            udp dpt:microsoft-ds 
DROP       tcp  --  anywhere             anywhere            tcp dpt:loc-srv 
DROP       udp  --  anywhere             anywhere            udp dpt:loc-srv 
DROP       tcp  --  anywhere             anywhere            tcp dpt:635 
DROP       udp  --  anywhere             anywhere            udp dpt:635 
DROP       udp  --  anywhere             anywhere            udp dpts:33434:33523 
DROP       tcp  --  anywhere             anywhere            tcp flags:PSH,ACK/PSH 
DROP       tcp  --  anywhere             anywhere            tcp flags:ACK,URG/URG 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,RST/FIN,RST 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN 
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,PSH,URG 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,ACK,URG 
DROP       icmp -f  anywhere             anywhere            
DROP       icmp --  anywhere             anywhere            icmp timestamp-request 
DROP       igmp --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       icmp --  anywhere             anywhere            icmp echo-request 
DROP       all  --  anywhere             anywhere            recent: CHECK seconds: 345600 name: portscan side: source 
DROP       icmp --  anywhere             anywhere            icmp any 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
DROP       icmp --  anywhere             anywhere            icmp any 

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
root@irr-irr:/home/jinarr#

---

### Post by Cheesehead on 2012-07-13
Well, looks to me like you're not running sshd on port 22, and it looks like your firewall should DROP port 22 requests.

Is your system, by chance, behind a router that has port forwarding enabled?

---

### Post by wirelessmonkey on 2012-07-13
I agree with Cheesehead, this appears to be something on the wireless controller (read: router), not your machine.

---

### Post by mrjahvi on 2012-07-13
behind a router that has port forwarding enabled?....             my guess would yes. this is a public wifi, the other ones i go to it is not open. And deleted ssh in my setup on laptop.

---

### Post by Cheesehead on 2012-07-13
The test you showed us only reflects the upstream router. **It** has port 22 open, not your machine. You tested the upstream router.

For example, If you re-enabled sshd on port 23, opened port 23 in your firewall, and re-ran the test, it would erroneously show port 23 as closed. Since the upstream firewall has it closed, the scanner cannot reach your machine. Similarly, port 22 is open on the router...but that doesn't mean the port scanner can log in on that port or see any downstream machines through it unless that port is forwarded to your machine.

To get an accurate test of your machine, you need a direct connection, or a connection using a router that has DMZ'd your machine.

If you have another machine on the same local network, you can also use the nmap tool to do a port-scanning test.
Warning: Do NOT try a port scan without the approval of that network's owner! (If you did that on my network without prior approval, you would be immediately banned)

---

