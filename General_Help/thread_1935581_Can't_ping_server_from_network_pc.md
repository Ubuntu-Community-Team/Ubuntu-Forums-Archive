---
title: "Can't ping server from network pc"
date: 2012-03-04
forum: General Help
---

### Post by Hamguy38 on 2012-03-04
I am a newbie and am having a problem with a local network server. I have set up a server using Ubuntu Server 11.10. I have not put any content files on it yet because I am unable to connect to it via the network. When I am signed in on the server, I can ping my pc, the router and sites on the internet, I.E> Google.com, etc. 
When I put in my address 192.168.1.99 in my browser it says "IT WORKS but no content has been added yet!" I have installed Openssh and have it configured but when I try to log in using putty, I never get a sign on and after a short while, it times out. When I try to ping the server address, it times out everytime. So I am not able to talk to it. I am not sure where the problem lies. Is it a router problem or something set up incorrectly in the server. Any help would be greatful. Thanks in advance.

---

### Post by Roasted on 2012-03-04
Is there any way you can run ifconfig on the system and report back with the results? I'm doubtful it's the router, however it certainly could be. At first glance it sounds like a network setting.

About the router, what setup are you using? What router, ISP, etc. Even the littlest details may matter when troubleshooting. When I was running my ISP-provided modem/router for a while until my Netgear came in from NewEgg I noticed the router's firewall was on and blocked my ping capabilities... Just a thought.

---

### Post by Hamguy38 on 2012-03-04
Since I can't copy and paste the ifconfig output I have to type it out. Here is my ifconfig listing:
 
etho Link:encap: Ethernet HWaddr: 00:07:e9:a8:96:04
inet addr: 192.168.1.99 Bcast: 192.168.1.255 Madk: 255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:306 errors:0 dropped:0 overruns:0 frame:0
TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:35727 (35.7 KB) TX Bytes:2296 (2.2 KB)
 
 
lo Link encap: Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX Bytes:0 (0.0 B)
 
My Router is a Cisco E100, my ISP is a local company called speedyquick.net and I am receiving my service via an wireless connection to their transmitter. They provide the radio and it is connected to my router. My local network includes 5 pc's 2 pc's and the server are on ethernet and 2 laptops are on the wireless connection. The ip address of the server is a static IP. 
 
I guess I just don't understand why I can ping out of my server to my PC but I can't ping the server from the pc. I would think that if it was a router problem, I could not go either way. Just a thought rattling through by brain.

---

### Post by Hamguy38 on 2012-03-05
HELP WANTED!!!
 
I am still looking for a solution to my problem, Can anyone give me something to look for to resolve this problem.

---

### Post by Sergius14 on 2012-03-05
Do you have admin access to your Wi-Fi router?

Most AP has an option that is something like AP isolation, which makes an insolation between clients. In this case, you can connect to other network but can't comunicate with other clients in the same networking.

One way to kickly test this, is to cable laptop and server to the same router.

Have you installed or add something on IP tables?

---

### Post by Hamguy38 on 2012-03-05
> **Sergius14 said:**
> Do you have admin access to your Wi-Fi router?
 
Most AP has an option that is something like AP isolation, which makes an insolation between clients. In this case, you can connect to other network but can't comunicate with other clients in the same networking.
 
One way to kickly test this, is to cable laptop and server to the same router.
 
Have you installed or add something on IP tables?
 
Yes I have admin access to router and I am able to ping any other computer that is attached to the router not matter whether they are hard wired connections or via wireless connections. I can ping outside world also with no problem,
 
I am not sure what you are asking about the IP Tables, could you explain further please?

---

### Post by Sergius14 on 2012-03-06
Ok, so we can discard for the moment any router misconfiguration.

IPTables is the default Linux Firewall. If you don't know yet what it is, it is very likely that is not an issue...

Can you confirm this:

Ping from Server to PC is OK

Ping from PC to Server is not OK.

---

### Post by Hamguy38 on 2012-03-06
That was correct but I have decided to start installing my server from scratch and see if I have the same problem this time. Last time I automatical set up a LAMP server and I decided to retry and manually set it up and see what happens. I thank you for your help and I will close out this post for now. I hope everything goes alright this time.

---

### Post by drdos2006 on 2012-03-06
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

