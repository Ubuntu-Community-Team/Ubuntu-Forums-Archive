---
title: "why is my internet so SLOW ..BUTT SLOW!"
date: 2006-03-30
forum: General Help
---

### Post by Rorgy on 2006-03-30
i have high speed...and the other computer in my hosue is running xp(hurl) and its internet works like it should...fast....the pages load fast, and everything works

on my ubuntu i am running firefox, and it takes like 30seconds++ to load a page, and then web sites with extra stuff on them (like my space profiles) it takes forever to scroll down a page and not everythuing works.
i get an error that says, DOCUMENT CONTAINS NO DATA...alot
and sometimse when running firefox if i am doing to much at once, all firefox windows will close without warning

do u need more info?


what is the easiest way to fix this..

if its nothing to do with my internet is it because i dont have enough ram?

---

### Post by frodon on 2006-03-30
You could try swiftfox if you have an AMD processor :[http://ubuntuforums.org/showthread.php?t=142798](http://ubuntuforums.org/showthread.php?t=142798)
And you could try to disable ipv6 : [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by Data Doctor on 2007-08-10
If turning off IPv6 fails, try this:

Ubuntu is having difficulty with DNS because of miscommunication with your router (related to wrong ports).

Establishing a direct DNS connection solves the problem. No need to disable IPv6!

1. Find your DNS servers. You may need to check your router settings (usually 192,168.1.1 or 192.168.0.1). Look for a status tab, or similar with the current DNS information. Write down your DNS servers (x.x.x.x & x.x.x.x).

You may wish to back up your dhclient.conf file at this point. In the Terminal, type:
cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.bak

2. Enter these DNS servers directly in your dhclient.conf file:

sudo gedit /etc/dhcp3/dhclient.conf

You should see your dhclient.conf file displayed (with text in it). Add two lines to the end:

supersede domain-name-servers x.x.x.x,x.x.x.x;
prepend domain-name-servers x.x.x.x,x.x.x.x;

The x's represent your DNS server IP addresses that you found in Step 1.

Save your dhclient.conf file, close gedit and return to the Terminal.

Now restart your DNS lookup with (assuming eth0 is your connection to the router):

sudo ifdown eth0 && sudo ifup eth0

You should immediately experience an improvement in your Internet speed.

After I updated Dapper, pages loaded very slowly until I made these changes.
I researched the solution on [https://forum.bytemark.co.uk/viewtopic.php?pid=1790](https://forum.bytemark.co.uk/viewtopic.php?pid=1790) as well as other Ubuntu forum entries.

---

### Post by HermanAB on 2007-08-10
Test your DNS server response times using 'dig' and put the fastest one first in /etc/resolv.conf.

Cheers,

Herman

---

