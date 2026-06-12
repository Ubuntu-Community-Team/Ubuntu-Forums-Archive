---
title: "Remote SSH Connection Help!"
date: 2011-11-20
forum: General Help
---

### Post by robn30 on 2011-11-20
So I have got the local SSH connections down but the remote is not working.  I installed Ubuntu 11.10 on my dads machine and when I got back to my place I attempted to remote SSH into his machine.  I already did a local SSH session before leaving his place, ensuring I passed my public key over, and all was working perfectly.  In sshd_config I set password authentication to no and rsa authentication to yes.  Like I said the local SSH worked perfectly on his home network.  When I got home I attempted to connect using the terminal command ssh -C dad@his externally visible IP and I get no error but it just says connecting to the external IP, and just sits there.  Of course this is when the -v option is added so I can see what is going on.  Could it be his Router?  Even though it worked over the local connection?  I need to get this working as he often calls for assistance and is new to using Ubuntu.  Any help would be great.  Thanks.

---

### Post by San_SS! on 2011-11-20
The most probable thing is that, if he is in a LAN and his router is the Gateway to the internet. The router is doing NAT, to support many PCs in the internal network with only one public IP to go to the internet(the one given by the ISP).

If that's the case the router doesn't know to which of the internal PCs the incoming connection must go. For that you should **forward** port tcp/22 to your dad's internal IP. Then the router when receives a connection on port 22 of the outside will route it to your dad's pc.

---

### Post by robn30 on 2011-11-20
> **San_SS! said:**
> The most probable thing is that, if he is in a LAN and his router is the Gateway to the internet. The router is doing NAT, to support many PCs in the internal network with only one public IP to go to the internet(the one given by the ISP).

If that's the case the router doesn't know to which of the internal PCs the incoming connection must go. For that you should **forward** port tcp/22 to your dad's internal IP. Then the router when receives a connection on port 22 of the outside will route it to your dad's pc.

I am by no means a network guru, but I thought it might be something like that.  I was unsure since I was able to locally connect via SSH to his machine from mine.  I guess when you are both on the same network and connected to the same router then it works locally without issue.  When coming in from the outside it must be a different story.  Will pinging his external IP also come back with nothing?  Or can I ping an external IP no matter what?  Thanks.

---

### Post by Doug S on 2011-11-20
> Will pinging his external IP also come back with nothing? Or can I ping an external IP no matter what?
That also depends on the router settings. Many routers default to not reply to ICMP Echo requests (pings). Most routers can be set to reply to pings or not reply to pings.

---

### Post by tordeu on 2011-11-21
Your are right, when you are at his place and connect to the router, it is a totally different story. I suppose your router has either WLAN or multiple ports to PCs/notebooks to plug-in (or both) and in this case, the router really is more than just a router. It's a WLAN-Access Point, Switch and Router in one machine. When you connect internally, it probably looks something like this:

```

[FONT=Courier New]                  |----his pc
[/FONT][FONT=Courier New] internet----router
                  |----your notebook[/FONT]

```[FONT=Courier New]

[/FONT][FONT=Courier New][FONT=Arial]But as I said, the router basically consists of three different machines. If you would buy a "pure" router, a WLAN-Access Point and a Switch individually, you would connect them as follows:

[/FONT][/FONT]```
[FONT=Courier New]
                           |----his pc
internet----router----switch----WLAN-AP
                           |----your notebook[/FONT]

```[FONT=Courier New]
[/FONT]
or, if you would connect via WLAN and your father's PC via Ethernet:
```
[FONT=Courier New]
                           |----his pc
internet----router----switch
                           |----WLAN-AP~~~~~~~your notebook
[/FONT]
```In these cases, when you try to connect to his PC, will not go through the router, but only through the switch. (Or in your case the switch that is within your "router"). I don't want to go into too much detail, because it's unnecessary, but _basically_ connecting two devices with a switch or connecting them directly does not make a difference for things like ssh. This is completely different, however, when you put a router between two devices, like you would when connecting from outside:
```

[FONT=Courier New]your pc----(router)----internet----router----switch[/FONT][FONT=Courier New]----his pc[/FONT]

```[FONT=Courier New]
[FONT=Arial]The problem now is that your two PCs are not on the same network anymore, so you can't connect to his PC directly. Therefore, you are using the external IP address of the router to establish your SSH connection. The problem now is, how would the router know what to do with you SSH connection attempt? Because you are using the router's external IP address, it has to assume that you want to talk to itself. It does not know that the SSH connection was supposed to be for a computer on the "other side" (=the internal network).

So, that's why you need to log in to the administration interface of the router and forward the port 22 (or whichever port you are using, in case you don't use the standard port number) to your father's internal IP. This way, when you try to connect via SSH next time, the router will receive data for the port 22. Then, the router will see that everything on port 22 is supposed to be for your father's pc and only then will it send the data along to it.[/FONT][/FONT]

This problem is similar to sending mail to a company without specifying the name of the person who should receive the mail, but only writing on it "to mailbox 22". When the letter arrives there, the person who is supposed to take care of the mail won't know what to do with it, because it only has the name and address of of the company on it and the mailbox 22 is not assigned to anyone. Therefore, he does not know how to deliver the mail internally. This is the problem you are having now, where the router does not know that it should deliver the ssh stuff to a machine internally or to which one.
So, the solution in this case is to assign the mailbox 22 to your father, who is working in the company. This way, next time your send a letter to mailbox 22, the letter will get to the right person.

Ok, I don't know if that helps in anyway, but it probably does not hurt, either.

P.S.: Pinging your router will not necessarily work. Just try to forward port 22 at your father's place and see if it works correctly (which it should).

EDIT: I just noticed that my "diagrams" are not displayed correctly, because all spaces got removed. I tried to fix and it and it looks ok now, but noticed that the software does not work very well.

---

### Post by robn30 on 2011-11-21
> **tordeu said:**
> Your are right, when you are at his place and connect to the router, it is a totally different story. I suppose your router has either WLAN or multiple ports to PCs/notebooks to plug-in (or both) and in this case, the router really is more than just a router. It's a WLAN-Access Point, Switch and Router in one machine. When you connect internally, it probably looks something like this:
 
[FONT=Courier New]|----his pc[/FONT]
[FONT=Courier New]internet----router[/FONT]
[FONT=Courier New]|----your notebook[/FONT]
 
[FONT=Courier New][FONT=Arial]But as I said, the router basically consists of three different machines. If you would buy a "pure" router, a WLAN-Access Point and a Switch individually, you would connect them as follows:[/FONT]
 
[/FONT][FONT=Courier New]|----his pc[/FONT]
[FONT=Courier New]internet----router----switch----WLAN-AP[/FONT]
[FONT=Courier New]|----your notebook[/FONT]
 
or, if you would connect via WLAN and your father's PC via Ethernet:
[FONT=Courier New]
 
[/FONT][FONT=Courier New]|----his pc[/FONT]
[FONT=Courier New]internet----router----switch[/FONT]
[FONT=Courier New]|----WLAN-AP~~~~~~~your notebook[/FONT]
 
In these cases, when you try to connect to his PC, will not go through the router, but only through the switch. (Or in your case the switch that is within your "router"). I don't want to go into too much detail, because it's unnecessary, but _basically_ connecting two devices with a switch or connecting them directly does not make a difference for things like ssh. This is completely different, however, when you put a router between two devices, like you would when connecting from outside:
 
[FONT=Courier New]your pc----(router)----internet----router----switch[/FONT][FONT=Courier New]----his pc[/FONT]
 
[FONT=Courier New][FONT=Arial]The problem now is that your two PCs are not on the same network anymore, so you can't connect to his PC directly. Therefore, you are using the external IP address of the router to establish your SSH connection. The problem now is, how would the router know what to do with you SSH connection attempt? Because you are using the router's external IP address, it has to assume that you want to talk to itself. It does not know that the SSH connection was supposed to be for a computer on the "other side" (=the internal network).[/FONT]
 
[FONT=Courier New]So, that's why you need to log in to the administration interface of the router and forward the port 22 (or whichever port you are using, in case you don't use the standard port number) to your father's internal IP. This way, when you try to connect via SSH next time, the router will receive data for the port 22. Then, the router will see that everything on port 22 is supposed to be for your father's pc and only then will it send the data along to it.[/FONT][/FONT]
 
This problem is similar to sending mail to a company without specifying the name of the person who should receive the mail, but only writing on it "to mailbox 22". When the letter arrives there, the person who is supposed to take care of the mail won't know what to do with it, because it only has the name and address of of the company on it and the mailbox 22 is not assigned to anyone. Therefore, he does not know how to deliver the mail internally. This is the problem you are having now, where the router does not know that it should deliver the ssh stuff to a machine internally or to which one.
So, the solution in this case is to assign the mailbox 22 to your father, who is working in the company. This way, next time your send a letter to mailbox 22, the letter will get to the right person.
 
Ok, I don't know if that helps in anyway, but it probably does not hurt, either.
 
P.S.: Pinging your router will not necessarily work. Just try to forward port 22 at your father's place and see if it works correctly (which it should).
 
Awesome information!  I teach electronics for a living and your explanation was perfect.  I fully understood it and will make the changes in his router today and give it a shot.  Thank you for all the information, breaking it down the way you have helped me to understand exactly what is going on with the communication between the two networks.  I may know electronics extremely well but that is much different than networking.  Luckily my background helps me to understand things a little easier, especially when provided such detailed instructions as you have provided.  Many thanks, and I appreciate you taking the time to be so detailed, it is a big help to me, as I am still a novice with Ubuntu(Linux) and networking.  Thanks again.

---

### Post by tordeu on 2011-11-21
You are very welcome. I hope everything works out. 

P.S.: I just noticed that the site somehow ate the spaces in the diagrams. I tried to get them right to make it clearer and also to help future visitors (you never now).

---

### Post by Doug S on 2011-11-21
Yes, very nice description tordeu
For this to work properly and all the time, you will have to make sure that your father's computer always gets the same IP address. If there are multiple devices on his network and he is using DHCP to get his local IP assigned, he might not always get the same address.

---

### Post by robn30 on 2011-11-22
> **tordeu said:**
> You are very welcome. I hope everything works out. 
 
P.S.: I just noticed that the site somehow ate the spaces in the diagrams. I tried to get them right to make it clearer and also to help future visitors (you never now).
 
I tested the setup with port forwarding last night and it worked perfectly! I also refered to this site [http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Port_forwarding_through_SSH](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Port_forwarding_through_SSH) for the command line to tunnel a VNC connection for remote desktop usage.  It also worked flawlessly.  So I am now able to provide assistance when needed.
 
> **Doug S said:**
> Yes, very nice description tordeu
For this to work properly and all the time, you will have to make sure that your father's computer always gets the same IP address. If there are multiple devices on his network and he is using DHCP to get his local IP assigned, he might not always get the same address.
 
I have not setup a Static IP yet but will soon.  Luckily his machine is on continuous and the others are not, so it seems he keeps getting the same IP.  Nonetheless I will set Static IP anyway to aviod any issues in the future.  Of course his ISP may eventually change his externally visable address which I will then have to be supplied to make the connection work.

---

### Post by San_SS! on 2011-11-22
You can configure Static IP, or if your router allows it , you can set up the DHCP server to associate the MAC from your father's PC to an internal IP address. So each time your father's PC makes a DHCP request it will receive the same IP.

In that way your father's PC's configuration won't change, it will keep receiving gateway and DNS configuration through DHCP, making the network easier to mantain.

---

### Post by robn30 on 2011-11-22
> **San_SS! said:**
> You can configure Static IP, or if your router allows it , you can set up the DHCP server to associate the MAC from your father's PC to an internal IP address. So each time your father's PC makes a DHCP request it will receive the same IP.
 
In that way your father's PC's configuration won't change, it will keep receiving gateway and DNS configuration through DHCP, making the network easier to mantain.
 
So if one of the other devices comes online with a MAC different than his it will be assigned an IP other than the one reserved for him?  I will have to look into that.  Do you happen to know where that is located for Linksys routers?

---

### Post by San_SS! on 2011-11-22
Which model of Linksys do you have?

---

### Post by robn30 on 2011-11-30
> **San_SS! said:**
> Which model of Linksys do you have?
 
Not sure but I got it all working and it did have the DHCP Reservation setting which I used to reserve the IP for his MAC.  Everything is working perfectly now.  It has made things much easier using this remote desktop capability than using Windows Remote Assistance.

---

