---
title: "ubuntu 9.10 internet not working"
date: 2009-10-29
forum: General Help
---

### Post by TRUJohn on 2009-10-29
Hey i am trying to connect to the internet but it wont let me, i don't get any error or nothing just wont connect, i install ubuntu 9.04 and everything is good, does anyone have any idea?

---

### Post by Giblet5 on 2009-10-29
Right-click the network icon near the upper-right corner and enable networking. Wait a second to see if you get a "Connection Established" message. If not, then left-click the icon and see if there's an available connection. Select one.

Did that do it?

---

### Post by TRUJohn on 2009-10-29
Nope i set up a DSL connection and its not connecting, its like something its blocking it.  Just wont connect and i am only having this problem in ubuntu 9.10

---

### Post by HolleywoodDesigns on 2009-10-29
Same here, 9.10 64bit. It worked fine with the 64bit RC. but now it's dead with the final.

---

### Post by Giblet5 on 2009-10-29
> **TRUJohn said:**
> Nope i set up a DSL connection and its not connecting, its like something its blocking it.  Just wont connect and i am only having this problem in ubuntu 9.10

Did you set it up manually?

I just noticed, over on a test system, that having edited a static IPv4 network connection and hitting the "Apply" button, the DHCP connection was dropped...and that was it. I had to open those settings back up and hit "Apply" again before it worked.

Don't EVEN get me started on Network Manager. There's very little documentation, the gnome applet has an interface that would make Mother Theresa scream obscenities and gut puppies...

On laptops, I remove it, then install wicd. It just works.


It's worth noting that certain network chip vendors don't open-source their drivers and these get tossed in with the restriced hardware drivers. So, check that via System -> Administration -> Hardware Drivers. If there's a network driver there, activate it (if you can)...

---

### Post by TRUJohn on 2009-10-30
I went to system -> administrator -> then upgrade manager and i upgraded to version 9.10 i restarted the PC and it wont work.  So i attempted to set the connection again and it simply would not connect, so i thought it was a problem from my ISP but nope it was the ubuntu upgrade that did all the damage soooooooo how do we fix it because nothing is working

---

### Post by Hemanth S A on 2009-10-30
I have a similar problem. I setup the wired connection and am unable to browse/download packages.

I'm able to get ping replies from google.com or any other site. But I'm not able to use the internet for anything else.

Its working fine on windows. I have this problem since I installed 9.10 a few hours ago.

I'm using Intel's DX58SO motherboard, so I guess a problem with the driver is also a possibility. I'd like to know if it is just a problem with my board or with the new release.

---

### Post by Ubnuut on 2009-10-30
> **Hemanth S A said:**
> I have a similar problem. I setup the wired connection and am unable to browse/download packages.

I'm able to get ping replies from google.com or any other site. But I'm not able to use the internet for anything else.




Exactly the same problem here... First time I experience something like this with a new Ubuntu release. Just with 9.10, Ubuntu 9.04 works fine.

---

### Post by cariboo on 2009-10-30
There seems to be a problem with dns. You should be able to fix the problem by right clicking on Network-Manager in the top panel and selecting edit connection. Next click the IPv4 Settings tab and select:

```
Automatic (DHCP) address only
```

From  the method drop down. In DNS servers teat box enter your isp's dns addresses, then click apply. You should be asked for your password, you Will get a notification that your cable is disconnected, give it 3o seconds (or less), it should create a connection, and you should be good to go.

---

### Post by James4 on 2009-10-30
I'm having the same problem here.
in jaunty my dsl connections worked just fine but in karmic it's become a real pain.
I tried evrything but it's not working anyway.

---

### Post by James4 on 2009-10-31
anybody knows any solution?
I'm kinda disappointed. what a waste upgrading to 9.10!

---

### Post by Egi_Power on 2009-10-31
Hi!

I hope you will solve your problem soon.

I'm thinking to upgrade to 9.10. At the moment I use Hardy, but it slowed down by time.
Anyway, I'm on the 9.10 LiveCD. From here my internet works. Did it work for you also from the LiveCD and just stoped working after you installed it?

Take it easy.

Egi_Power

---

### Post by James4 on 2009-10-31
well, I had to use pppoeconf command after all.
I think that'd be good temporary solution till a patch comes out.

---

### Post by coalitians on 2009-10-31
I have the same problem . I can ping google, initially firefox didn't work until i changed disable ipv6= "true " in about:config in firefox. 
But still update manager , or empathy not working.....
I changed ipv6.disable=1 in grub but still no success...
any help........

---

### Post by coalitians on 2009-10-31
The problem is with dns. firefox uses different dns hence it worked in ipv4.

Go and edit[SIZE="3"] [COLOR="black"]**network connections -->edit (your working connection)-->ipv4 setting -->change to automatic dhcp address only -->then type dns servers ip address ,,i used open dns 208.67.222.222**[/COLOR][/SIZE] , then save and refresh ur network connection...

still my wireless not working....:p

---

### Post by James4 on 2009-10-31
has anybody reported this bug?

---

### Post by Ubnuut on 2009-11-01
> **cariboo907 said:**
> There seems to be a problem with dns. You should be able to fix the problem by right clicking on Network-Manager in the top panel and selecting edit connection. Next click the IPv4 Settings tab and select:

```
Automatic (DHCP) address only
```

From  the method drop down. In DNS servers teat box enter your isp's dns addresses, then click apply. You should be asked for your password, you Will get a notification that your cable is disconnected, give it 3o seconds (or less), it should create a connection, and you should be good to go.

Yes, I can confirm it is a DNS issue in Ubuntu 9.10. After manually configuring DNS with ISP's DNS, problem was solved. I have 2 ISP's, and it is only with one ISP that I have the DNS issue in 9.10, when connecting modem to other ISP I have no problem. 

Must be some bug in 9.10, cause in 9.04 I don't have this issue.
Looking at the few entries in this thread there are hopefully not too many people encountering this issue.

Would still be good to file a bug report if nobody hasn't done so yet.

---

### Post by TBeholder on 2009-11-01
I got the same bug.
Apparently, it was lack of DNS: traceroute in network tools failed to find a target even with disabled firewall. Firefox failed to see anything, but worked via squid (extra DNS set in squid config). :)

I saved old config files when updating packs asked for overwrite, so i see that 9.10 sets in **/etc/NetworkManager/nm-system-settings.conf** has ```
[ifupdown]
managed=false

``` ...and my old config has "true". Fixed, rebooted, checked that the proper connection is set in NetworkManager (nm-connection-editor) as auto-used - everything works.

---

### Post by jiapei100 on 2009-11-01
Facing the same problem right now.
No matter how I edited Network Connections, still can't wake up any wireless network list. Namely, always 

Wired Network
disconnected
Wireless Network
disconnected


There was no such problem when using Ubuntu 9.04

Cheers
JIA

---

### Post by abhilash82 on 2009-11-01
I also have a similar problem. Can someone help me out on this?

[http://ubuntuforums.org/showthread.php?t=1309419&referrerid=341990](http://ubuntuforums.org/showthread.php?t=1309419&referrerid=341990)

---

### Post by tal13sin on 2009-11-30
Similar problem here too.  Can get my wireless to connect to the network but no access to websites.  I'll try the DNS changes suggested tonight, figures crossed that will solve it.

---

### Post by tal13sin on 2009-12-01
Fixed mine by changing the encryption on my wifi from WPA/WPA2 to WPA2 only.

---

### Post by avengerxp on 2010-02-21
ubuntu 9.10 user here....after facing with a virus in xp i tried ubuntu,

it autoloaded all my drivers and etc!:D

but although my mobile broadband connection is installed and shows it's connected, Firefox doesnt see it!

any help pleeeze!

---

### Post by 3rdalbum on 2010-02-21
> **avengerxp said:**
> ubuntu 9.10 user here....after facing with a virus in xp i tried ubuntu,

it autoloaded all my drivers and etc!:D

but although my mobile broadband connection is installed and shows it's connected, Firefox doesnt see it!

any help pleeeze!

Please don't bump old threads; please start a new thread.

You might need to disconnect and reconnect. Some modems are flaky under Ubuntu 9.10 and will only occasionally work. Try 9.04 or 10.04 alpha.

What happens if you try to ping Google:

```
ping www.google.com
```

---

### Post by Tom55 on 2010-04-11
I think I've stumbled upon a solution to my internet access problem with Ubuntu 9.10.

My internet connection is shared with a number of pc's via a hub and the Ubuntu 9.10 pc needs a static IP address.  However if I configured it with one the other pc's on the LAN can see the Ubuntu 9.10 pc but it doesn't have access to the internet.

I added the dns to the network connections setting and it didn't resolve the problem.

Then in the IPV4 Settings window I noticed a small tick box in the bottom left corner named 'Available to all users'  I selected it and click Apply.

Ubuntu discarded my manual IP setting and defaulted to Automatic but it did give me access to the internet

---

### Post by cguwilliams on 2010-12-23
I was having the same problem with 9.10. The method from cariboo907 worked! I had to create a new connection, and then edit IPv4 settings from there.

---

