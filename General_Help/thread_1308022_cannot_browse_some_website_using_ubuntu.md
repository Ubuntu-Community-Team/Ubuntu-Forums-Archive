---
title: "cannot browse some website using ubuntu"
date: 2009-10-31
forum: General Help
---

### Post by aimwin on 2009-10-31
update 8/12/2009
thsolar.com finally works
I tried to find out why and how do they fixed it.
Then answer is clear that it is the web server, and nothing to do with ubuntu.
How do they fixed it, I could not get the answer.

But there are many sites like this one as well.
So you just keep in mind of what has happen.

Thanks for everyone try to help solving the problems.

Update 19/11/2009
The current status is it is fixed.
I am still waiting for the information, How it got fixed.
---------------------------
[COLOR="Red"]I cannot browse
[www.thsolar.com](www.thsolar.com)
using (as of Nov 1 2009),(discovered Apx 10 August 2009)
Ubuntu (any 8.10, 9.04. 9.10) with Firefox, Opera 10, Google Chrome, and Arora.[/COLOR] which I will now call "Ubuntu"

If I reboot to[COLOR="Magenta"] windowXP, I can use firefox to browse [www.thsolar.com](www.thsolar.com) imediatly.[/COLOR]

The above problems were tested with **_3 different computers_** and they are not the same brand. Using the **same connections**, 3 computes and at 2 different suburbs, Optus Adsl connections in both places, And they have the same problems and XP on all of them have not problems to browse the site, [www.thsolar.com](www.thsolar.com).

I report to the [www.thsolar.com](www.thsolar.com). that we cannot use "Ubuntu" to browse their site.

They ask me to try 
[http://211.101.136.42:8081/TSINGHUA/templates/T_Product_en/index.aspx?nodeid=65](http://211.101.136.42:8081/TSINGHUA/templates/T_Product_en/index.aspx?nodeid=65)
=== they said it is a new testing site =====

Yes "Ubuntu" can browse

Please help verify by browsing those 2 web address from the same company.
And see if you got the same result.

The IT department, has not report back to me, why it happen like that.
But I was told by my contact, that the IT department has report to their ISP.

Since I wait for almost 2 weeks now, I decide to start a new Thread and see if anyone know the reason.

Or If some one got the same problem with other sites please help report.

**_Why "Ubuntu" cannot browse some sites and how to solve this problems?_**

I attached the [ATTACH]133921[/ATTACH]
So you can see the background are the successful browsing,
using [http://211.101.136.42:8081/TSINGHUA/templates/T_Product_en/index.aspx?nodeid=65](http://211.101.136.42:8081/TSINGHUA/templates/T_Product_en/index.aspx?nodeid=65)

The front [www.thsolar.com](www.thsolar.com) that "Ubuntu" fail to browse.

Later Post:
I decided to post to lunchpad as well since I was not sure if it is a bug.
[https://answers.launchpad.net/ubuntu/+question/87793](https://answers.launchpad.net/ubuntu/+question/87793)

The moderator please have a look if I should have only one thread in what part or not.

Please take action that you think it is appropriate.

Thank you

---

### Post by coffeecat on 2009-10-31
I get the same. With Ubuntu Karmic and Firefox I get a "problem loading page" with [www.thsolar.com]("http://www.thsolar.com"), but the page with the 211.101.136.42 comes up just fine.

It's a bit ironic that you can access thsolar.com with Windows because [Netcraft]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fwww.thsolar.com%2F") reports that they are using Linux/Apache on their server. Also - look at that Netcraft report more closely. The numeric IP address is different from the one they gave you. Interesting.

---

### Post by aimwin on 2009-10-31
> **coffeecat said:**
> I get the same. With Ubuntu Karmic and Firefox I get a "problem loading page" with [www.thsolar.com]("http://www.thsolar.com"), but the page with the 211.101.136.42 comes up just fine.

It's a bit ironic that you can access thsolar.com with Windows because [Netcraft]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fwww.thsolar.com%2F") reports that they are using Linux/Apache on their server. Also - look at that Netcraft report more closely. The numeric IP address is different from the one they gave you. Interesting.

Thank for teaching me how to look for more info on this.

I will send this thread to [www.thsolar.com](www.thsolar.com).
I hope they will help us find the reasons.

It is bad to spread the words that Ubuntu cannot access all websites.
But Windows Can....


I hate to see that.  I hope we resolve this soon.

Any one else has the same problems???

---

### Post by dependancyhell on 2009-10-31
Can confirm the problem, and also add I tried changing the browsers user-agent string to imitate Windows XP with IE6, and Ubuntu is still blocked.


No ideas for solution though, sorry.

---

### Post by lovinglinux on 2009-10-31
I also confirm the same behavior.

---

### Post by lovinglinux on 2009-10-31
I'm not sure, but perhaps Windows has stored the DNS info or something, so it can connect while Ubuntu is trying to query the DNS server without success. Is just a guess anyway, since I'm not sure how this stuff works. 

I can't even ping or traceroute. Also tried to connect via web proxy, but no joy.

Here are the traceroute results:


> **Traceroute to 58.30.5.50**


Analysis:
Number of hops: 18

Last hop responding to ICMP: 14, UDP: 14, TCP: 0.

There appears to be a firewall at  (hop 15) that blocks ICMP (ping) packets.

There appears to be a firewall at  (hop 15) that blocks unwanted UDP packets.

There appears to be a firewall at 174.133.202.225 (hop 1) that blocks unwanted TCP packets.


Legend:

    * ECN was not used on the TCP packets. To use ECN, click here.
    * T1/T2/T3 are the round-trip times in milliseconds (1/1000ths of a second).
    * T1 uses a proper ICMP-based tracert (Microsoft style). T2 uses a UDP-based traceroute (Unix-style). T3 uses a TCP-based traceroute (port 80).
    * Since many ISPs now block ICMP and/or packets to unknown ports, T3 (rarely used by traceroute programs) typically shows the best results.
    * Best times may be theoretical (if it takes 80ms to hop 10, and 50ms to hop 11, we say the best time for hop 10 is 50ms).
    * If no reverse DNS entry is given for an IP, we display 'unknown.example.com' if the domain name is known. 

---

### Post by clhsharky on 2009-10-31
Firefox in Wine - no go
Firefox in XP KVM virtual machine - good

---

### Post by qwerty2009 on 2009-10-31
i dont understand why i can browse teh site and you lot cant ? im using karmic and the default firefox that comes with ubuntu

---

### Post by lovinglinux on 2009-10-31
> **qwerty2009 said:**
> i dont understand why i can browse teh site and you lot cant ? im using karmic and the default firefox that comes with ubuntu

Probably the route from your machine to the site is not compromised. The site is in Australia and I'm in Brazil.

---

### Post by bibekdai on 2009-10-31
The site may be down and windows may be displaying cached page ????
PING [www.thsolar.com](www.thsolar.com) (58.30.5.50) 56(84) bytes of data.
^C
--- [www.thsolar.com](www.thsolar.com) ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5040ms

---

### Post by judge jankum on 2009-10-31
when i try to log in at homestead.com it says i have to have a computer with windows :(

---

### Post by aimwin on 2009-11-01
> **qwerty2009 said:**
> i dont understand why i can browse teh site and you lot cant ? im using karmic and the default firefox that comes with ubuntu

Which site you can browse the site please confirm?
The one that we cannot access is
[www.thsolar.com](www.thsolar.com)

That will give some more light if you can, please specify.

I want to confirm that my Ubuntu 9.04 from Thailand cannot access the same site too.
The desktop in Thailand is also dual boot. Yes windowXP on that computer can access the site.
But not the Ubuntu OS.

I came back to Australia early October, and found it is the same as in Thailand.

Please specify your country as well please just to help find out why XP can but Ubuntu cannot access the site.

---

### Post by aimwin on 2009-11-01
> **lovinglinux said:**
> I'm not sure, but perhaps Windows has stored the DNS info or something, so it can connect while Ubuntu is trying to query the DNS server without success. Is just a guess anyway, since I'm not sure how this stuff works. 

I can't even ping or traceroute. Also tried to connect via web proxy, but no joy.

Here are the traceroute results:

I don't think it is Cache in DNS server, if it is, why Windows can access it but our Ubuntu cannot access.

As "coffeecat" point out, the server that host [www.thsolar.com](www.thsolar.com) is also Apache/Linux.

---

### Post by Eddie Wilson on 2009-11-01
> **judge jankum said:**
> when i try to log in at homestead.com it says i have to have a computer with windows :(

I have no such problem with homestead.com. Everything works properly.

---

### Post by aimwin on 2009-11-01
> **bibekdai said:**
> The site may be down and windows may be displaying cached page ????
PING [www.thsolar.com](www.thsolar.com) (58.30.5.50) 56(84) bytes of data.
^C
--- [www.thsolar.com](www.thsolar.com) ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5040ms

The IT department of [www.thsolar.com](www.thsolar.com) cofirm that the site is up.
And they don't know why,
but they, at the moment, still blame to the ISP, and has informed the ISP.

And the 2 computers I tested, never access the [www.thsolar.com](www.thsolar.com) before,
neither XP nor Ubuntu, not even the router.
And both with Ubuntu no, with XP yes immediatly successful.

So we have been waiting, and I thought they might not know.
And if they don't use Ubuntu, 
they would careless to find out if Ubuntu can access it or not.

Regarding Ping, many site the firewall will block Ping port.
But the [http://.](http://.)........ that is still accessible.
Pleae confirm if I have the correct understanding.

---

### Post by aimwin on 2009-11-01
> **judge jankum said:**
> when i try to log in at homestead.com it says i have to have a computer with windows :(

I can also access homestead.com with no hickup,

it gave out sound perfectly immediately too.

My is Karmic 9.10 release updated from 9.10 beta.

---

### Post by mgabby on 2009-11-01
The Web Page displays correctly for me -- I'm using Firefox 3.5.4 -- it also works in Opera 10.01. I don't see the problem.

Mike Gabby

---

### Post by aimwin on 2009-11-01
> **mgabby said:**
> The Web Page displays correctly for me -- I'm using Firefox 3.5.4 -- it also works in Opera 10.01. I don't see the problem.

Mike Gabby

I hope you meant [www.homestead.com](www.homestead.com)

Please confirm if you can acces [www.thsolar.com](www.thsolar.com) or not?

---

### Post by aimwin on 2009-11-01
I decided to post to lunchpad as well since I was not sure if it is a bug.
[https://answers.launchpad.net/ubuntu/+question/87793](https://answers.launchpad.net/ubuntu/+question/87793)

The moderator please have a look if I should have only one thread in what part or not.

Please take action that you think it is appropriate.

Thank you

---

### Post by coffeecat on 2009-11-01
@**aimwim**, some more information for you, although Goodness knows what it means. :?

Firefox 3.5.4 and Safari 4.0.3 in Snow Leopard MacOS: your [www.thsolar.com]("http://www.thsolar.com") site opens just fine. Or I presume fine - I can't read whatever characters those are! :wink: Interestingly, the page renders differently between FF and Safari.

But more interestingly:

In Windows 7 RC running as a VirtualBox guest with Ubuntu Jaunty as the host OS. I get time outs with both Firefox 3.5.4 and IE8. Which suggests, as an earlier poster pointed out, that this is not a user agent issue. Perhaps the (Linux-running) web-server doesn't like being contacted by a Linux host. Has anyone tried another distro? I think I've zapped all my Fedora and Mandriva partitions, but I'll have a look on my other desktop later. It might be interesting, because I wouldn't be surprised if the problem is in the web-server not Ubuntu.

**Edit:** this is getting to be even more interesting. As expected Mandriva couldn't load that site either. But I have Windows 7 RC as a native install on sda1 on my other machine. **Neither Firefox nor IE8 would display [www.thsolar.com](www.thsolar.com) in Windows 7**.

@**aimwim**: this has to be a website problem. Why not ask them why they don't let Windows 7 through either?

Anyone got Vista to try? :lol:

---

### Post by aimwin on 2009-11-01
> **coffeecat said:**
> @**aimwim**, some more information for you, although Goodness knows what it means. :?
..............
@**aimwim**: this has to be a website problem. Why not ask them why they don't let Windows 7 through either?

Anyone got Vista to try? :lol:

Yes I will for sure ///

I will send them every things today as they start working now.

Thanks for helping the test, I don't have Windows 7 nor Vista. 
Anyone has it please help report back so we know exactly what the happening?

---

### Post by aimwin on 2009-11-18
[www.thsolar.com](www.thsolar.com)

is now working for Ubuntu Linux

I am waiting for the information, how did the IT team fixed it.

---

### Post by aimwin on 2009-12-08
update 8/12/2009
thsolar.com finally works
I tried to find out why and how do they fixed it.
Then answer is clear that it is the web server, and nothing to do with ubuntu.
How do they fixed it, I could not get the answer.

But there are many sites like this one as well.
So you just keep in mind of what has happen.

Thanks for everyone try to help solving the problems.

---

