---
title: "Address Redirect Problem in Firefox"
date: 2011-12-12
forum: General Help
---

### Post by Ian Clark on 2011-12-12
[FONT="Comic Sans MS"][COLOR="Navy"]I've got a readdressing problem in China which I thought everyone might find interesting.

Recently my ISP went down and when I went to my address, <website>.org, a spam page came up instead.

The offending IP 202.102.110.207 is on my NoScript blacklist and so is the domain 025.zhenhuasuan.com, so what I expected to happen was that the redirect would stop. YET, even with <website>.org coming from my server with no problem, when I type in <website>.org into my firefox browser, the address redirection still happens.

Some interesting points:

1. If I use SeaMonkey instead, the readdressing doesn't happen
2. Even with cookies cleared and 202.102.110.207 blocked via NoScript, the redirect happens again and the cookie is reinstalled into Firefox. Now cookies are blocked from both that IP and 025.zhenhuasuan.com, but this doesn't stop the redirect.
3. I [blacklisted]("http://www.ehow.com/how_8430122_blacklist-website-ubuntu-firefox.html") 025.zhenhuasuan.com by editing the etc/hosts file (I'm running Ubuntu 10.04). The readdressing STILL happens, only that I get a "could not connect to the server" error in Firefox with the address still showing as 025.zhenhuasuan.com! (I assume the same would happen if I installed [BlockSite]("https://addons.mozilla.org/it/firefox/addon/blocksite/?src=search") FF addon).
4. I ran FF in safemode according to [this]("http://www.ehow.com/how_2315720_run-firefox-safe-mode.html"), ran FF without plugins and the address redirect was still there. Not a rogue plugin!
5. I also tried about:config and searched for 025.zhenhuasuan.com and got no results. I can't find where the redirect is being ordered from in the config file. (any suggestions?)

I contacted the [developer]("http://maone.net/") of NoScript and he said:

> there's probably something (a rogue add-on / toolbar or plugin? maybe a proxy configuration?) installed into your Firefox profile which performs the redirect. At least, this is the only theory consistent with the fact Seamonkey is unaffected.

Please check if running Firefox in safe mode or with a clean profile helps. If it does, you may need [http://kb.mozillazine.org/Transferring_data_to_a_new_profile](http://kb.mozillazine.org/Transferring_data_to_a_new_profile)

There's no toolbar, plugins/addons have been disabled and the thing still redirects - so I don't think that's the problem. Making a new profile would work, but it takes too long to keep up with all the new hijacking attacks.

Any suggestions on how I might kick this Chinese virus? Thanks in advance to anyone who has read this far![/COLOR][/FONT]

---

### Post by Ian Clark on 2011-12-12
[FONT="Comic Sans MS"][COLOR="Navy"]I installed an extension which looked very apt, [NoRedirect]("https://addons.mozilla.org/zh-CN/firefox/addon/noredirect/?src=oftenusedwith"). Unfortunately I don't understand the syntax for the blacklist, like:

> ^[http://(?:](http://(?:)[^/]+\.)?websearch\.verizon\.net

What the heck is that?!

I haphazardly tried a couple filters...

> ^[http://025.zhenhuasuan.com*](http://025.zhenhuasuan.com*)
^[http://202.102.110.207*](http://202.102.110.207*)

with "origin" and "DNS" checked, which then yielded a very interesting address over the "can't connect to server" error:

http://202.102.110.207:8080/1.htm?AIMT=http://<website>.org/&host=<website>.org&refer=&server=111&pre=1323700940101

Looks like the "AIMT" is what is redirecting http://<website>.org address queries. The plot thickens! [/COLOR][/FONT]:popcorn:

---

### Post by lovinglinux on 2011-12-14
Start a clean profile. Adding a redirecting add-on will just masquerade the real problem.

---

### Post by Ian Clark on 2011-12-17
> **lovinglinux said:**
> Start a clean profile. Adding a redirecting add-on will just masquerade the real problem.

I don't have the time to create a new profile every time my server goes down (which happens often). Chinese ISP's jump in when you type in an address and that address isn't reachable, showing you spam.

Now the address is reachable and I can only get the spam. The problem will quickly reappear if I start with a new profile, so I'm looking for a way to test how it is my ISP is spamming me and solve the problem from the root.

The program I mentioned above is actually designed for Chinese trying to block this spam. However for the redirect I had before installing it, this program can only block connection to their spam page, and doesn't allow me to get to the address I was trying to get to in the first place.

---

### Post by lovinglinux on 2011-12-17
> **Ian Clark said:**
> I don't have the time to create a new profile every time my server goes down (which happens often). Chinese ISP's jump in when you type in an address and that address isn't reachable, showing you spam.

Now the address is reachable and I can only get the spam. The problem will quickly reappear if I start with a new profile, so I'm looking for a way to test how it is my ISP is spamming me and solve the problem from the root.

The program I mentioned above is actually designed for Chinese trying to block this spam. However for the redirect I had before installing it, this program can only block connection to their spam page, and doesn't allow me to get to the address I was trying to get to in the first place.

After a second though, I realized the problem might me somewhere else. Please try to reach your web site using the IP address instead of the domain name and report back. I suppose your ISP is redirecting the domin when the site is down and Firefox is keeping the DNS record. When you start Sea Monkey or a new profile, the DNS record is clean, so it queries your ISP and it returns the correct address, since the site is live.

You could try to use an add-on like [DNS Flusher](https://addons.mozilla.org/en-US/firefox/addon/dns-flusher/) or use a different DNS provider, like OpenDNS or Google DNS.

---

### Post by Ian Clark on 2011-12-19
> **lovinglinux said:**
> After a second though, I realized the problem might me somewhere else. Please try to reach your web site using the IP address instead of the domain name and report back. I suppose your ISP is redirecting the domin when the site is down and Firefox is keeping the DNS record. When you start Sea Monkey or a new profile, the DNS record is clean, so it queries your ISP and it returns the correct address, since the site is live.

You could try to use an add-on like [DNS Flusher](https://addons.mozilla.org/en-US/firefox/addon/dns-flusher/) or use a different DNS provider, like OpenDNS or Google DNS.

:KS DNS flusher ROCKS. Thanks for the suggestion! :KS

---

### Post by lovinglinux on 2011-12-19
> **Ian Clark said:**
> :KS DNS flusher ROCKS. Thanks for the suggestion! :KS

You are welcome. I am glad it worked.

---

