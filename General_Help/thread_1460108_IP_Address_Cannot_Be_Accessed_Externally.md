---
title: "IP Address Cannot Be Accessed Externally"
date: 2010-04-22
forum: General Help
---

### Post by ajwei810192 on 2010-04-22
Hi, 
 
I hope I am in the right section to ask this question. I have finished something simple and would like some people to test it, and when I gave my url of my website that sits on my computer to someone, the response was that she kept getting messages saying that connection has been reset. She tried for a couple of times and could not see my website, which the address is accurate. 
 
Are there specific things I need to do to allow users to see my site? Yet, why does she not get messages saying that "failed to access" or something like that?

---

### Post by Portmanteaufu on 2010-04-22
Could you tell us a little bit about the server hosting the site? If it's a box in your living room, it's very likely that your ISP blocks port 80 (the normal web traffic port) to keep people from running sites out of their residence. There are workarounds for that, but I'd like to confirm that that's the problem before diving in.

Is your computer (which is able to get to the site) on the same network as the server? Are they both behind a router?

---

### Post by _0R10N on 2010-04-22
Wich webserver are you using? Are you behind a router? if that's the case, you'll have to enable port forwarding in your router for the given port.

Kind regards!

_0R10N >>

---

### Post by ajwei810192 on 2010-04-22
My router is sitting a yard away from me behind the wall, by the way. I believe that the web ip address I am using is within the range of the netmask and the gateway on my router. 
 
Of course, while I would like to do this, I am hoping that my machine would not get hacked, despite the fact I do know Linux is relatively safer. 
 
By the way, I use a laptop, and it is the same machine as where my website sits that I use to be connected to the internet. 
 
Am I making sense here?

---

### Post by Portmanteaufu on 2010-04-22
Alright, if I'm understanding you properly:

- You have a computer in your house that hosts a website. 
- You are able to get to that website from computers within your house.
- You are not able to get to that website from computers outside your house.

What you'll need to do now is:
- Find out what your router's IP address is. You can get this by going to ipchicken.com. I'm going to call your IP address "$ADDR".
- Pick a port that you want to be in your web address. It should be a number above, say, 2000. I will call your port number "$PORT".
- Go to [portforward.com/]("http://portforward.com/") and follow the directions to figure out how to forward external port $PORT to internal port 80 on the internal IP address of your webserver.
- Tell your friend to go to http://$ADDR:$PORT (e.g. [http://123.456.78.910:4545](http://123.456.78.910:4545)). If your port forwarding is set up correctly, they should be able to see it.

---

### Post by _0R10N on 2010-04-22
That's right!! It's most likely that your friend is trying to access the site using the IP address of the server within your LAN but, remember, he/she is not in your LAN, thus you have to give him/her your WAN address. So, you have to do 2 things:

1- Like Portmanteaufu said, you should know your external IP address, asking that information to the site mentioned or others like whatismyipaddress.com. The address provided will be the IP of your access (the router a yard away). So you have to...

2- Tell the router that incoming request to port $PORT must be forwarded to the machine with the ip of the server (LAN address). This is accomplished configuring the router, details depend on the router model.

Kind regards!

_0R10N >>

---

### Post by _0R10N on 2010-04-22
You can also create an account in no-ip and configure your router, so your friends can access the site via an stardard url like mycoolsite.com.:popcorn:

_0R10N >>

---

### Post by LurkyLou on 2010-04-22
What kind of router are you using (name brand, model#)?  Many routers have online emulators, so us forum members could "see" how your router is set up and maybe offer more detailed help.

---

### Post by ajwei810192 on 2010-04-22
Thanks to [Portmanteaufu]("http://ubuntuforums.org/member.php?u=631265")'s clear instructions. I have done the port forwarding, checked my router, which is [http://portforward.com/english/routers/port_forwarding/2wire/3800HGV-B/default.htm](http://portforward.com/english/routers/port_forwarding/2wire/3800HGV-B/default.htm). However, I still miss one thing. 

I did go to chicken.com like you suggested, and this is the result: 99.48.66.63, and yet I have set my static ip to 192.168.1.125. Which address should my friend use? BTW, my forwarded port number is 12, since all the numbers I tried over 75 gets me this nasty error saying that it is out of range.

---

### Post by _0R10N on 2010-04-22
99.48.66.63 is your external IP address: This is the IP address by wich you're known in the Internet.
192.168.1.125 is you internal (or local) IP address: PCs on your home network knows your system by this address.

Assuming your friend isn't in your home, he/she must be provided with the first one.

There's two different address because their purpose are quite different. One address is used to distinguish your PC from the rest, in the whole world. But, like you have a router that address identifies the router.

Now, imagine there's more than one system in your home, there must to be a reliable way to distinguish a PC from the other, so a second address is needed. This address is used to mount networks in offices, etc...

I don't want to make it more complicated so, if you need more details, let us know.

Kind regards!

_0R10N >>

---

### Post by 3rdalbum on 2010-04-23
> **ajwei810192 said:**
> Thanks to [Portmanteaufu]("http://ubuntuforums.org/member.php?u=631265")'s clear instructions. I have done the port forwarding, checked my router, which is [http://portforward.com/english/routers/port_forwarding/2wire/3800HGV-B/default.htm](http://portforward.com/english/routers/port_forwarding/2wire/3800HGV-B/default.htm). However, I still miss one thing. 

I did go to chicken.com like you suggested, and this is the result: 99.48.66.63, and yet I have set my static ip to 192.168.1.125. Which address should my friend use? BTW, my forwarded port number is 12, since all the numbers I tried over 75 gets me this nasty error saying that it is out of range.

Have your friend go to [http://99.48.66.63](http://99.48.66.63), and tell your router to forward port 80 to 192.168.1.125.

It should let you forward Port 80 (default web port); if it doesn't, then you'll have to edit Apache's configuration file to make it run on port 75. I don't think you can make it run on port 12.

---

### Post by ajwei810192 on 2010-04-23
3rdalbum and _0R10N,

 I think I have forwarded 12 to 80, and not the other way round, and again I may be wrong. BTW, did I mention that the Ubuntu that I am running is on the virtual box? I have set that to the static address of 192.168.1.125, which I am assuming when I am setting that up, I am supposed to set it up with my internal and not my external address. 

  _0R10N, you mentioned about the second address, is that the port number?  I have attached the screen shot of my settings here. There is something that is weird is that I am certain when I entered the information in my settings through my router, I entered it 192.168.1.125, which was what I set as the "static IP", then how come on my Firewall settings, it tells me 192.168.1.64? Have I set it to the wrong machine? I don't want this to be set to my main system on my PC, but my virtual box. 

Am I getting confusing here?
Thanks for your help.

---

### Post by _0R10N on 2010-04-23
> **ajwei810192 said:**
> 3rdalbum and _0R10N,

 I think I have forwarded 12 to 80, and not the other way round, and again I may be wrong. BTW, did I mention that the Ubuntu that I am running is on the virtual box? I have set that to the static address of 192.168.1.125, which I am assuming when I am setting that up, I am supposed to set it up with my internal and not my external address. 

  _0R10N, you mentioned about the second address, is that the port number?  I have attached the screen shot of my settings here. There is something that is weird is that I am certain when I entered the information in my settings through my router, I entered it 192.168.1.125, which was what I set as the "static IP", then how come on my Firewall settings, it tells me 192.168.1.64? Have I set it to the wrong machine? I don't want this to be set to my main system on my PC, but my virtual box. 

Am I getting confusing here?
Thanks for your help.

I meant your public IP address..

Your friend should type in his/her url something like this: 
```
http://your-public-IP-address:port/mypage.html
```

This is what happens: everytime a system connects to the internet is assigned an public IP address. That address is used for other systems to know about that system.

Since it's your router who is connected to internet, the public IP address you mentioned identifies the router, and not your PC.

So, how do you system connects to the internet? Well, the router keeps track of all the PCs/laptops connected in your home, and it has assigned a second address to every one of them, so it can communicate with them. So the router communicates with the Internet via the public IP address, the Matrix provided; and talk to its local PCs via local IP addresses of each PC.

In short, what happens when your friend attempts to access your page? Wel, he/she needs to know:

a- Your public IP addrees.
b- The port where the server of your page is listening
c- The specific page name (/mypage.html)

We can resume the process as follows.

Your friend types in the data mentioned in a,b,c. and hits enter.

Then, the public IP address is utilized to know where to go. Then the request comes to your home. woh!! there's a router. Well, a port number was proportionate as part of the url. So the router needs to know that incoming request for a given port must be forwarded to an specific system in your home network. That little step is accomplished by setting in your router a rule saying "forward request to port XXX to the ip 192.... (your pc). Then your server is told to serve the file mypage.html

Hope this helps!

Kind regards!

_0R10N >>

---

### Post by ajwei810192 on 2010-04-23
So, am I supposed to talk to my ISP and have them assign me a static ip address so I could use? I am wondering if I have done anything wrong in my configuration on my router. It is in my previous in the attached image. 

Second, am I supposed to hook up the static ip from my internal or external to my /etc/networking/interface file?

I told my friend to try it this morning with the public address, which is [http://99.48.66.43:12:12/myfiles/&#8207;mypage.html](http://99.48.66.43:12:12/myfiles/&#8207;mypage.html), and her response is that she still cannot see it with that public address. She has kindly given me the error, and I hope this would help someone who sees this thread to figure out what else I need to do. 

Failed to Connect
Firefox can't establish a connection to the server at 99.48.66.43:12.

Though the site seems valid, the browser was unable to establish a connection.
 
    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's 
network connection.
    * Is your computer or network protected by a firewall or proxy? 
Incorrect settings can interfere with Web browsing.
 [FONT=Verdana]
Thanks for your help[/FONT]

---

### Post by _0R10N on 2010-04-23
Your ISP won't give you an Static External IP address. So, you have 2 choices.

1- Notify your friends whenever your external IP address changes.
2- Create an account in No-IP. So you'll have a domain name like [www.mycoolsite.com](www.mycoolsite.com). This option requires some basic configuration in your router, but is the best one.

I can't see much on the screenshot you uploaded, but nothing seems to be wrong. Your friends could try to ping that IP address. If they got a response, then we'll have to review your router configuration, step by step.

_0R10N >>

---

### Post by ajwei810192 on 2010-04-23
_0R10N,
 
  Based on what you mentioned in the previous post, looks like you or someone you know use this. I have just set up my account, and I wonder if the below snippet meant anything to you. 
[COLOR=#000000][FONT=Verdana][B]
Quick Tip:[/B] Many ISPS block port 80(http) and 25(smtp).  You'll need [No-IP Enhanced]("http://www.no-ip.com/services/managed_dns/enhanced_dynamic_dns.html?utm_source=welcome1&utm_medium=email&utm_campaign=newuser1&utm_content=quicktip") to get around blocked port 80 and [No-IP Mail Reflector]("http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html?utm_source=welcome1&utm_content=quicktip&utm_medium=email&utm_campaign=newuser1") to get around Port 25

Do I have to do anything about this? Since I am only running this on my own machine, would you recommend this?

Thanks for your help.
[/FONT][/COLOR]

---

### Post by Portmanteaufu on 2010-04-23
Sorry, I fell behind on this thread. I wanted to mention really quickly, though, that all ports beneath 1024 are usually reserved by the system for other uses. I don't know if it's the same case with routers, but since a lot of routers run Linux firmware I wouldn't be surprised.

Since you can't use port 80 because your ISP likely blocks it, I would set the external port number to be something comfortably higher than 1024. Maybe change "12" to "1212"?

---

### Post by Portmanteaufu on 2010-04-23
> **_0R10N said:**
> Your ISP won't give you an Static External IP address.

At least not for free! If you're lucky, this might cost you 15 bucks a month. Of course, since you can get web hosting for far less than that, it would probably make more sense to just get server space if you're going to pay for it.

To help you debug this problem, you might try firing up telnet:

```
telnet [ip or hostname] [port]
```

Point it towards your external IP address and the external port and see what message you get. If it's "Connection refused", you'll know your router isn't properly configured. If it's something more cryptic that looks like it came from Apache (or whatever web server you're using), then your router is good to go -- you just have to tweak your webserver.

If it's something else altogether, post it and we might be able to decipher it. :D

---

### Post by ajwei810192 on 2010-04-24
Portmanteaufu,

So you do find it a problem that I am using port 12? Is that my remote port? For some reasons, when I get a higher number, it tells me that I am doing this out of range. So, I am not sure what that means. 

I did try doing what you suggested here by going to the terminal and telnet to my external ip address from my local machine. I didn't get that message you suggested, and instead I get,  

telnet: Unable to connect to remote host: Connection timed out

I don't think this is significant,. since there is no error message that was displayed on why it took so long. 

Thank for your help.

---

### Post by Aped on 2010-04-24
Funny that you chose 12. I'm pretty sure it's actually like the only port that DOESN'T have a standard service running on it. 

Timedout connection means it's not even getting to your router, so either it's the wrong IP, your router isn't set to respond to incoming traffic (possible), or it got forwarded properly and your destination computer didn't respond to the query. 

Bluehost.com is what you need, spend the $4/month and get literally everything you could want out of a basic provider.

---

### Post by Portmanteaufu on 2010-04-24
> **ajwei810192 said:**
> Portmanteaufu,

So you don't find it a problem that I am using port 12? Is that my remote port? For some reasons, when I get a higher number, it tells me that I am doing this out of range. So, I am not sure what that means. 

I did try doing what you suggested here by going to the terminal and telnet to my external ip address from my local machine. I didn't get that message you suggested, and instead I get,  

telnet: Unable to connect to remote host: Connection timed out

I don't think this is significant,. since there is no error message that was displayed on why it took so long. 

Thank for your help.

Actually, I was trying to suggest that port 12 could be a problem. Sorry if I was unclear. On a lot of systems, a huge number of the ports less than 1024 are reserved for things like web traffic, e-mail traffic, telnet traffic and other specific uses. As a result, when picking a port to use, it's usually recommended that you pick a number higher than 1024 just to be sure you're not stepping on some other service's toes.

As Aped mentioned, the "connection timed out" message means that the computer on the other end isn't being reached. Can you double-check the external IP address you're using?

---

### Post by ajwei810192 on 2010-04-24
I have just read that a lot of residential servers are blocked on port 80, so do I need to change it to 8080 instead of 80 on my apache server?

This is what I have on my 2wire configuration:

Firewall Status: Active
Device: 192.168.1.64 
Type Protocol: TCP
Port: 12-80
Public IP: 99.68.66.43 

Have I done anything wrong here? I am not sure if it is 12 to 80 or 12 from 80 in this circumstance. 

I cannot even ping myself to the external ip even when I am at my own machine, even though I can use the internal address to access the site. Just out of curiosity, if my ISP changes the address periodically, how would it know when to change the public IP to use?

---

### Post by ajwei810192 on 2010-04-24
Just out of curiosity, if I set up the ServerName in my httpd.conf file, 
ServerName mysite888888.org

would my users be able to use something like 

[http://mysite888888.org](http://mysite888888.org) to access my website so that it would prevent the interchangeable ip address?

Thanks for your help.

---

### Post by _0R10N on 2010-04-24
Nop, it won't work... think what happens if many people set that value to google.com... if you don't want to use the IP address, you must register a domain name somewhere,  you can't just assign it to yourself.

_0R10N >>

---

### Post by ajwei810192 on 2010-04-24
Well, this is what I have done, but I still cannot even telnet to my public ip. 

1. I made sure all of my listeners in ports.conf and /etc/apache2/site-enabled with 52108 as the listener. So, I have 
<VirtualHost *:52108> and 
NameVirtualHost *:52108
Listen 52108
I then restarted apache service.

2. I then went to [https://www.no-ip.com/](https://www.no-ip.com/) and registered a new hostname called  hhwebdesign.no-ip.org, and did the port forwarding to 52108

3. I opened up Firewall configuration, and added "52108" for both listening ports to be allowed.

4. I then went to my router, which is 2Wire ** **3800HGV-B, and added a new device for my virtualbox, 

Current Settings: Custom
Device     Allowed Applications     Application Type     Protocol     Port Number(s)     Public IP
192.168.1.64     Alice Virtual Box     -                                TCP     52108                 99.48.66.63
                                                                                          UDP     52108                 99.48.66.63

5. I then reset the firewall settings of the router, and then tried to telnet to my public ip. 

  I had no luck, but what is interesting is, even though I did set up the port forwarding option on no-ip.com to be 52108, when I ran the nmap function to see which port the site is on, it shows the following:

alice@alice-laptop:~$ nmap -v  hhwebdesign.no-ip.org

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-04-24 23:30 EDT
NSE: Loaded 0 scripts for scanning.
Warning: Hostname hhwebdesign.no-ip.org resolves to 2 IPs. Using 208.51.78.252.
Initiating Ping Scan at 23:30
Scanning 208.51.78.252 [2 ports]
Completed Ping Scan at 23:30, 0.10s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 23:30
Completed Parallel DNS resolution of 1 host. at 23:30, 0.20s elapsed
Initiating System CNAME DNS resolution of 1 host. at 23:30
Completed System CNAME DNS resolution of 1 host. at 23:30, 0.10s elapsed
Initiating Connect Scan at 23:30
Scanning url-redirect.noip.net (208.51.78.252) [1000 ports]
Discovered open port 80/tcp on 208.51.78.252
Completed Connect Scan at 23:30, 15.46s elapsed (1000 total ports)
Host url-redirect.noip.net (208.51.78.252) is up (0.13s latency).
Interesting ports on url-redirect.noip.net (208.51.78.252):
Not shown: 998 filtered ports
PORT     STATE  SERVICE
80/tcp   open   http
2200/tcp closed unknown

6. I then looked at the ip address coming from my registered hostname, entered in the commands on the terminal, and I get this: 

alice@alice-laptop:/$ sudo netcat -nv 99.68.66.63 52108
(UNKNOWN) [99.68.66.63] 52108 (?) : Connection refused

Looks like my port is either not forwarded properly, or not opened. Is something in the procedure I have here wrong? In any of the steps, I mean?

Sorry for the long message. I really would like this to be done. Thanks for your help.

---

### Post by ajwei810192 on 2010-04-25
After almost a whole week bumming around messing with the router, I finally found a more economical way, which is to go to [http://www.zymic.com/](http://www.zymic.com/) and register an account and have them host it for me. It is free if anyone is interested. 

Thanks to those of you who offered these previous suggestions.

---

