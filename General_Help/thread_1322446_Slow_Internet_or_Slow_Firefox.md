---
title: "Slow Internet or Slow Firefox ?"
date: 2009-11-10
forum: General Help
---

### Post by JimBuntu on 2009-11-10
After my upgrade to karmic, my internet has been extremely slow. Sometimes not even fully loading the page. Both my desktop and laptop are experiencing this. Not even craigslist is loading correctly. I was trying to not have to post this thinking that there was a fix coming but nothing so far. What the heck is the prob?

---

### Post by fluffman86 on 2009-11-10
Grab a jaunty CD and boot from that.  That should tell you if something is up with karmic or not.

Be sure to reboot your cable modem, then your router.  Sometimes that will help.

Also, go to [http://speedtest.net](http://speedtest.net) in both jaunty and karmic on the same computer.

---

### Post by Giblet5 on 2009-11-10
How certain are you that your upgrade completed ... successfully?

Boot from the 9.10 CD. Surf a bit. Still seem slow?

---

### Post by Giblet5 on 2009-11-10
> **fluffman86 said:**
> Grab a jaunty CD and boot from that.  That should tell you if something is up with karmic or not.

Be sure to reboot your cable modem, then your router.  Sometimes that will help.

Also, go to [http://speedtest.net](http://speedtest.net) in both jaunty and karmic on the same computer.

Uh. No it won't. That'll tell him if apples are the same as oranges. I can do that without booting a Jaunty CD. ;)

Boot a 9.10 CD and test your surfability. If it's good, I would backup my data and do a clean install of 9.10...

---

### Post by fluffman86 on 2009-11-10
meh, there's more than one way to skin a cat.

---

### Post by lidex on 2009-11-11
Have you tried using a different browser or bittorrent to see if it is Firefox? Check this [link]("http://ubuntuforums.org/showthread.php?t=1307102")

If not Firefox, I'm +1 for clean install.

---

### Post by lovinglinux on 2009-11-11
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

Also see [Simple Firefox DNS Hacks To Boost Performance](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/)

---

### Post by Minsky on 2009-11-11
I'm using Karmic with the Adobe 64 bit flash player plugin installed in Firefox, and I also suffered fron slow page downloads. I found that disabling ipv6 in Firefox solved the problem for me.

---

### Post by coffeecat on 2009-11-11
> **Minsky said:**
> I'm using Karmic with the Adobe 64 bit flash player plugin installed in Firefox, and I also suffered fron slow page downloads. I found that disabling ipv6 in Firefox solved the problem for me.

That cured the symptoms (in Firefox) but didn't solve the problem. If the IPv6 issue is affecting you it may very well affect other parts of the system that need to access the internet.

The problem could be with your router firmware, your ISP, or - I don't know where. Disabling IPv6 is a good diagnostic test but hardly a solution. You may want to dig deeper. Good luck! :)

---

### Post by Minsky on 2009-11-11
I think that the cause of my problem was that I'm connected to the internet using a usb mobile broadband modem, and that Ubuntu may not support the ivp6 protocol for these modems. I'm basing this on the fact that there aren't any ipv6 settings available for mobile broadband in Network Connections but there is a tab for ipv4 settings. If I'm wrong, I'd be grateful for more info on how to solve this.

---

### Post by coffeecat on 2009-11-11
I have no experience of usb mobile modems, but my understanding is that there are IPv6 protocols, period. Devices either support them, not at all or wrongly.

I was caught with the IPv6 issue some 4+ years ago when I first started using Linux. At that time IPv6 was enabled in most Linux distros but not in Windows XP. Long story short" the problem was solved when I updated my router firmware. The old firmware simply didn't understand IPv6 and was confused by the traffic emanating from Linux - even though my Linux box was trying to access IPv4-address webpages. Pass. :?

That being said, I doubt your problem is really an IPv6 issue per se because IPv6 is enabled by default in Vista, Win 7 and the last three iterations (at least) of MacOSX. That modem just has to work with Vista, W7 and MacOS. So - I wonder if this is an obscure bug with IPv6 implementation in Ubuntu which is only revealed with that particular modem, or is an entirely unrelated bug that is coincidentally bypassed when you disable IPv6 in Firefox.

Sorry - I'm not being much help here. I'm out of my depth and I get the impresssion I'm beginning to burble without making any sense. :wink:

One experiment you might try if you wish. Before I upgraded my old router firmware I found that setting a static IP address in my Linux box and configuring DNS addresses manually got round the problem. I've read elsewhere that the IPv6 issue can interfere with name resolution, so that makes some sort of sense. You could try that but it may not get you much further.

By the way - out of interest - do Update Manager and Synaptic show any delay in resolving IP addresses when you use them>

---

### Post by boz86 on 2009-11-11
> **JimBuntu said:**
> After my upgrade to karmic, my internet has been extremely slow. Sometimes not even fully loading the page. Both my desktop and laptop are experiencing this. Not even craigslist is loading correctly. I was trying to not have to post this thinking that there was a fix coming but nothing so far. What the heck is the prob?

Me, too. Much slower with 9.10 and Firefox than with Vista. Almost like it's "hanging up" and frequently to the point of timing out.

---

### Post by bwdease on 2009-11-11
Ok! I just updated to ubuntu 9.10 to find my internet connection was real slow as well. I searched around and I think I may have stumbled across something here. I found this on another sight, so here goes....
-open firefox
-type "about:config" in the address bar
-click "I'll be careful. I promise."
-in the filter bar type "network.dns.disableIPv6"
-make it "true"
-close firefox and try again.

I noticed a difference right away in my browser. Worth a try for others who are experiencing the same problems. After this change to firefox, It's now normal speed for me. Hope this helps. Good luck!!!
bwdease is online now Report Post   	Edit/Delete Message

---

### Post by johnboy1313 on 2009-11-11
> **JimBuntu said:**
> After my upgrade to karmic, my internet has been extremely slow. Sometimes not even fully loading the page. Both my desktop and laptop are experiencing this. Not even craigslist is loading correctly. I was trying to not have to post this thinking that there was a fix coming but nothing so far. What the heck is the prob?

right after I did my upgrade my internet connection went really slow too, I just did a reset on my modem and renewed my ip and it seems to be going pretty good now. the only site I have a problem with load times now is you tube, but its been working better since the last firefox update I got, Ive also been told opera and chrome run faster to be honest I have not given either a try yet, I might download those now, since I'm thinking about it.

---

### Post by Minsky on 2009-11-11
> **coffeecat said:**
> 

By the way - out of interest - do Update Manager and Synaptic show any delay in resolving IP addresses when you use them>

Any help is welcome coffeecat, gives me new ideas for searching for, or trying a solution. I noticed no difference with delays using Update Manager compared with using it with Jaunty and from what I could gather after having a look in  a few forums, static IP address aren't available for PAYG mobile broadband packages which is what I'm currently using. However.......I've just downloaded the latest updates for Firefox and re-enabled ipv6 support, and the problem seems to have been resolved. :)

---

### Post by coffeecat on 2009-11-11
> **Minsky said:**
> I've just downloaded the latest updates for Firefox and re-enabled ipv6 support, and the problem seems to have been resolved. :)

That's the ticket! Do an update. A problem mysteriously solves itself. Move on. :lol:

---

### Post by johnboy1313 on 2009-11-11
been playing with opera now for about an hour, totally faster! chrome was freezing up on me a lot. i recommend opera highly right now

---

### Post by boz86 on 2009-11-11
> **johnboy1313 said:**
> been playing with opera now for about an hour, totally faster! chrome was freezing up on me a lot. i recommend opera highly right now
Chrome froze on me, too. Not having as much success as you with Opera.

Bummer.

Does Opera have an ad blocker?

---

### Post by Baked- on 2009-11-11
did you try putting these settings in /etc/sysctl.conf

```
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
```


after you do that and save the changes run 
```
sudo sysctl -p
```

I have to use these settings when connected to the network at my office to get normal speeds, but not anywhere else.  Figured id give ya something else to try :P

---

### Post by JimBuntu on 2009-11-21
what is the deal????????

It's not Firefox or Chrome. They are both terribly slow. It's got to be something that changed in Karmic. My Win XP Firefox works fast. I've done all the updates. Still unbelievably slow. Sometimes just times out. This is on two diff computers too.

---

### Post by Kruptein on 2009-11-23
I also have an extremely slow internet connection.
The first weeks after the update to karmic the internet was good,
but 3 days ago it became soo slow! damn
Dissabling ipv6 does not work either
so what is a possible solution
and how can I reset my modem / router without risking the internet will be down on other laptops in the house?

---

### Post by cmfrtblynmb on 2009-11-28
OK guys and girls

Same problem here. I have installed karmic 3 times, tried 64 bit, did every trick with firefox, but no result!

Karmic is so ..king slow. I don't get it

It doesn't matter whether you are updating a repo or using any other browser

It is just slow, painfully slow. 

I can't use this distro. Thanks to karmic, after 2 years I have been trying other distros.

---

### Post by lidex on 2009-11-28
> Thanks to karmic, after 2 years I have been trying other distros.
Jaunty works great for me and I'm staying with it for the time being as I feel no real need to upgrade. You don't *HAVE TO* upgrade every six months if it works for you. What is XP, 7 years old? People are still using it - I'm using it. A six month release cycle is pretty cutting-edge.

---

### Post by john newbuntu on 2009-11-29
I am also on Karmic with 2.6.31-15-generic kernel and firefox is working just fine - blazing fast - even after 8 hours of using the same firefox window and several tabs.  I do not have any add-ons and my firefox version is 3.5.5.  It is straight out of the box and I have not tweaked it.  I also made sure all my software stays up-to-date by using the update manager.  There are several sites out there that speak about tweaking firefox for speed.  Here's one of them:
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

You could also try completely uninstalling it and then re-installing firefox from mozilla's website.

---

### Post by JimBuntu on 2009-12-21
I figured out that my wireless router needed to be updated. It is a Netgear WPN824 version 1. Everything is now fast after the firmware upgrade. This one is now solved for me...

---

### Post by re1n0ut on 2010-02-01
Hello,

I hope this thread won't get closed after it's been solved as I've also been experiencing slow pageloads in Firefox since yesterday, updating Ubuntu and videoconferencing using Skype still works very fast.

I tried both wifi and ethernet connections and both suffer the same issue.
Using multiple tabs in a single FF window will keep my connection speed up to par for some time yet when opening (an) additional window(s) even the most common websites (google) load agonizingly slow (up to 5 mins. per page).
I'm not an expert at this but I do know Firefox tends to eat lots of RAM when opening multiple windows and pages in tabs (it does under Vista and XP).
Using "Systemmonitor" I found that I didn't use that much memory at all and opening new FF windows and tabs kept my memory usage at a constant level.

---

### Post by lovinglinux on 2010-02-01
> **re1n0ut said:**
> Hello,

I hope this thread won't get closed after it's been solved as I've also been experiencing slow pageloads in Firefox since yesterday, updating Ubuntu and videoconferencing using Skype still works very fast.

I tried both wifi and ethernet connections and both suffer the same issue.
Using multiple tabs in a single FF window will keep my connection speed up to par for some time yet when opening (an) additional window(s) even the most common websites (google) load agonizingly slow (up to 5 mins. per page).
I'm not an expert at this but I do know Firefox tends to eat lots of RAM when opening multiple windows and pages in tabs (it does under Vista and XP).
Using "Systemmonitor" I found that I didn't use that much memory at all and opening new FF windows and tabs kept my memory usage at a constant level.

See [this](http://lovinglinux.megabyet.net/?page_id=220#Web-sites-keeps-loading-but-never-show-up-2).

---

### Post by re1n0ut on 2010-02-01
> **lovinglinux said:**
> See [this]("http://lovinglinux.megabyet.net/?page_id=220#Web-sites-keeps-loading-but-never-show-up-2").

Thanks for your reply but that's not it, I'd allready disabled IPv6 as suggested earlier in this thread and that didn't solve my problem. (I've allready found your website before I found this thread searching for a possible solution so your link wasn't new to me either ;) )
I did install two add-ons yesterday "Betterprivacy" and "Cookieculler" I've been using these for quite some time now so I didn't think that would be an issue.
Yet however far fetched it might be I tried disabling Betterprivacy, rebooted (cold start just to be sure) to no avail. Then I disabled Cookieculler, rebooted again, and now I've been surfing at a regular speed for about 20 minutes so it looks like this solved it.
There usually is a delay of 5 to 10 minutes before webpages start to load slower which is rather annoying when troubleshooting this so things might still go wrong.
I'm going to enable IPv6 again and see what that gives, I'll also enable Betterprivacy again if that doesn't change firefox' behaviour than I'll just uninstall Cookieculler for now.


grtz.r

---

### Post by lovinglinux on 2010-02-01
> **re1n0ut said:**
> Thanks for your reply but that's not it, I'd allready disabled IPv6 as suggested earlier in this thread and that didn't solve my problem. (I've allready found your website before I found this thread searching for a possible solution so your link wasn't new to me either ;) )
I did install two add-ons yesterday "Betterprivacy" and "Cookieculler" I've been using these for quite some time now so I didn't think that would be an issue.
Yet however far fetched it might be I tried disabling Betterprivacy, rebooted (cold start just to be sure) to no avail. Then I disabled Cookieculler, rebooted again, and now I've been surfing at a regular speed for about 20 minutes so it looks like this solved it.
There usually is a delay of 5 to 10 minutes before webpages start to load slower which is rather annoying when troubleshooting this so things might still go wrong.
I'm going to enable IPv6 again and see what that gives, I'll also enable Betterprivacy again if that doesn't change firefox' behaviour than I'll just uninstall Cookieculler for now.


grtz.r

[This one](https://addons.mozilla.org/en-US/firefox/addon/5207) works great for me. BTW, I use Better Privacy and Ghostery too. See my extension list [here](http://lovinglinux.megabyet.net/?p=36).

---

