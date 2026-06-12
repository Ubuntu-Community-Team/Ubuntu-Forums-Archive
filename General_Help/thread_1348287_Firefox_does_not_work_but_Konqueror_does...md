---
title: "Firefox does not work but Konqueror does.."
date: 2009-12-07
forum: General Help
---

### Post by cezzar on 2009-12-07
Hi All;
I am an Intrepid 8.10 user. At home; I can use Firefox (3.0) without any problem. But at work; Firefox almost does not work (well, it takes few minutes to open a page). But I can use Konqueror without any speed problem.

I made a search on this problem, and have disabled ipv6 accordingly; to make my firefox function as usual also at work; but it did not help..

Does any of you have any comment? Thanks A LOT in advance..

---

### Post by lovinglinux on 2009-12-07
If disabling ipv6 doesn't help, then it looks like a DNS issue. You could try [this](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/), which will store the DNS info of sites you visit into Firefox database, so the next time you try to open it, it won't be necessary to query the DNS server again and it will load faster.

 Also check Firefox connection settings.

---

### Post by cezzar on 2009-12-09
[COLOR="Red"]lovinglinux[/COLOR]; thanks A LOT for your reply..

I have applied the changes given in the link you provided; and loading pages have become very fast; so it worked..

But; every morning I have the same slowness again. Could it be that every day the stored DNS info is deleted? (I use the same laptop at home in the evenings; and I have never experienced this problem at home. Could it be that a different connection clears all DNS info? )

Also, as far as I have understood; every new website I haven't visited before will take still a while with this solution.. Isn't there a way to make Firefox work like Konqueror? I mean, the same system and Konqueror does not experience any problem.. So, shouldn't there be another way to solve this problem?

Thanks a lot again for the help..

---

### Post by lovinglinux on 2009-12-09
> **cezzar said:**
> I have applied the changes given in the link you provided; and loading pages have become very fast; so it worked..

So, for some reason Firefox is taking too much time to contact the DNS server. This is usually a problem on the server itself, but it's strange that Konqueror does not behave the same.

> **cezzar said:**
> Could it be that a different connection clears all DNS info?

I don't think so.

> **cezzar said:**
> But; every morning I have the same slowness again. Could it be that every day the stored DNS info is deleted?

Yes. The DNS info is cached for a limited period. One of the settings of that tutorial is responsible for determining the period the DNS info will cached. You can increase that a little bit. 

Keep in mind that those tweaks are just a workaround for those days the DNS server is slow. You need to figure out why Firefox is taking too much time to contact the DNS server.

You could try to change the DNS servers on your connection and check if you get any improvement. If not, then it could be Firefox's fault.

Try the new [Google open DNS servers](http://ubuntuforums.org/showthread.php?t=1344880). Some people say it is really fast, although it is slower for me (I'm in Brazil).

The IP addresses of Google DNS service are:

[B]8.8.8.8
8.8.4.4[/B]

---

### Post by lovinglinux on 2009-12-09
I have got some DNS related updates today that fixed similar issues on Chromium. Perhaps it will also solve your problem. Update your system and check if the problem persists.

---

### Post by cezzar on 2009-12-16
Problem still persists with my updated system..
I did not try Google DNS server  since basically I read in the link you provided that it is not safe to use it. And, I personally do not know the function of DNS server; that's also why I did not want to change the related settings...

If Konqueror works without any problem, there must be a simple way to make Firefox too, I think...
Anyway; I would like to thank you again VERY MUCH for your interest in my problem and for the time you spent in writing replies.. thanks..

---

### Post by lovinglinux on 2009-12-16
> **cezzar said:**
> Problem still persists with my updated system..
I did not try Google DNS server  since basically I read in the link you provided that it is not safe to use it. And, I personally do not know the function of DNS server; that's also why I did not want to change the related settings...

If Konqueror works without any problem, there must be a simple way to make Firefox too, I think...
Anyway; I would like to thank you again VERY MUCH for your interest in my problem and for the time you spent in writing replies.. thanks..

A DNS server is responsible for translating web addresses into IP numbers. The www address is easy to remember, but your browser actually connects to IP numbers, not www addresses. So, whenever you type a www adddress, the browser sends a query to the DNS server, that converts that name into an IP number so you can connect to it. 

Is not unsafe to use Google DNS. There are some concerns about privacy, but it doesn't matter what DNS server you use, someone will always know every web address you visit.

---

### Post by cezzar on 2009-12-21
Aha! So, that is what DNS Server is.. that simple! Thanks for the info..

I implemented GoogleDNS, still same firefox problem..

My workaround for the problem is to install Opera; which is a browser way better than Konqueror in terms of functionality; and works very well in terms of speed..

I still find it stupid that Firefox has such a problem.. Anyway; I am happy now :P.. Thanks a lot again [COLOR="RoyalBlue"]lovinglinux[/COLOR] for your helps..

---

