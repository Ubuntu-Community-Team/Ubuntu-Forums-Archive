---
title: "HELP!! Problems with Comcast broadband internet??"
date: 2012-08-25
forum: General Help
---

### Post by handofdave on 2012-08-25
I have recently subscribed to comcast/xfinity broadband internet and i have found that when I try to use a web browser I have little or no connectivity (the black circle of death). I was informed that Comcast does not provide support for linux users but also that the problem might be in the "config" files. Could some one please help me solve this problem i am new to linux (user for 4months)

---

### Post by Rexilion on 2012-08-25
You have to be a lot more specific before we can help :-s

Do you use a router with modem?
Do you use a router without modem?
Was the router provided by your ISP?
Do you need to install additional software?
Is the networking gear already configured?
Do you only use a modem?
If yes, does your modem have a linux driver?
If yes, do you have pppd configured for this?
What kind of protocol is it?
Annex A, Annex B?
ADSL? ISDN? Phone Line? Sattelite?

etc etc etc...

---

### Post by handofdave on 2012-08-27
hey hey hey! thats a bit much, give me a min to catch up.... ok so here is what you asked for---
using the comcast/xfinity Arris gateway wireless cable modem/router
provided by comcast/xfinity.
as far as the other things you asked for I'm not sure how to find that information.. but this is what i can tell you--my internet seems to work perfectly everywhere else like at school ,the public library, even starbucks, and barnse&noble. 
 if you could tell me where to look (and how--"noobie at work") i could be of more help. sorry but i am a noob.
 thankyou for your help and assistance

---

### Post by drmrgd on 2012-08-27
Do you happen to dual boot, or are you only using Ubuntu?  I've found in my own travels that Comcast is quite particular about running their setup script the first time you access the service, which I believe will only run on a Windows computer.  So, for me, I found that I had to set up the service from my Windows partition by installing their lame software.  Once I ran that for the first time, I could remove the software from Windows and boot into Ubuntu without any issues.  It's just that they want you to establish your account with their "tool" for the first time.

If you've already done all that, let us know and we can starting digging a little deeper.

---

### Post by Rexilion on 2012-08-27
> **drmrgd said:**
> Do you happen to dual boot, or are you only using Ubuntu?  I've found in my own travels that Comcast is quite particular about running their setup script the first time you access the service, which I believe will only run on a Windows computer.  So, for me, I found that I had to set up the service from my Windows partition by installing their lame software.  Once I ran that for the first time, I could remove the software from Windows and boot into Ubuntu without any issues.  It's just that they want you to establish your account with their "tool" for the first time.

If you've already done all that, let us know and we can starting digging a little deeper.

Thanks for helping out. Maybe one can just run the software under wine?

---

### Post by drmrgd on 2012-08-27
> **Rexilion said:**
> Thanks for helping out. Maybe one can just run the software under wine?

That's an interesting thought I hadn't considered.  It might be possible to do that as well.  It's certainly easy enough to try if the OP doesn't have a dual boot set up going.

---

### Post by handofdave on 2012-08-27
That might be a problem because i don't own a copy of windows or at least a copy that is legal. the weird thing is that i have to reload the page several times before it will come up and i don't know much about wine. another thing is that one of the techs said something about a config file that might need to be edited but i didn't quite understand what he was saying.
At the moment i am quite perturbed had i known that comcast doesn't offer support for linux users then i never would have signed on with them. 
My next question is--could it have something to do with my configuration and if so how do i access and edit that particular file?

---

### Post by Rexilion on 2012-08-27
I guess it's some sort of configuration inside the router. Checked the manual?

---

### Post by Tobeus on 2012-08-27
Just out of curiosity, are you trying to connect using a cable, or through wireless?

-Tobeus

---

### Post by handofdave on 2012-08-27
I have tried both wired and wireless and still the same outcome. 
oh and btw i am using an arris gateway tg862g modem... looking into the online manual as we chat..

---

### Post by Tobeus on 2012-08-27
Also, I am assuming since you have talked to comcast that all the simple stuff was done, like resetting the modem, and verifying all the lights.  I know it sounds silly, but sometimes it's the simple things that work.  Please double-check that those are good as well.

-Tobeus

---

### Post by Rexilion on 2012-08-27
You said:

> using the comcast/xfinity Arris gateway wireless cable modem/router

and

> oh and btw i am using an arris gateway tg862g modem

are those the same device?

---

### Post by Tobeus on 2012-08-27
It looks like Xfinity is a service that Comcast offers including both internet and phone.  The Arris tg862g would be the modem they receive as the network device for their home.

-Tobeus

---

### Post by oldfred on 2012-08-27
My Comcast is older, with Comcast only providing modem and I have my own Linksys router.

My modem is at:
[http://192.168.100.1/](http://192.168.100.1/)
and my router is at 
[http://192.168.1.1/index.asp](http://192.168.1.1/index.asp)

What happens if you just use one or the other of the above?

The vendor software usually just automates the setup but you can easily do it manually. It just is you need to get into modem and set addresses. Most is DHCP so very little has to be done. But if also wireless you need to change default name and default passwork or else tomorrow I will be over and use your system instead of mine. :)

---

### Post by Colo993 on 2012-08-27
Handofdave,

More questions:

1. Is your computer connected directly to the cable modem that Comcast provided?  If not, then it is connected to a switch/router?

2. From your terminal can you run a ifconfig -a and paste the results.  This will display the network interfaces on your PC.

3. The actual network interface configuration files can be in /etc/network.  The interfaces file can be used to configure static IPs/routes/additional interfaces.  Lots of documentation on the internet for that.

4.  If you PING a site on the internet from terminal are you getting consistent results? From my Ubuntu laptop:


/etc/network$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=48 time=59.2 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=48 time=58.8 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=48 time=59.1 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=48 time=59.1 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=48 time=58.4 ms
^C
--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 58.418/58.960/59.222/0.399 ms


Colo993

---

### Post by atammin on 2012-12-02
I had similar symptoms when I connected my Linux computers (wireless and with cable) to Comcast router. 

I went through the router admin panel, and noticed that the parental controls were turned ON by default and my Desktop Ubuntu was not set as Trusted. 

Although the blocked sites lists were empty I switched my computer to "trusted" and then I also disabled the parental control where ever possible (since i really have no use for it). 

I did this just few minutes ago - so I am not sure if this has a long lasting positive effect, but at least for now I do not have the problems anymore.

(My original symptoms were exactly the same as the original post suggested: pages not loading, domain names not resolved, having to refresh pages many times, and general slowness when pages were loaded)

---

### Post by atammin on 2012-12-02
Actually - seems the problem was not in the parental controls. The problem came back pretty quickly.

The second solution seems to work way better: 

Edit Network Connections
* Choose the connection (under wired / wireless) 
* Go to "IPv4 Settings" -tab
* Change Method to "Automatic (DHCP) addresses only"
* type Google DNS server addresses: "8.8.8.8, 8.8.4.4" to the "DNS Servers -field
* Hit "Save"

Might make sense to restart networking. 

After these changes, I have not had ANY of the earlier symptoms.

---

### Post by RedRat on 2012-12-02
I have been using Comcast/Xfinity for over 6 years with my various Ubuntu installations. I have never had a problem and I run both a laptop with Ubuntu, two desktops running Ubuntu 12.04 and Mint 13. All have worked with my my Xfinity cable modem and my Linksys routers. All of this goes way back to my starting with Ubuntu 7.04. All of these have worked right out of the box and right after installation.

---

### Post by Rexilion on 2012-12-03
> **RedRat said:**
> I have been using Comcast/Xfinity for over 6 years with my various Ubuntu installations. I have never had a problem and I run both a laptop with Ubuntu, two desktops running Ubuntu 12.04 and Mint 13. All have worked with my my Xfinity cable modem and my Linksys routers. All of this goes way back to my starting with Ubuntu 7.04. All of these have worked right out of the box and right after installation.

Thanks for reporting this. Could you post the output of:

> cat /etc/resolv.conf

Let's see if the DNS hypotheses holds :) .

---

### Post by RedRat on 2012-12-03
> **Rexilion said:**
> Thanks for reporting this. Could you post the output of:



Let's see if the DNS hypotheses holds :) .
Here it is:

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search hsd1.wa.comcast.net

---

### Post by atammin on 2012-12-03
Third time's the charm, right?

Here's what happened to me: things worked well with Google DNS servers until I restarted the computer - and the problems came back. So I went on and did some more digging. I came across [this post]("http://forums.comcast.com/t5/Home-Networking-Router-WiFi/Problems-Connecting-on-Ubuntu/td-p/1297015") in Comcast discussion forums. 

In my case, the problem was related to DNS, but the solution I proposed earlier was not a long lasting one. Issue appears to be with the dnsmasq which tries to resolve host names locally (and is enabled by default in 12.04).

So I followed [these instructions to disable dnsmasq]("http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html"), and now (*still* after several restarts) things are finally working well.

---

### Post by Rexilion on 2012-12-04
> **atammin said:**
> So I followed [these instructions to disable dnsmasq]("http://www.ubuntugeek.com/how-to-disable-dnsmasq-in-ubuntu-12-04precise.html"), and now (*still* after several restarts) things are finally working well.

After the restart, settings were returned to default I guess, or dnsmasq picked up on your settings and applied them slightly different(?). Or overwriting your old configuration (maybe)?

That's just braindead...

---

### Post by Stuie675 on 2012-12-04
Hi,

sorry if I am getting in on this to late, but I am not seeing how Ubuntu would cause these issues. My first spot I would be looking is the router provided by ComCast, and from the OPs listing of "gateway tg862g", doing a quick search his symptoms seem to be a common issue with this device. I would call ComCast and get a replacement, then if that does not resolve your issue. Look into the default settings on the router, not the PC.

Also some basic troubleshooting I would do is start pinging the closest device, which will be the router and make your way out. Ping the router which is probably 192.168.x.1, and ping it a good 50 or so times, see if you get any drops. Or you could also do a traceroute to a site like google.com or where ever and see where it drops.

---

### Post by RedRat on 2012-12-04
> **Stuie675 said:**
> Hi,

sorry if I am getting in on this to late, but I am not seeing how Ubuntu would cause these issues. My first spot I would be looking is the router provided by ComCast, and from the OPs listing of "gateway tg862g", doing a quick search his symptoms seem to be a common issue with this device. I would call ComCast and get a replacement, then if that does not resolve your issue. Look into the default settings on the router, not the PC.

Also some basic troubleshooting I would do is start pinging the closest device, which will be the router and make your way out. Ping the router which is probably 192.168.x.1, and ping it a good 50 or so times, see if you get any drops. Or you could also do a traceroute to a site like google.com or where ever and see where it drops.

I agree. I have run a cable modem that I bought and Linksys wireless routers and have not had any such problems. About two years ago, I switch out my cable modem with one provided by Comcast, and still no problems. 

I suspect that the problem may well be with your router. The cable modem connects to the router via a simple ethernet connection and just gives you a gateway out/in. This is pretty vanilla. However, it is the router that connects your computer to the internet and it sounds as if something ain't quite right there. I would suggest borrowing someone else's router that actually works or go to their home and see if you get internet access--but get a router that is actually working correctly. 

Router do crap out. I also had to replace mine about two years ago, again with a Linksys. At that time Comcast did not provide them.

---

### Post by atammin on 2012-12-05
Hey,

At least for me - all problems are gone now that I disabled dnsmasq. 

Reason why I suspected problem was in Ubuntu rather than router was the fact that I did not experience same intermittent connectivity with my Mac or Windows 7 PC (or other internet connected devices like phones, tablets, tv). 

I don't really know on detailed level what it is / was dnsmasq did not like in the Comcast provided router - but now, with dnsmasq disabled, life is a bliss.

---

