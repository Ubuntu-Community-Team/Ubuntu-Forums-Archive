---
title: "Another Cisco VPN question."
date: 2006-06-17
forum: General Help
---

### Post by chajuram on 2006-06-17
Hi,

For the last few days I have been trying to get Cisco VPN to work on my computer running Dapper. I have seen a number of posts about Cisco VPN questions but none of the solutions seem to fit my problem. Here goes...

I have the required files to install Cisco 4.8 from my school. When I did sudo ./vpn_install the thing seemed to compile fine but for the following warning messages.

> /home/ritwik/Desktop/vpnclient/interceptor.c:310: warning: assignment from incom patible pointer type
/home/ritwik/Desktop/vpnclient/interceptor.c:334: warning: assignment from incom patible pointer type
/home/ritwik/Desktop/vpnclient/interceptor.c:335: warning: assignment from incom patible pointer type
/home/ritwik/Desktop/vpnclient/interceptor.c: In function &#8216;do_cleanup&#8217;:
/home/ritwik/Desktop/vpnclient/interceptor.c:378: warning: assignment from incom patible pointer type
  CC [M]  /home/ritwik/Desktop/vpnclient/linuxkernelapi.o
  LD [M]  /home/ritwik/Desktop/vpnclient/cisco_ipsec.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/ritwik/Desktop/vpnclient/.libdriver.so.cmd for /ho me/ritwik/Desktop/vpnclient/libdriver.so


After that I move my pcf file to the place it needs to be and run 

> sudo /etc/init.d/vpnclient_init start

And I get the error message

> Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.15-19-386/CiscoVPN/cisco_ipsec.ko': -1 Unknown symbol in module
Failed (insmod)

I have seen this message quoted a number of times in other posts but I am wondering if my error is due to the following...

My uname -r is "2.6.15-19-386" and the only linux-header file I could find are called 
[LIST]linux-headers-2.6.15-25-386[/LIST]
[LIST]linux-headers-2.6.15-23-386[/LIST] 

I have tried both, but neither work. I have an AMD Athlon so I also tried 
[LIST]linux-headers-2.6.15-25-k7[/LIST]
Which one should I use? 

Anyway, nothing helped me get rid of the error message. I tried looking for something like linux-headers-2.6.15-19-386, but could not find it anywhere. 

Sorry about the long post, I know you are all busy, I thank you for your time.

Ritwik.

PS. I tried vpnc, but am having some other problems there. If you are aware of a nice howto for vpnc, I will be happy to read it.

---

### Post by chajuram on 2006-06-18
Hi,

I had installed flight 6 of dapper and that was the reason for the older kernel. I did a dist-upgrade and have the lastest kernel, on which the Cisco VPN complies fine.

Ritwik.

---

### Post by freddo on 2006-06-18
Wich problems did you have with vpnc? Works fine for me and more people I know.

---

### Post by eentonig on 2006-06-18
I tried installing Cisco VPN client as well. Never got it working.

Then I slapped my head and told myself: "Why troubleshoot a closed source program, when the Open Source equivalent awaits me?".

Installed vpnc, took me a day to figure out I had to run it as root to have it actually set up the connection AND CHANGE THE ROUTING!!!!!!

Stupid me, I agree. Now I couldn't live without vpnc anymore. Whenever I need to troubleshoot vpns for clients, vpnc is the easiest and fastest way to test the vpns.

---

### Post by janformanek on 2006-06-21
Well I for instance seem to lose my connection to internet whenever i run vpnc, which makes the program kind of useless. I run it as root and when i ping [www.google.com](www.google.com) nothing happens.
Would be happy for some advice, I am a rookie so it's probably a rookie failure..
Thanks in advance :D

---

### Post by chajuram on 2006-06-22
[QUOTE=janformanek]Well I for instance seem to lose my connection to internet whenever i run vpnc, which makes the program kind of useless. I run it as root and when i ping [www.google.com](www.google.com) nothing happens.
Would be happy for some advice, I am a rookie so it's probably a rookie failure..
Thanks in advance :D[/QUOTE]

Hi Janformanek,

I am not sure if this is a good answer, but try restarting firefox after you start Cisco VPN. I had this problem sometimes, that the existing firefox did not work but closing firefox and restarting it worked.

Chajuram.

---

### Post by emnaki on 2006-06-29
I too have a problem when using vpnc. I seem to b able to initialize the connection just fine, and when I do a route -n it seems to be alright:

res78-124:/home/kchik/tt/src # route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.78.208.82   172.17.128.254  255.255.255.255 UGH   0      0        0 eth0
172.17.128.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0

but I can't seem to get any applications working with it, not even ping. Does anyone know what is wrong?

---

