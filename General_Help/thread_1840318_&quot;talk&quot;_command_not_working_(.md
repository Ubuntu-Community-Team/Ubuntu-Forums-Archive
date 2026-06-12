---
title: "&quot;talk&quot; command not working :("
date: 2011-09-07
forum: General Help
---

### Post by Neo_Lithic on 2011-09-07
Hello...

I installed 'talk' in my ubuntu 10.04 by doing

$sudo apt-get install inetutils-talk

All websites, forums etc. and the man page i saw, stated that
entering

$talk user@host

will enable my machine to connect with that machine
and be able to chat with the other user through terminal.
I tried the following things, but no use...

- $talk myfriend@f_host
- $talk myfriend@f_ipaddr
- $talkd
  $talk myfriend@f_host
  $talk myfriend@f_ipaddr

I dont have any idea about talk daemon..
I thought that the problem maybe with /etc/hosts but,
completely unaware of these things..

Can you please help me 'talk' with my friend using terminal?

Thanks in avance...

---

### Post by haqking on 2011-09-07
> **Neo_Lithic said:**
> Hello...

I installed 'talk' in my ubuntu 10.04 by doing

$sudo apt-get install inetutils-talk

All websites, forums etc. and the man page i saw, stated that
entering

$talk user@host

will enable my machine to connect with that machine
and be able to chat with the other user through terminal.
I tried the following things, but no use...

- $talk myfriend@f_host
- $talk myfriend@f_ipaddr
- $talkd
  $talk myfriend@f_host
  $talk myfriend@f_ipaddr

I dont have any idea about talk daemon..
I thought that the problem maybe with /etc/hosts but,
completely unaware of these things..

Can you please help me 'talk' with my friend using terminal?

Thanks in avance...


I take it your friend is logged into a system running the talk daemon and so are you ?

you cant just use it to talk anyone on the internet randomly you know that right ?

I say that cos a mate of mine was trying to do it to chat to me using my msn login email addrres and wondered why i wasnt chatting back...LOL

---

### Post by Neo_Lithic on 2011-09-07
Yes, Of course.. sorry, didnt mention it in the older post...

---

### Post by haqking on 2011-09-07
> **Neo_Lithic said:**
> Yes, Of course.. sorry, didnt mention it in the older post...
  read here, it may solve your issues and save me from typing and asking you lots of questions ;-)

[http://ubuntuforums.org/showthread.php?t=913525](http://ubuntuforums.org/showthread.php?t=913525)

---

### Post by Neo_Lithic on 2011-09-07
I refered it already... It wasnt helpful enough... :(

---

### Post by haqking on 2011-09-07
> **Neo_Lithic said:**
> I refered it already... It wasnt helpful enough... :(

ok so do and him have mesg y set


and you know his IP or username for system he is logged into ?

also other thread here [http://ubuntuforums.org/showthread.php?t=191896](http://ubuntuforums.org/showthread.php?t=191896)

i take it your daemon is running correct ?

---

### Post by Neo_Lithic on 2011-09-07
theres no file called '[B]xinetd.d/talk' in /etc/

[/B]and mesg is set to yes in both machine...

i know my friend's ip addr, and host name..

---

### Post by haqking on 2011-09-07
> **Neo_Lithic said:**
> theres no file called '[B]xinetd.d/talk' in /etc/

[/B]and mesg is set to yes in both machine...

i know my friend's ip addr, and host name..


ok so can you give us an idea how you are both setup.

is he running daemon locally ? or logged in via telnet to a given system.

is this just for fun or important (plenty of IM clients ;-)

and you are typing:

talk user@whatever

and you both have the ports open on your router or port forwarding and dont have firewalls blocking it ?

---

### Post by Neo_Lithic on 2011-09-08
> **haqking said:**
> ok so can you give us an idea how you are both setup.

is he running daemon locally ? or logged in via telnet to a given system.

is this just for fun or important (plenty of IM clients ;-)

and you are typing:

talk user@whatever

and you both have the ports open on your router or port forwarding and dont have firewalls blocking it ?

Sorry for late reply... ):P

First of all I don't know what a daemon or telnet is.. :-/ 
I read somewhere to run 'talkd' before 'talk'ing..
We did it and ran 'talk' addressing each other.. 
And this is not so important or urgent :)
We are trying to learn what the problem is, and 
why the procedure followed according to the man page fails in our machines.

And, can you please elaborate on opening port on router? 
I'm not well acquainted in using commands on network and its setup :(
How to check firewall blocks?

Thanks in advance...

---

### Post by Bodsda on 2011-09-08
> **Neo_Lithic said:**
> Hello...
 
I installed 'talk' in my ubuntu 10.04 by doing
 
$sudo apt-get install inetutils-talk
 
All websites, forums etc. and the man page i saw, stated that
entering
 
$talk user@host
 
will enable my machine to connect with that machine
and be able to chat with the other user through terminal.
I tried the following things, but no use...
 
- $talk myfriend@f_host
- $talk myfriend@f_ipaddr
- $talkd
$talk myfriend@f_host
$talk myfriend@f_ipaddr
 
I dont have any idea about talk daemon..
I thought that the problem maybe with /etc/hosts but,
completely unaware of these things..
 
Can you please help me 'talk' with my friend using terminal?
 
Thanks in avance...
 
When you say that you know his IP and hostname, is this a LAN connection (e.g: same network) or are you attempting to connect to his machine over the internet?
 
If it is over the internet, I would expect you would both have to configure some sort of port forwarding on your routers.
 
Bodsda

---

### Post by haqking on 2011-09-08
> **Bodsda said:**
> When you say that you know his IP and hostname, is this a LAN connection (e.g: same network) or are you attempting to connect to his machine over the internet?
 
If it is over the internet, I would expect you would both have to configure some sort of port forwarding on your routers.
 
Bodsda


yeah exactly, which is why i said above.

I think you need TCP and UDP ports 518 open on your router or firewall.

Depending on your router use the port forwarding section to set these up for your IP address.

Same to the remote Talk user.

---

### Post by Bodsda on 2011-09-08
> **haqking said:**
> yeah exactly, which is why i said above.
 
I think you need TCP and UDP ports 518 open on your router or firewall.
 
Depending on your router use the port forwarding section to set these up for your IP address.
 
Same to the remote Talk user.
 
In addition to the above, if you are using DHCP on your LAN, the port forward will break if you get leased a different IP next time. One workaround would be to use hostname as the portforward destination.
 
Bodsda

---

### Post by haqking on 2011-09-08
> **Bodsda said:**
> In addition to the above, if you are using DHCP on your LAN, the port forward will break if you get leased a different IP next time. One workaround would be to use hostname as the portforward destination.
 
Bodsda

+1

Ahh good point, or set statics or reservations on your router.

or alternatively use [Pidgin]("http://www.pidgin.im/") ;-) joke :lol:

---

### Post by Bodsda on 2011-09-08
> **haqking said:**
> +1
 
Ahh good point, or set statics or reservations on your router.
 
or alternatively use [Pidgin]("http://www.pidgin.im/") ;-) joke :lol:
 
irssi in a ##room would be a lot simpler than faffing with port forwarding :)

---

### Post by haqking on 2011-09-08
> **Bodsda said:**
> irssi in a ##room would be a lot simpler than faffing with port forwarding :)


ha indeed.  But weve all been there playing around trying to get something to work and not knowing why.

even with simpler alternatives sometimes it is just interesting to use something, especially archaic such as talk

---

### Post by Bodsda on 2011-09-08
> **haqking said:**
> ha indeed. But weve all been there playing around trying to get something to work and not knowing why.
 
even with simpler alternatives sometimes it is just interesting to use something, especially archaic such as talk
 
I actually did this recently. Spent 6 hours setting up and troubleshooting a hamachi VPN over the internet to allow me and my old man to play Dungeon Keeper 2 deathmatch :)... via Wine

---

### Post by Johnb0y on 2011-09-08
> **Bodsda said:**
> I actually did this recently. Spent 6 hours setting up and troubleshooting a hamachi VPN over the internet to allow me and my old man to play Dungeon Keeper 2 deathmatch :)... via Wine

:o:o:o:o:o

well done you! that sounds epic old school!

---

### Post by haqking on 2011-09-08
> **Bodsda said:**
> I actually did this recently. Spent 6 hours setting up and troubleshooting a hamachi VPN over the internet to allow me and my old man to play Dungeon Keeper 2 deathmatch :)... via Wine

ha nice one.

I was just thinking for the OP

what is the format of the talk command you are using ?

you are not sending it to his email address or LAN ip are you ? LOL

you need to send it to his WAN IP (the one on his router, which may change if he is not static)

and like i said previoulsy about the ports 518 being open, then the talk traffic directed at his WAN IP will forward to the talk daemon on his LAN IP

and vice versa for you

---

### Post by Neo_Lithic on 2011-09-08
> **Bodsda said:**
> When you say that you know his IP and hostname, is this a LAN connection (e.g: same network) or are you attempting to connect to his machine over the internet?
 
If it is over the internet, I would expect you would both have to configure some sort of port forwarding on your routers.
 
Bodsda

No.. We are not trying this in a LAN.

Can you help me in knowing how to configure port forwarding on our routers?
Please?... :confused:

Thanks in advance

---

### Post by Bodsda on 2011-09-08
> **Neo_Lithic said:**
> No.. We are not trying this in a LAN.
 
Can you help me in knowing how to configure port forwarding on our routers?
Please?... :confused:
 
Thanks in advance
 
Can you provide the manufacturer and model number of both routers
 
Thanks,
Bodsda

---

### Post by haqking on 2011-09-08
> **Neo_Lithic said:**
> No.. We are not trying this in a LAN.

Can you help me in knowing how to configure port forwarding on our routers?
Please?... :confused:

Thanks in advance


Depends on your router.

Like i said before, login to your router.

There should be a port forwarding section (depends on your router) then add the ports needed and forward them to your machine IP address.

Simple

Then use talk to talk to whatever his WAN IP is as i explained

see this thread [http://ubuntuforums.org/showthread.php?t=1839156](http://ubuntuforums.org/showthread.php?t=1839156) and post #5 from Dangertux who uploaded an example page from his router

---

### Post by Neo_Lithic on 2011-09-08
> **Bodsda said:**
> Can you provide the manufacturer and model number of both routers
 
Thanks,
Bodsda

Sorry.. I dont know all those stuff..
I have got a connection from BSNL(India)

It gave me the following details...

Board ID:                   96338L-2M-8M                                                   Software Version:                   3.08.02.UB.01.14_1357_100807                                                   Bootloader (CFE) Version:                   1.0.37-10.1                      Firmware Version:  UT300R2U.0011.01      Hardware Version:  UT300R2U 2.2      Model Name:  UT300R2U                                This information reflects the current status of your DSL connection.
            
                                             Line Rate - Upstream (Kbps):839Line Rate - Downstream (Kbps):1996                                   LAN IP Address:                   192.168.1.1                                                   Default Gateway:                   117.201.200.1                                                    Primary DNS Server:                   218.248.255.139                                                   Secondary DNS Server:                   218.248.255.141

---

### Post by Bodsda on 2011-09-08
> **Neo_Lithic said:**
> Sorry.. I dont know all those stuff..
I have got a connection from BSNL(India)
 
It gave me the following details...
 
Board ID: 96338L-2M-8M Software Version: 3.08.02.UB.01.14_1357_100807 Bootloader (CFE) Version: 1.0.37-10.1 Firmware Version: UT300R2U.0011.01 Hardware Version: UT300R2U 2.2 Model Name: UT300R2U This information reflects the current status of your DSL connection.
 
Line Rate - Upstream (Kbps):839Line Rate - Downstream (Kbps):1996 LAN IP Address: 192.168.1.1 Default Gateway: 117.201.200.1 Primary DNS Server: 218.248.255.139 Secondary DNS Server: 218.248.255.141
 
Use a browser to go to [http://192.168.1.1](http://192.168.1.1) and login. Then look on every page for a port forwarding option.
 
Bodsda

---

### Post by Neo_Lithic on 2011-09-08
> **Bodsda said:**
> Use a browser to go to [http://192.168.1.1](http://192.168.1.1) and login. Then look on every page for a port forwarding option.
 
Bodsda

I posted those data after logging into it..

I searched every section, but did not find anything like Port Forwarding :(

---

### Post by haqking on 2011-09-08
> **Neo_Lithic said:**
> I posted those data after logging into it..

I searched every section, but did not find anything like Port Forwarding :(


I am guessing you dont actually have a router per se, your ISP supplies you a modem i guess either USB or ethernet ?

You might not be able to configure this then ?

---

### Post by Neo_Lithic on 2011-09-08
> **haqking said:**
> Depends on your router.

Like i said before, login to your router.

There should be a port forwarding section (depends on your router) then add the ports needed and forward them to your machine IP address.

Simple

Then use talk to talk to whatever his WAN IP is as i explained

see this thread [http://ubuntuforums.org/showthread.php?t=1839156](http://ubuntuforums.org/showthread.php?t=1839156) and post #5 from Dangertux who uploaded an example page from his router

Thank you, Haqking...

Finding the port forward section is my current problem :( LOL :D
I saw the example page posted by DangerTux.. Could not find any matching
page in my DSL Router page..

@Haqking and @Bodsda
I found some post on Port Forwarding in BSNL(India) -
[http://jishnusdiary.blogspot.com/2008/01/port-forwarding-in-bsnl-dataone.html](http://jishnusdiary.blogspot.com/2008/01/port-forwarding-in-bsnl-dataone.html)

I don't know what I'm supposed to do.. :(

---

### Post by Neo_Lithic on 2011-09-08
> **haqking said:**
> I am guessing you dont actually have a router per se, your ISP supplies you a modem i guess either USB or ethernet ?

You might not be able to configure this then ?

Yeah, I'm supplied with a modem and an ethernet cable

---

### Post by haqking on 2011-09-08
> **Neo_Lithic said:**
> Thank you, Haqking...

Finding the port forward section is my current problem :( LOL :D
I saw the example page posted by DangerTux.. Could not find any matching
page in my DSL Router page..

@Haqking and @Bodsda
I found some post on Port Forwarding in BSNL(India) -
[http://jishnusdiary.blogspot.com/2008/01/port-forwarding-in-bsnl-dataone.html](http://jishnusdiary.blogspot.com/2008/01/port-forwarding-in-bsnl-dataone.html)

I don't know what I'm supposed to do.. :(


That link is for bittorrent, the same things apply but it will probably confuse you.

It needs to be done on your device, if you dont have a port forward option you might be stuck, what is the device you connect to the internet with ?

modem. router etc ? is it the device in that link ?


if it is then read the instruction it shows from 

6. Once logged in. Go to "Advanced set up->NAT
7. click "add" and then type some name say "talk" in custom server bar. (modify this to suit you as you not using it for torrent
8. Check your IP address of your computer. It will be 192.168.1.x, where x not equal to 1 if DHCP is configured.
9.in the port start and end column copy and paste the info about "current port" given in speed guide section (2).
10. Keep the same nos for both internal and external port start and end. Save it.
11.  Then go to "settings" section below "advanced setup" and do a "save/reboot"



you need to use port 518 to be forwarded to whatever your machine IP is

---

### Post by Bodsda on 2011-09-08
> **Neo_Lithic said:**
> Thank you, Haqking...
 
Finding the port forward section is my current problem :( LOL :D
I saw the example page posted by DangerTux.. Could not find any matching
page in my DSL Router page..
 
@Haqking and @Bodsda
I found some post on Port Forwarding in BSNL(India) -
[http://jishnusdiary.blogspot.com/2008/01/port-forwarding-in-bsnl-dataone.html](http://jishnusdiary.blogspot.com/2008/01/port-forwarding-in-bsnl-dataone.html)
 
I don't know what I'm supposed to do.. :(
 
Do you have this page? Go to "Advanced set up->NAT"

Bodsda

---

### Post by Neo_Lithic on 2011-09-08
Modem, with ethernet cable

---

### Post by Neo_Lithic on 2011-09-08
> **Bodsda said:**
> Do you have this page? Go to "Advanced set up->NAT"

Bodsda

Yeah... done

It displayed the following page :

**NAT -- DMZ Host**
            
            The DSL router will forward IP packets from the WAN that do not belong to any              of the applications configured in the Virtual Servers table to the DMZ host              computer.
            
            Enter the computer's IP address and click "Apply" to activate the DMZ host.
            
            Clear the IP address field and click "Apply" to deactivate the DMZ host.
            
                                               DMZ Host IP Address:                                                             __________

---

### Post by Bodsda on 2011-09-08
> **Neo_Lithic said:**
> Yeah... done
 
It displayed the following page :
 
**NAT -- DMZ Host**
 
The DSL router will forward IP packets from the WAN that do not belong to any of the applications configured in the Virtual Servers table to the DMZ host computer.
 
Enter the computer's IP address and click "Apply" to activate the DMZ host.
 
Clear the IP address field and click "Apply" to deactivate the DMZ host.
 
DMZ Host IP Address: __________
 
I'm not hot on security or networking, but I would say that would forward any external inbound traffic to that IP if you enter one. Which would be what we want.
 
@ haqking, what do you think?
 
Bodsda

---

### Post by haqking on 2011-09-08
> **Neo_Lithic said:**
> Yeah... done

It displayed the following page :

**NAT -- DMZ Host**
            
            The DSL router will forward IP packets from the WAN that do not belong to any              of the applications configured in the Virtual Servers table to the DMZ host              computer.
            
            Enter the computer's IP address and click "Apply" to activate the DMZ host.
            
            Clear the IP address field and click "Apply" to deactivate the DMZ host.
            
                                               DMZ Host IP Address:                                                             __________

> **Bodsda said:**
> I'm not hot on security or networking, but I would say that would forward any external inbound traffic to that IP if you enter one. Which would be what we want.
 
@ haqking, what do you think?
 
Bodsda

mmm yeah or configure a virtual server for your application talk, did you follow the steps from my post #28

---

### Post by Neo_Lithic on 2011-09-08
> **Bodsda said:**
>  but I would say that would forward any external inbound traffic to that IP if you enter one. Which would be what we want.
 
Bodsda

> **haqking said:**
> mmm yeah or configure a virtual server for your application talk, did you follow the steps from my post #28

I don't know how to proceed, in both of your suggestions :P
Is it possible to set up a virtual server for an application?

---

### Post by haqking on 2011-09-08
> **Neo_Lithic said:**
> I don't know how to proceed, in both of your suggestions :P
Is it possible to set up a virtual server for an application?


in my suggestion on post 28 i gave the steps which are from your link.

did you do that and enter port 518 ?

---

### Post by Neo_Lithic on 2011-09-08
> **haqking said:**
> That link is for bittorrent, the same things apply but it will probably confuse you.

It needs to be done on your device, if you dont have a port forward option you might be stuck, what is the device you connect to the internet with ?

modem. router etc ? is it the device in that link ?


if it is then read the instruction it shows from 

6. Once logged in. Go to "Advanced set up->NAT
7. click "add" and then type some name say "talk" in custom server bar. (modify this to suit you as you not using it for torrent
8. Check your IP address of your computer. It will be 192.168.1.x, where x not equal to 1 if DHCP is configured.
9.in the port start and end column copy and paste the info about "current port" given in speed guide section (2).
10. Keep the same nos for both internal and external port start and end. Save it.
11.  Then go to "settings" section below "advanced setup" and do a "save/reboot"



you need to use port 518 to be forwarded to whatever your machine IP is

According to step named 7., I have to click 'add', but theres no option to add anything here.. theres just a box to enter this:

DMZ Host IP Address:                   ________

How to use port 518?

---

### Post by haqking on 2011-09-08
> **Neo_Lithic said:**
> According to step named 7., I have to click 'add', but theres no option to add anything here.. theres just a box to enter this:

DMZ Host IP Address:                   ________

How to use port 518?


mmmm well i dont know then ;-)

can you post a few screen dumps of your router interface just for clarity ?

cheers

---

### Post by Neo_Lithic on 2011-09-08
> **haqking said:**
> mmmm well i dont know then ;-)

can you post a few screen dumps of your router interface just for clarity ?

cheers

I guess this might help you...

Its late night here.. I'm feeling sleepy :) . If you dont mind, I'll reply tomorrow?

Thank you for your help :)
Good night :)

---

### Post by haqking on 2011-09-08
> **Neo_Lithic said:**
> I guess this might help you...

Its late night here.. I'm feeling sleepy :) . If you dont mind, I'll reply tomorrow?

Thank you for your help :)
Good night :)


ok so on your app filtering and incoming (possibly also your outgoing) IP filtering page you need to set things up.

app filtering = create a new one and call it talk if you can and use the port 518 and let me know what others options it gives you

ip filtering = again your lan IP and port 518 to be forwarded to it.

cant give you step by step as i can see all options after some options are added.

time for you to play ;-)

make sure you have a backup of your device though.

good luck

---

### Post by Neo_Lithic on 2011-09-08
> **haqking said:**
> ok so on your app filtering and incoming (possibly also your outgoing) IP filtering page you need to set things up.

app filtering = create a new one and call it talk if you can and use the port 518 and let me know what others options it gives you

ip filtering = again your lan IP and port 518 to be forwarded to it.

cant give you step by step as i can see all options after some options are added.

time for you to play ;-)

make sure you have a backup of your device though.

good luck

I tried doing things as you mentioned..
I was able to add filters only for incoming and outgoing (router9.png, router10.png)
But, I had no option to add anything other than the items listed in the drop down menu in App Filtering... (router5.png)

Can you please tell me what I entered was right?(in *.png)

Thanks :)

---

### Post by haqking on 2011-09-10
> **Neo_Lithic said:**
> I tried doing things as you mentioned..
I was able to add filters only for incoming and outgoing (router9.png, router10.png)
But, I had no option to add anything other than the items listed in the drop down menu in App Filtering... (router5.png)

Can you please tell me what I entered was right?(in *.png)

Thanks :)

The IP addresses you are using are local (private) addresses for your lan.  You need to allow his WAN ip address to come in on the given port and forwarded to your LAN IP.

The same his end for his configuration also.

I cant tell you what his WAN IP his, he will need to do that.

---

