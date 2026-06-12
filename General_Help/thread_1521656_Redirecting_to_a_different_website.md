---
title: "Redirecting to a different website?"
date: 2010-07-01
forum: General Help
---

### Post by naminem on 2010-07-01
I'm using ubuntu 10.04 64bit.

The problem I am having is sometimes ubuntu just keeps redirecting me to a different website.

For example, I type in yahoo.com and on the URL it shows yahoo.com, but it goes to google.com or some other website. This isn't a browser problem because when I have this problem, I try it on other browsers I have and it keeps redirecting me to that other site. Keep in mind that this does not happen every time. But sometimes ubuntu just bugs out on me and it starts redirecting.

Is it a problem with some DNS thing? Is there a way for me to fix this problem without having to restart?

The problem is usually fixed by itself. All I have to do is wait a bit.

Maybe ubuntu somehow changes my router settings? o.o;

This does not happen to me when I'm using Win 7 64bit.

---

### Post by naminem on 2010-07-01
Please I need help T_T

---

### Post by mkvnmtr on 2010-07-01
This is not a Ubuntu problem. The operating system can not redirect you. I  believe it is a DNS problem where you are redirected. I believe in Firefox there are add-ons to stop redirection but I have never had to use them.

---

### Post by WorMzy on 2010-07-01
The operating system can redirect you, but you need to manually edit /etc/hosts to get it to do it. If you've been messing with /etc/hosts recently, then undo your changes and see if the problem persists. Otherwise, call your ISP, it's likely that they've got a problem at their end.

---

### Post by naminem on 2010-07-02
> **WorMzy said:**
> The operating system can redirect you, but you need to manually edit /etc/hosts to get it to do it. If you've been messing with /etc/hosts recently, then undo your changes and see if the problem persists. Otherwise, call your ISP, it's likely that they've got a problem at their end.

I haven't touched my hosts file. These are the contents of it

127.0.0.1	localhost
127.0.1.1	my-laptop
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Well, I would like to believe it's my ISP's problem but like I said, things work perfectly fine with my win 7 desktop. The problem only occurs on this laptop with a 64bit ubuntu 10.04.

If it is a DNS problem, is there a way to reset my DNS cache on my computer or something?

---

### Post by philinux on 2010-07-02
> **naminem said:**
> I haven't touched my hosts file. These are the contents of it

127.0.0.1	localhost
127.0.1.1	my-laptop
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Well, I would like to believe it's my ISP's problem but like I said, things work perfectly fine with my win 7 desktop. The problem only occurs on this laptop with a 64bit ubuntu 10.04.

If it is a DNS problem, is there a way to reset my DNS cache on my computer or something?

Hosts file is spot on. Why not try open dns look up.
Attached is settings.

---

### Post by Rubi1200 on 2010-07-02
As philinux suggested changing to a different DNS server might help.

Google DNS is also a possibility:

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

Also, try clearing the cache in Firefox.

Tools > Clear Recent History > Everything

---

### Post by naminem on 2010-07-03
> **Rubi1200 said:**
> As philinux suggested changing to a different DNS server might help.

Google DNS is also a possibility:

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

Also, try clearing the cache in Firefox.

Tools > Clear Recent History > Everything

Hello. I just tried Google DNS. I am still having the same problem though. =(

The clearing cache doesn't really help since I'm not just having the problem in firefox. I can switch to any other browser and I'll have the same problem.

I'm still thinking it's an OS problem. Maybe the OS is fiddling with my router settings (highly doubtful though)?

No one else is having this problem?

Should I reinstall ubuntu?

Oh by the way, sometimes when I have this problem, typing www. infront of the URL fixes the problem. For example, if google.com redirects me to some page, I can try typing [www.google.com](www.google.com) and it directs me to the right page. 

And the problem fixes itself if I wait a while.

---

### Post by naminem on 2010-07-04
Oh and it seems to happen the most when I am trying to access 2 or more websites at once.

For example, when I start firefox, I type in the URL of a site, open a tab, type in another URL, repeat.

Do you think that has anything to do with the problem I'm having?

---

### Post by dino99 on 2010-07-04
im using firefox addons: noscript & adblock; but your issue seems to be custom issue or illusion

---

### Post by naminem on 2010-07-05
I do not use any addons.

---

