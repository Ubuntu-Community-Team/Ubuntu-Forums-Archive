---
title: "Desperate! Please help!"
date: 2012-03-28
forum: General Help
---

### Post by wordmaster on 2012-03-28
I am suddenly getting a notice that my system administrator has blocked me from going to various (nearly all) sites. 

It has a Prime Mobile icon showing and
the url that shows up is
[https://bpb.opendns.com](https://bpb.opendns.com)

Any idea of what is going on? I can't go anywhere on my browser (firefox). I am having to send this on my wife's windows computer. Please Help!

---

### Post by wayover13 on 2012-03-28
Um, do you have an account with opendns? Or do you just use their name servers for domain resolution?

James

---

### Post by wordmaster on 2012-03-28
I don't knowingly use their servers at all.

---

### Post by wayover13 on 2012-03-28
Seems to me your domain name resolver is set to opendns. That could be something configured on your computer, or something configured upstream from you (your router, perhaps your ISP, etc). What sort of internet connection do you have? Did you ever enter any DNS information into your system (usually in /etc/hosts, if memory serves)?

James

---

### Post by uRock on 2012-03-28
> **wordmaster said:**
> I don't knowingly use their servers at all.

Do you have admin privileges to your system?

---

### Post by mikewhatever on 2012-03-28
Can you provide some info about your internet connection. Are you part of a larger network like a company or university campus?

---

### Post by wordmaster on 2012-03-29
Just a simple home connection. My wife's windows computer is hooked to the same router and it is what I am using now. Hardwired, not wifi on both. 

I do have admin rights on my computer.

How can I get in to check the dns settings and change them?

I normally never have to do that, the dsl provider randomly assigns ip's and  I never access dns server settings at all.

---

### Post by wayover13 on 2012-03-29
Mmm, I was wrong. The relevant file for DNS resolution on your local machine should be /etc/resolve.conf . What's the content of that file on your machine?

James

---

### Post by wordmaster on 2012-03-29
I rebooted and will have to wait as it is checking disks.

HOwever, I have an ASUS motherboard with Express Gate on it which allows you to get on the net without starting an operating system. It works fine, I get on whatever I want with no problem. Problems start after ubuntu boots. 

BTW, this is all very new. 2 hours ago there was no problem. I have loaded no new programs or anything like that.

---

### Post by wordmaster on 2012-03-29
resolve.conf shows

search 208.67.222.222 209.67.220.220
nameserver 208.67.222.222
nameserver 208.67.220.220

---

### Post by uRock on 2012-03-29
Edit your profile in Network Manager. Use 8.8.8.8 or your ISP's default. The DNS you have right now is OpenDNS's [https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=208.67.222.222%3F](https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=208.67.222.222%3F)

---

### Post by wayover13 on 2012-03-29
Yep, those are opendns name server IP's alright. Are you sure someone in your household didn't set up an opendns account and configure it for some kind of filtering? Seems to me something along those lines is going on. Of course you could always get rid of those entries and just use your ISP's (or router's--which may also come from your ISP) name servers.

James

---

### Post by wordmaster on 2012-03-29
Nope, no one but me uses that computer. 

If I set for automatic DHCP will that do it?

---

### Post by wordmaster on 2012-03-29
Yep, changing to auto DHCP got me going, but does anyone have any idea what caused it to change in the first place?

Thanks to all for your help.

---

### Post by wayover13 on 2012-03-29
> **wordmaster said:**
> Yep, changing to auto DHCP got me going, but does anyone have any idea what caused it to change in the first place?
So you had your machine set up for static network addressing? You never did supply much detail about your network, and with such sketchy information it's nearly impossible to diagnose this situation. For example, I'd guess you connect to the internet through a router, since you said you used another computer in your house to post a message in this thread. But you never stated whether or not a router is involved, and without knowing that, as well as not knowing how the router is configured and who has access to it, only guesses can be made about the matter. Also, saying you have "just a simple home connection" doesn't tell us much: does that mean it's DSL/ADSL, cable, on some cellular network, or what? Without more specific information about those sorts of things all we could do is make semi-educated guesses about how you ended up with opendns name servers configured as your resolvers.

James

---

