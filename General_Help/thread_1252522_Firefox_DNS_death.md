---
title: "Firefox DNS death"
date: 2009-08-28
forum: General Help
---

### Post by kihjin on 2009-08-28
The problem I'm having is a longstanding problem. I've had this problem ever since I upgraded to a 64bit system. I have a quad core now. Since then I've used 8.04, 8.10 and 9.04, and varying versions of firefox. Today I compiled Firefox 3.5.2 from source just for the purpose of testing this. 

For the most part, browsing on firefox works. I don't have trouble accessing any sites, and then suddenly I'm no longer able to load any more sites. Firefox hangs on "Looking up..." I know for a fact that my network is still active, and a quick check with dig verifies that DNS is still working. Even if I press stop, close all my tabs, I can't load anything. The basic solution I've found is to close firefox, and reopen it. Right as firefox closes, there's a burst of data on the network.

I have not noticed any patterns or specifically how long after opening the browser this occurs. It does not happen on my 32bit dual core laptop (running 8.10 firefox 3).

I have tried various about:config tweaks with no success. Once firefox forgets how to do a DNS lookup, it's stuck like that until I exit completely.

I have no tried changing my DNS addresses, but, I don't see how that could be the problem since I don't experience this issue on my laptop, and it's only firefox that forgets.

Thanks.

---

### Post by bchurchill on 2009-08-28
I assume from what you wrote that you've tried the binary Ubuntu package already, and that didn't make a difference.  Can you load things by IP address (eg google is [http://74.125.65.103)?](http://74.125.65.103)?)  How about pages on localhost or your LAN?

---

### Post by ptn107 on 2009-08-28
> It does not happen on my 32bit dual core laptop (running 8.10 firefox 3).
Is your firefox 3 on 8.10 compiled from source or is it the stock 3.0.13?

---

### Post by lovinglinux on 2009-08-29
I know you said you have used some config tweaks but have you tried these:

- Changing the value of **network.dnsCacheExpiration** to a big value, so it doesn't check for DNS very often? I use 7200.

- Changing the value of **network.dnsCacheEntries** to a big value, so Firefox stores more DNS entries? I use 1000.

- Changing **network.dns.disableIPv6** to true, so ipv6 is disabled? ipv6 is known to cause this kind of connection problem.

---

### Post by kihjin on 2009-08-29
Hey everyone. Thanks so much for the responses. They are all appreciated. 

Before yesterday I had been running the ubuntu binary release of firefox 3.0. Every day I dealt with this dns issue, and I even researched the issue by searching these forums. I got used to closing firefox and "saving tabs."

I've been using firefox 3.5 from source, and the problem does not seem to occur nearly as much. Though, I've only been using it for less than a day, so we'll see how that goes. 

I had not thought to try the IP address for google. I have now bookmarked that address, so when the problem occurs I can quickly try the IP and see what happens. What I have noticed with firefox 3.5 is that occasionally it will hang briefly on "looking up..." 
 At this point I quickly open the google IP in a new tab. Google loads up before the other tab even finishes resolving. 

The laptop is using the binary install. 

@Lovinglinux: Those are the config tweaks I had done in my binary 3.0 install. I used the following values:

network.dnsCacheExpiration = 3600
network.dnsCacheEntries = 500
network.dns.disableIPv6 = true

This actually seemed to make the problem somewhat more pronounced (in ff 3.0), so I didn't keep them for more than a few days. I did leave the ipv6 disabled, but the other two I set back to 0.

---

### Post by kihjin on 2009-09-15
Well after using Firefox 3.5 for a couple weeks, I can say that my problem **still exists**. At first, it seemed to have gone away, but it's been returning with a vengeance. 

Basically, firefox locks up on a DNS query and then refuses to do anything else, load any other websites. It wont even complete the query its already doing. I have the google IP ADDRESS bookmarked. In most cases, opening this IP in a new tab does nothing! The tab just sits there, doesn't appear to load anything at all.

However, I am able to load localhost (my local apache) just fine. 

The only solution that works every time is to completely close firefox and reopen it.

---

### Post by winotree on 2009-09-15
Of course, you've seen both of these?

[http://kb.mozillazine.org/Network.dnsCacheExpiration](http://kb.mozillazine.org/Network.dnsCacheExpiration)
[http://kb.mozillazine.org/Network.dnsCacheEntries](http://kb.mozillazine.org/Network.dnsCacheEntries)

As I read them, it says to keep 20 entries in cache, each one for 60 seconds as default.  

As you have it -- with both defaulted to zero -- it says to keep no entries in cache, for no length of time.  

That is to say that Firefox has to look for each new DNS address which it then can't keep, then place it for storage in a place where it's told not to store it for any amount of time.  Is this a correct reading?  :?

Possible Remedy - enter defaults, live with it for two or three days, post results.  ;)

---

### Post by kihjin on 2009-09-15
I will give this a try.

However, DNS does not explain why I was not able to load a google IP (during the query lock)

[http://74.125.65.103/](http://74.125.65.103/)

---

### Post by kihjin on 2009-09-19
So after using **winotree**'s suggestion for a few days, it is obvious that my experience is better, only *slightly*.

This evening alone, I have experienced several dead-locking situations. Though, unlike in the past these dead-locking situations were mostly temporary, only requiring 30-60 seconds to "fix" themselves naturally. 

Still I often find it easier to exit the browser, and try again. At which point all the pages load without effort.

---

### Post by winotree on 2009-09-19
Well, it's good news that something I offered helped someone -- bad news that it wasn't a true fix.  :(  I read a lot (have the time to do so) and haven't ever come across anything like what you're going through.  You say it's been happening over a long period and across different distributions; you say you custom configured the last one as a test, is that correct?  :)

Question -- have you used the *same profile* for all of them or not?  If so, I'd bet that's your issue -- creating a new one should really help -- if not I'm truly at a loss as being any further help.  Regardless, my best to you.  Maybe we'll see each other around the forum??  :D

---

### Post by kihjin on 2009-09-19
Yes, thank you for your attempt. I have also done searching on this, and only found one similar situation:

[http://ask.metafilter.com/74766/Why-does-my-Firefox-lose-its-ability-to-do-DNS-lookups](http://ask.metafilter.com/74766/Why-does-my-Firefox-lose-its-ability-to-do-DNS-lookups)

But this guy is using Windows XP. Turns out it was Norton Antivirus that was causing the trouble. Obviously I'm going through something different.

This problem started when I upgraded to 64bit back in 8.04, been an issue ever since. Initially I had been using the binary distribution of Firefox, but my recent attempt is a locally compiled Fire^H^H^H^HShiretoko 3.5

I do believe I've been using the same profile... it's worth a shot to make a new one and see what happens.

I might look into debugging firefox and see where it is dead-locking on the DNS response.

---

### Post by winotree on 2009-09-19
[Putting off doing household chores until coffee takes effect]  :D

[http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/)
[https://addons.mozilla.org/en-US/firefox/addon/8923](https://addons.mozilla.org/en-US/firefox/addon/8923)
[http://kb.mozillazine.org/Error_loading_any_website](http://kb.mozillazine.org/Error_loading_any_website)
[http://www.reddit.com/r/linux/comments/9gcmu/does_anyone_else_get_slow_dns_lookups_in_firefox/](http://www.reddit.com/r/linux/comments/9gcmu/does_anyone_else_get_slow_dns_lookups_in_firefox/)

[https://answers.launchpad.net/ubuntu/+question/7789](https://answers.launchpad.net/ubuntu/+question/7789)
[http://forums.pcbsd.org/viewtopic.php?f=1&t=14127](http://forums.pcbsd.org/viewtopic.php?f=1&t=14127)

NOTE - I just entered search terms (hopefully different from yours) then did a copy-and-paste without fully reading these links -- you know more about what you need than I do.  ;)

---

### Post by lovinglinux on 2009-09-19
> **winotree said:**
> NOTE - I just entered search terms (hopefully different from yours) then did a copy-and-paste without fully reading these links -- you know more about what you need than I do.  ;)

Yep, I can see that :)

> **winotree said:**
> 
[http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/)

Same thing suggested by [post #4](http://ubuntuforums.org/showpost.php?p=7864246&postcount=4)

> **winotree said:**
> [https://addons.mozilla.org/en-US/firefox/addon/8923](https://addons.mozilla.org/en-US/firefox/addon/8923)

Does not apply to FF 3.5.x, since this is done natively as suggested by [post #4](http://ubuntuforums.org/showpost.php?p=7864246&postcount=4)

> **winotree said:**
> [http://forums.pcbsd.org/viewtopic.php?f=1&t=14127](http://forums.pcbsd.org/viewtopic.php?f=1&t=14127)

Basically, the ipv6 issue, already suggested by [post #4](http://ubuntuforums.org/showpost.php?p=7864246&postcount=4).

---

### Post by winotree on 2009-09-19
:(

---

### Post by kurian2z5 on 2010-04-26
I have the EXACT same problem with the EXACT same symptoms. However when it hangs on looking up I cannot even open localhost or other LAN IPs in a new tab. After 1-2 minutes all the tabs instantly load. Otherwise the only way is to close and reopen Firefox.

---

### Post by lovinglinux on 2010-04-27
> **kurian2z5 said:**
> I have the EXACT same problem with the EXACT same symptoms. However when it hangs on looking up I cannot even open localhost or other LAN IPs in a new tab. After 1-2 minutes all the tabs instantly load. Otherwise the only way is to close and reopen Firefox.

See post #4

---

### Post by kurian2z5 on 2010-04-27
> **lovinglinux said:**
> See post #4

I have already disabled IPv6 DNS in about:config. The other two settings are only a pseudo workaround which I do not want to do, since the problem only started a few days ago and was working fine before.

The fact that even localhost or LAN IPs don't open while it is stuck in another tab querying DNS implies it is just bad programming in Firefox.

I forgot to mention I am using Windows Server 2008 R2. I posted here because this is one of the few threads that fit my exact problem.

---

### Post by lovinglinux on 2010-04-27
> **kurian2z5 said:**
> I have already disabled IPv6 DNS in about:config. The other two settings are only a pseudo workaround which I do not want to do, since the problem only started a few days ago and was working fine before.

The fact that even localhost or LAN IPs don't open while it is stuck in another tab querying DNS implies it is just bad programming in Firefox.

I forgot to mention I am using Windows Server 2008 R2. I posted here because this is one of the few threads that fit my exact problem.

Create a new Firefox profile with the Profile Manager and test it. If it works, then you have an extension messing things up or suboptimal settings.

Click "Start >> Run" and run this command:

```
firefox -P
```

---

### Post by kurian2z5 on 2010-04-27
> **lovinglinux said:**
> Create a new Firefox profile with the Profile Manager and test it. If it works, then you have an extension messing things up or suboptimal settings.

Click "Start >> Run" and run this command:

```
firefox -P
```

It affects all profiles. I have separate profiles with -P -no-remote for daily use, guests and pr0n. The other profiles don't have any extensions and are basically blank. The first thing I did was create a new profile and copy my sqlite dbs from my old one to keep my cookies/passwords. about:config settings are all at default except for disable IPv6 DNS.

---

### Post by lovinglinux on 2010-04-27
> **kurian2z5 said:**
> It affects all profiles. I have separate profiles with -P -no-remote for daily use, guests and pr0n. The other profiles don't have any extensions and are basically blank. The first thing I did was create a new profile and copy my sqlite dbs from my old one to keep my cookies/passwords. about:config settings are all at default except for disable IPv6 DNS.

Have you tried another browser, another DNS server and another Ubuntu user?

Also see [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-becomes-unresponsive-(grey)-frequently-2).

---

### Post by kurian2z5 on 2010-04-27
> **lovinglinux said:**
> Have you tried another browser, another DNS server and another Ubuntu user?

Opera and IE both work fine (during the time when Firefox is stuck and otherwise). I have tried using the router's IP to DNS forward to my ISP's DNS servers, setting the DNS on the PC servers to OpenDNS, and forwarding using the Domain Controller's DNS server.

I mentioned I was on Server 2008 R2. I haven't tried another user. I'll have to try when I get back home.

Is there a way to make Firefox use the OS's DNS resolver instead of doing it on its own? Windows programs can query DNS through the OS's DNS Client. The network connection for the lookup will originate from one of the system processes instead of the application. The application will only connect to the target IP. If DNS Client is stopped only then the application directly contacts the DNS server. But Firefox directly contacts the DNS server whether this is disabled or enabled. (I am not talking about local DNS server, I mean OS's DNS Client present on all workstation Windows)

---

