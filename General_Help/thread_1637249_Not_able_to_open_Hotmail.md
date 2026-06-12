---
title: "Not able to open Hotmail"
date: 2010-12-04
forum: General Help
---

### Post by sanjaydelhi on 2010-12-04
I just installed Ubuntu 10.10  - the Maverick Meerkat -. 

I am not able to open hotmail. Just a blank screen. I can open yahoo and gmail though.

I tried to open with Google Chrome and FireFox

Even following sites are not opening.

[http://www.coderanch.com/](http://www.coderanch.com/)
[http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)



I have opened all the above sites when I just booted from XP.

---

### Post by Frogs Hair on 2010-12-04
Hi and Welcome

That is downright strange ! I am able to use Hotmail in Opera and Firefox.Do you have flash installed yet ? There may be elements on that page that require flash. Both of the sites you posted open in both browsers.

---

### Post by sanjaydelhi on 2010-12-04
No I do not have flash installed. I just installed brand new Ubuntu OS. Right now I am in XP and I could open hotmail and other sites without problem. I will go back to Ubuntu again in a minute and try.

---

### Post by sanjaydelhi on 2010-12-04
Now I could open all the sites.


I guess after brand new install when I started OS, I updated everything which was there for update. May be it required restart or something.

But now I could open all the sites.:D

Thanks.

---

### Post by kanishkdudeja on 2010-12-04
great. please mark this thread as solved.

---

### Post by sanjaydelhi on 2010-12-06
No it does not work. 

Yesterday after working smooth for sometime, again it was not opening few sites. So I decided to wait for sometime and try again. Again today I got problem. Then I uninstalled OS and reinstalled new Ubuntu. Now I installed "Ubuntu 10.04 LTS   - the Lucid Lynx" Amd_64 version. I see same problem. Not able to open hotmail and few sites at all. But I can open google. I can open Ubuntu forums. I had screenshot of error console of filrefox. I am attaching it.

My hardware is Dell Vostro 1015, 2 GB RAM, 1,8 GHz Dual core processor.

---

### Post by sanjaydelhi on 2010-12-06
Update on it.

I did some search. My guess is it is something to do with MTU which I found for XP at following link.

[http://www.indiabroadband.net/broadband-how/26551-setting-correct-mtu-value.html](http://www.indiabroadband.net/broadband-how/26551-setting-correct-mtu-value.html)

I did similar changes in my Ubuntu DSL connection to set correct MTU.
For now hotmail has opened. I tried other sites, they also opened. But firefox error console do show some errors like the following.

```
Warning: Unknown property 'zoom'.  Declaration dropped.
Source File: http://www.google.co.in/
Line: 1
```Let's see how it goes. If it goes well for few days, I will post results here.

I am marking this thread as solved. I request moderators to change the title of thread from hotmail not opening to "few sites not opening" so that if someone gets into similar problem will be able to find the thread quickly.

Thank you.

---

### Post by sanjaydelhi on 2010-12-06
I again started getting same problem. I think this specific to BSNL broad band in India. It works well on XP, CentOS, but not on Ubuntu. I think I will have to wait for few days and find solution on this before I can start using Ubuntu. :(

---

### Post by dineshs on 2010-12-06
> I did similar changes in my Ubuntu DSL connection to set correct MTU.
I think MTU is the issue.[Here]("http://ubuntuforums.org/showthread.php?t=872346") is a guide
How is your modem setup?bridge or PPPoE?

---

### Post by sanjaydelhi on 2010-12-07
> How is your modem setup?bridge or PPPoE? 	

I don't know how to find out.

I tried opening [http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) this site. but It it is not opening.

I am new to Linux.

---

### Post by sanjaydelhi on 2010-12-07
I followed instructions on CD of my Modem for linux.
At the end of setup this was my summary.

```
VPI/VCI : 0/35
Connection type : PPPoE
Service Name : pppoe_0_35_1
Service Category : UBR
IP Address : Automatically Assigned.
Service State : Enabled.
NAT : Enabled
Firewall : Enabled.
IGMP Multicast : Disabled.
Quality of Service : Disabled.
```


Result is not able to open any site in Ubuntu at all.
Before I did this setup, it used to ask me user name, password of BSNL. Now it does not ask. Which means user name , password is saved in modem.

So the result is in Ubuntu, I can  not access internet at all now after setup of modem.
In XP, I can access internet but I do not have to enter user name, password of BSNL.

---

### Post by dineshs on 2010-12-07
So now your modem is in PPPoE mode.Can you post the result of```
ifconfig -a
```and ```
ping 4.2.2.1 -c3
```
What is the modelname of your modem?

---

### Post by sanjaydelhi on 2010-12-07
dineshs,

Thank you very much for the help.

Just now I again restarted and strange. It is working. I opened all sits including hotmail. But I really hope it keeps working. But I think it will work now. Thank you once again for the help. :D

---

