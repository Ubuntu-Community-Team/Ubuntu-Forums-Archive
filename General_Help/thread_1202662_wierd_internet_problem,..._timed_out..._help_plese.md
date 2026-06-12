---
title: "wierd internet problem,... timed out... help plese"
date: 2009-07-02
forum: General Help
---

### Post by beanco on 2009-07-02
so, i am still on an older version of Ubuntu, i think it is feisty, but i cannot remember forsure..
 
anyway... i cannot access anythign o the Net.


i was downloading a torrent and using a browser with no issues, even got, sent a few emails in evolution... 

then evolution started timing out,,, then epiphany started timing out.... then i tried FF and Galeon, both timed out....

but ktorrent kept on working, very wierd... now I have down loaded everthing, and I cannot get anything on the Net to work....


the kids lap top works fine on the WiFi... but the ubuntu box is Netless.... kind of a pain..


any ideas????  any help?

thanks

robi

---

### Post by Boondoklife on 2009-07-02
post the output of `ifconfig`

---

### Post by beanco on 2009-07-03
well, i wil type in what i got for ifconfig



```
etho link encap:Ethernet HWddr 00:13:D4:E8:C7:61
 
inet addr:192.168.0.50  Bcast: 192.168.0.255 Mask:255.255.255.0

UP BROADCAST RUNNING BULTICAST MTU:1500 Metric:1

RX packets:27 errors:0 dropped:0 overruns:0 frame:0

TX packets:387 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueeulen:100

RX bytes:3231 (3.1 KiB) TX bytes:5388 (5.2 KiB)

Base address: 0xe800 Memory:fbfe0000-fc000000



lo Link encap:Local Loopback

inet addr:127.0.0.1 Mask:255.0.0.0

UP LOOPBACK RUNNING MTU: 16436 Metric:1

RX packets:2 errors:0 dropped:0 overruns:0 frame:0

TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0

RX bytes:100 (1000 b) TX bytes:100 (100.0b)
```



sorry if there are any typoes.... what should I be looking for from all this ?

thanks

robi

---

### Post by Boondoklife on 2009-07-03
Im gonna go with the assumption that your router is 192.168.0.1, try
```
ping 192.168.0.1
```

---

### Post by beanco on 2009-07-03
ok... i am a temrinal newbie so i typed what you suggested at the command line (if that is not the right place then where should I have tried?)

I have the following

64 bytes from 192.168.0.1: icmp_seq=308 ttl =64 time = 0.530 ms


this just keep going on and on....

i wonder if it will ever stop... not it is at seq 363....


robi

---

### Post by Boondoklife on 2009-07-03
ok well it can see your router which is good, now try to ping this ip: 74.125.45.100 . Also can you post the contents of your /etc/resolv.conf

---

### Post by beanco on 2009-07-03
i just tried and got email some how....

i will do what you suggest, out of curiousity, any idea what happened?

Robi

---

### Post by beanco on 2009-07-03
Ping got me this

64 bytes from 74.125.45.100: icmp_seq=8 ttl=52 time=137 ms

and here is the other one you asked for

rob@rob-desktop:~$ /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied


and I tried it from root to, just to see if it would give a different result...

robi

---

### Post by unutbu on 2009-07-03
Type 
```

cat /etc/resolv.conf
```
to see the contents of /etc/resolv.conf.

The ping results seem to suggest you have a working internet connection. Is Firefox working now?

---

### Post by beanco on 2009-07-03
epiphany is working FF is too



this is what I got with /etc./.....

search barczi.elte.hu
nameserver 194.149.0.157
nameserver 192.168.0.1

---

### Post by beanco on 2009-07-06
getting the problems again... well


i pinged and got the same as above.... 


any idea?


Thanks


Robi

---

### Post by unutbu on 2009-07-06
I'm not sure I know how to solve your problem, but it may help to post the output from the following commands. Run these commands at a time when your internet connection is not working (i.e. when you can ping, but other internet apps are not working):

```

cat /etc/resolv.conf
ping -c1 194.149.0.157
ping -c1 192.168.0.1
ping -c1 74.125.45.100
ping -c1 google.com
dig www.google.com
dig @192.168.0.1 www.google.com
dig @194.149.0.157 www.google.com

```

---

### Post by beanco on 2009-07-06
ok, when i get the time i will run them, and type in here the result for ech command....


man, I wish I could type faster.

thanks

robi

---

### Post by unutbu on 2009-07-06
Here is a tip: Select the text in the terminal with the mouse. Then to paste it into a web browser post, just middle-click the mouse. (If you have a two-button mouse, middle-click is achieved by clicking both buttons at the same time. If you have a three-button mouse, middle-click is simply pressing the middle button. If you have a wheel-mouse, middle-click is done by clicking the wheel.)

---

### Post by beanco on 2009-07-07
> **unutbu said:**
> I'm not sure I know how to solve your problem, but it may help to post the output from the following commands. Run these commands at a time when your internet connection is not working (i.e. when you can ping, but other internet apps are not working):

```

cat /etc/resolv.conf
ping -c1 194.149.0.157
ping -c1 192.168.0.1
ping -c1 74.125.45.100
ping -c1 google.com
dig www.google.com
dig @192.168.0.1 www.google.com
dig @194.149.0.157 www.google.com

```

 i got this in the order you listed:

cat /etc/resolv.conf

search barczi.elte.hu
nameserver 194.149.0.157
nameserver 192.168.0.1



ping -c1 194.149.0.157
ping: bad number of packets to transmit


ping -c1 192.168.0.1
ping: bad number of packets to transmit


ping -c1 74.125.45.100
ping: bad number of packets to transmit


ping: -cl google.com
ping: bad number of packets to transmit


rob@rob-desktop:~$ dig google.com 

; <<>> DiG 9.3.4-P1.1 <<>> google.com 
;; global options:  printcmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60935 
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0 

;; QUESTION SECTION: 
;google.com.                    IN      A 

;; ANSWER SECTION: 
google.com.             36      IN      A       74.125.127.100 
google.com.             36      IN      A       74.125.67.100 
google.com.             36      IN      A       74.125.45.100 

;; Query time: 12 msec 
;; SERVER: 194.149.0.157#53(194.149.0.157) 
;; WHEN: Tue Jul  7 14:36:15 2009 
;; MSG SIZE  rcvd: 76 

rob@rob-desktop:~$ dig [www.google.com](www.google.com) 

; <<>> DiG 9.3.4-P1.1 <<>> [www.google.com](www.google.com) 
;; global options:  printcmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44616 
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0 

;; QUESTION SECTION: 
;[www.google.com](www.google.com).                        IN      A 

;; ANSWER SECTION: 
[www.google.com](www.google.com).         604696  IN      CNAME   [www.l.google.com](www.l.google.com). 
[www.l.google.com](www.l.google.com).       74      IN      A       74.125.87.99 
[www.l.google.com](www.l.google.com).       74      IN      A       74.125.87.147 
[www.l.google.com](www.l.google.com).       74      IN      A       74.125.87.104 
[www.l.google.com](www.l.google.com).       74      IN      A       74.125.87.103 

;; Query time: 14 msec 
;; SERVER: 194.149.0.157#53(194.149.0.157) 
;; WHEN: Tue Jul  7 14:36:40 2009 
;; MSG SIZE  rcvd: 116 



rob@rob-desktop:~$ dig @192.168.0.1 [www.google.com](www.google.com) 

; <<>> DiG 9.3.4-P1.1 <<>> @192.168.0.1 [www.google.com](www.google.com) 
; (1 server found) 
;; global options:  printcmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39038 
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0 

;; QUESTION SECTION: 
;[www.google.com](www.google.com).                        IN      A 

;; ANSWER SECTION: 
[www.google.com](www.google.com).         604535  IN      CNAME   [www.l.google.com](www.l.google.com). 
[www.l.google.com](www.l.google.com).       214     IN      A       74.125.87.147 
[www.l.google.com](www.l.google.com).       214     IN      A       74.125.87.103 
[www.l.google.com](www.l.google.com).       214     IN      A       74.125.87.99 
[www.l.google.com](www.l.google.com).       214     IN      A       74.125.87.104 

;; Query time: 32 msec 
;; SERVER: 192.168.0.1#53(192.168.0.1) 
;; WHEN: Tue Jul  7 14:39:21 2009 
;; MSG SIZE  rcvd: 116 



rob@rob-desktop:~$ dig @194.149.0.157 [www.google.com](www.google.com) 

; <<>> DiG 9.3.4-P1.1 <<>> @194.149.0.157 [www.google.com](www.google.com) 
; (1 server found) 
;; global options:  printcmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24214 
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0 

;; QUESTION SECTION: 
;[www.google.com](www.google.com).                        IN      A 

;; ANSWER SECTION: 
[www.google.com](www.google.com).         604480  IN      CNAME   [www.l.google.com](www.l.google.com). 
[www.l.google.com](www.l.google.com).       159     IN      A       74.125.87.147 
[www.l.google.com](www.l.google.com).       159     IN      A       74.125.87.103 
[www.l.google.com](www.l.google.com).       159     IN      A       74.125.87.99 
[www.l.google.com](www.l.google.com).       159     IN      A       74.125.87.104 

;; Query time: 27 msec 
;; SERVER: 194.149.0.157#53(194.149.0.157) 
;; WHEN: Tue Jul  7 14:40:16 2009 
;; MSG SIZE  rcvd: 116 




i have no idea what all this means.... but thanks for the help



robi

---

### Post by beanco on 2009-07-08
it appears that I can use remote desktop .... 
this is strange.
i cannot get emails, or surf the net, keeps timing out on me...but I can use remote desktop to log onto my work place and do stuff from there and I am typing this from my kids' laptop on our wifi system... 

robi

---

### Post by unutbu on 2009-07-08
beanco, I think the output of the "dig" commands shows that your networking setup is working. The fact that certain apps work and other apps don't suggests that the problem is at the application level, not at the underlying (networking) system level.

If you have any proxy server running, perhaps try turning it off. 
A misconfigured proxy server might explain why the web browser is not working.
Perhaps go to System>Pref>Network Proxy and enable "Direct internet connection".

What program do you use to get emails?

---

### Post by beanco on 2009-07-08
currently i am using evolutin for email....

i will ty your idea of direct connect... could this have an adverse affect things?


robi

---

### Post by beanco on 2009-07-08
the direct internet connection radio button was alredy chosen...?

any other ideas?

what if I remove the apps that are not working adn then reinstall them?

robi

---

### Post by unutbu on 2009-07-08
Are you using a firewall? That could also explain your symptoms. You can check Ubuntu's firewall by typing (and posting)
```

sudo iptables -L
```

If you are using Ubuntu's default settings you will see
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    
```     

If you see this, then the firewall on Ubuntu is not the source of the problem. (Note that routers can also act as firewalls.) If you see something different, please post the output.

I assume your router's firewall is not the problem since mail and web surfing work from the laptop. It would not hurt to check the router's configuration however, just to make sure it isn't filtering web and email packets destined for the Ubuntu machine.

Regarding enabling "Direct network connection":
If you are using a proxy server for web surfing, this could explain why the browser is not working while some other internet apps are. By disabling the proxy server you'll be able to check if that is the source of the browser time-out problem.

If you want to use a proxy server, however, then you'll have to re-enable it (in System>Pref>Network Proxy) and configure it properly. Unfortunately, this is something I have zero knowledge about.

I also have zero knowledge about Evolution. :( If none of the above helps, perhaps it would be best to start a new thread describing the Evolution problem on its own. Specify if the problem involves sending mail or receiving mail or both. Point out that other internet apps like "remote desktop" do work, so people will know it is probably not a basic network configuration issue.

---

### Post by beanco on 2009-07-08
i got exactyl what you posted... so this is not a firewall issue...

i will try a new thread.

thanks for all the help.


robi

---

