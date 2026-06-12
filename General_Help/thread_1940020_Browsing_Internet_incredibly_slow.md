---
title: "Browsing Internet incredibly slow?"
date: 2012-03-12
forum: General Help
---

### Post by Spewed on 2012-03-12
I have a dual boot of Ubuntu 11.10, and Windows 7. My browsing on Windows 7 is super snappy, and quick at all times. For some reason it's not that way with Ubuntu? Ubuntu is my favorite OS by FAR, so I'd hopefully I can get this issue fixed. 

I have both Google Chrome and Firefox installed on Ubuntu. Both of them perform pretty terrible. Google Chrome struggles to even load up the home page. Then if you want to switch from say Facebook to something like Texasrangers.com or Gamespot.com it sits and sits and sits for a while. 

I have a 3 meg DSL connection, and my specs are as follows.

4GB Patriot Xtreme Viper Ram 1600
GTX 570 Superclocked
Overlocked core i5 2500k processor
windows 7\ubuntu 11.10. 

Can anyone help with this? I installed the video drivers for my GPU. A side note, I have not installed any motherboard drivers in Ubuntu, I have in Windows though. Would this be my issue?

Edit: After clicking "Submit" on this thread it took around a full minute for it to finally actually submit my new thread.

---

### Post by gunksta on 2012-03-12
Are you using a wireless connection?
What is your connection speed in Ubuntu?
Is Firefox slow to load? 
Are other apps slow?

Try opening the "System Monitor" when you are browsing the web. Are you getting a CPU or memory spike? If so, who/where/when?

Not trying to be annoying, but there isn't enough information in your post for anyone to even hazard a guess as to what could be the problem. 

What is the computer make/model? If you try googling for it and linux compatibility, you may find that there is a known problem with this system and (hopefully) a workaround.

I would try enabling the proprietary drivers for the graphics card. I don't know why that would cause firefox/chrome to run dirt slow, but who knows. I know firefox is trying to do more with direct graphics rendering, but I would assume this is disabled if you don't have the necessary drivers.

---

### Post by Spewed on 2012-03-12
> **gunksta said:**
> Are you using a wireless connection?
What is your connection speed in Ubuntu?
Is Firefox slow to load? 
Are other apps slow?

Try opening the "System Monitor" when you are browsing the web. Are you getting a CPU or memory spike? If so, who/where/when?

Not trying to be annoying, but there isn't enough information in your post for anyone to even hazard a guess as to what could be the problem. 

What is the computer make/model? If you try googling for it and linux compatibility, you may find that there is a known problem with this system and (hopefully) a workaround.

I would try enabling the proprietary drivers for the graphics card. I don't know why that would cause firefox/chrome to run dirt slow, but who knows. I know firefox is trying to do more with direct graphics rendering, but I would assume this is disabled if you don't have the necessary drivers.

Proprietary graphics card drivers are enabled. This was among the first things I did when installing Ubuntu. I build the computer myself sometime ago. The specs again are:

Intel® Core&#8482; i5-2500K CPU @ 3.30GHz × 4 
GeForce GTX 570/PCI/SSE2
OS type : 64-bit
Motherboard: Biostar Tseries TZ68A+

Both browsers run equally slow. Other apps like I said load fast, everything else is very slow. The browsing is the only problematic figure at the moment.  Here is my connection speed as per Ethtool, and yes I am on a WIRED connection, not wireless.

It says 100Mb/s

Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                             100baseT/Half 100baseT/Full 
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup

My CPU's idle specs are: 

Core 1 idles anywhere from 8%-19% usage
Core 2 idles anywhere from around the same.
Core 3 idles anyhwere from 0%-6%
Core 4 idles anywhere from 0% to 6%

All of this is while I type to you. Now lets browse the web and see what happens. I enter in Google to start with, no noticable spike doing that, however it takes over a 1 minute for it to actually only say "Problem loading page"<< This is a frequent problem. So I hit refresh, it jumps to 34% for a split second, then goes right back down and loads fairly quickly the Google interface, yet continues to say it's loading for a while. Lets try another site. I'll do Gamespot, it loads quickly, no spike whatsoever. Switching from there to "Weather.com", no load spikes, and takes forever to load yet again. (a minute goes by, still not fully loaded) cancelling the load and switching to "Texas Rangers" site. Loads fairly quikcly, with no spikes anywhere.  Switching to Dallas Cowboys it goes all the way up to 50% on my CPU load, but my memory load stays the same, and it takes again forever to load. 

My ram usage is however staying around 29% usage while browsing\typing this message.(which seems fairly high)

I have compiz and have animations enabled, and I'm using GLX dock, but everything was slow before either of those were working on my machine. I have also noticed the list of my processes is quite large. Is it worth it to post them as well?

I logged out to close out everything that I had open and start fresh. Before opening anything I start up system monitor my CPU usage never goes above 9% on core one. As you can imagine it's lower on the other cores, and my RAM stays around 20% usage. I pull up Firefox, and my usage stays around 8% again, as well as my ram hovering around 20%

---

### Post by Spewed on 2012-03-12
bump

---

### Post by gunksta on 2012-03-13
Sorry for the delay. Was eating dinner.

Don't worry with posting all of the other processes. Linux systems tend to try and max ram usage for speed purposes so I wouldn't worry about the relatively high RAM usage.

I missed the part about being on 64-bit.

You're right. This is some odd behavior. I'd like to blame your connection, but you already said Windows works well when browsing the web. Because, honestly, this sounds like some sort of weird DNS or connectivity problem. Not a "Linux" problem.

Another question. Since you are using a wired connection, I want to  compare your network settings in Ubuntu to those in Windows where things allegedly work better. :D Hit the button  that looks like an up/down error on your top menu bar -- the one that  lists your connections. Go down to "Edit Connections..."

There should be, under the "Wired" tab, some information. I don't need to know your MAC address, but everything else I'd like to see.

MTU - 
802.1x Security - 
IPV4 Settings - 
IPV6 Settings - 

Another thought - You said your connection is 100 MB/S. Is this an older router? 

This is a shot in the dark, but perhaps you need to disable IPV6 on your network. I'm wondering if it might somehow be causing trouble. Could be an old router fighting with IPV6.

---

### Post by Spewed on 2012-03-13
> **gunksta said:**
> Sorry for the delay. Was eating dinner.

Don't worry with posting all of the other processes. Linux systems tend to try and max ram usage for speed purposes so I wouldn't worry about the relatively high RAM usage.

I missed the part about being on 64-bit.

You're right. This is some odd behavior. I'd like to blame your connection, but you already said Windows works well when browsing the web. Because, honestly, this sounds like some sort of weird DNS or connectivity problem. Not a "Linux" problem.

Another question. Since you are using a wired connection, I want to  compare your network settings in Ubuntu to those in Windows where things allegedly work better. :D Hit the button  that looks like an up/down error on your top menu bar -- the one that  lists your connections. Go down to "Edit Connections..."



There should be, under the "Wired" tab, some information. I don't need to know your MAC address, but everything else I'd like to see.


MTU - 
802.1x Security - 
IPV4 Settings - 
IPV6 Settings - 

Another thought - You said your connection is 100 MB/S. Is this an older router? 

This is a shot in the dark, but perhaps you need to disable IPV6 on your network. I'm wondering if it might somehow be causing trouble. Could be an old router fighting with IPV6.

The router is one provided by my Internet company, it's an old 2wire router. It performs fine on everything else, including things like Xbox, DVR, etc. 

MTU: Automatic
802.1x Security is not enabled. However, if I do enable it my authentication would be MD5
IPv4Settings: Automatic DHCP(require IPV4 addressing for this connection to complete
IPv6 I set to ignore previously.

Settings are the same in that of Windows.

---

### Post by Spewed on 2012-03-13
Also with Chrome I sometimes get the error "He's dead, Jim!" Either chrome ran out of memory or the process for the webpage was terminated for some other reason. To continue, reload or go to another page. 

As to where Firefox it just wont load.

---

### Post by gunksta on 2012-03-13
I was really hoping the IPV6 stuff would be the ticket. Oh well.

Run these in Ubuntu and Windows.

[http://www.pingtest.net/](http://www.pingtest.net/)
[http://speedtest.net/](http://speedtest.net/)

I'm really trying to find something that confirms that this is a connection issue. I don't have any idea what the connection issue might be, but I'm trying to confirm that for some reason, Ubuntu is establishing a slow connection.

---

### Post by Generalunderpants on 2012-03-13
I too have the exact problem. I just installed Ubuntu today and at first Firefox was working just fine. About a couple of hours ago however, my speeds dropped to abysmal levels.  The weird thing is, when I download something, say with apt, my speeds are perfect. It's just with the browsing. When I use the internet with my Windows partition, I, like the OP, have no issues. Could this be an update problem or something?

---

### Post by gunksta on 2012-03-13
Hmmmm. That is interesting. I rather hope I do not see this behavior.

Here is a test (not of the emergency broadcast system).

I'd like you to download the same file, twice. I know. There sounds like more fun than poking myself in the eye.

[http://www.thinkbroadband.com/download.html](http://www.thinkbroadband.com/download.html)

[http://www.thinkbroadband.com/download.html](http://www.thinkbroadband.com/download.html)

Pick a couple of these files and try downloading them with firefox/chrome/whatever. Watch it for a couple of minutes and see, on average, how fast you are  downloading. Feel free to kill the connection after a couple of minutes.

Then, open a terminal and try to download one of these files. Repeat the watch routine. That gives us a reasonably objective way to measure/compare network capacity with and without the browser.

The problem is, if the browser is messed up, I have no idea why or even how to approach this. I suppose you could both try installing Epiphany or something.

One other thought - you aren't running your browser connection through a proxy are you? Go to System Settings --> Network and look at "Network Proxy". Make sure this says none (unless you know for a fact that you need one). If you change anything, be sure to hit apply system wide.

To look at Firefox, go to Preferences --> Advanced --> Connection (Settings) and make sure it is using the system wide settings . . . or none.

---

### Post by TBABill on 2012-03-13
I had these same issues on 11.10. Randomly my speeds would drop to the point where it appeared the machine just was struggling to manage loading sites. Speed tests (speakeasy) would show down as low as 200Kbps on a 12Mbps service. I tried every setting I could for my Atheros wireless and the only thing I did not try was using wicd instead of network manager.
 
Instead of fighting it I just installed 12.04 beta 2 the other day and it's blazingly fast compared to 11.10 speeds both within the desktop and online. World of difference but the problem is that I still do not know the root cause of the issue. Chrome, Chromium and Firefox were all affected the same way so I leaned away from it being a browser issue.

---

### Post by gunksta on 2012-03-15
That is an interesting post.

First -- I REALLY don't understand why Ubuntu would suddenly start browsing slowly. I'm not saying I don't believe you. I do. I just don't get the "why" part.

Second -- I am feeling the itch to upgrade. Are updates still coming in fast and furious?

---

### Post by cssutto on 2012-03-16
I developed a similar problem today.

I have no idea why other than I made several upgrades that Synaptic told me I needed.

ubuntu 10.4 on a Thinkpad T60p.

The same machine I have used now for 4 years or maybe more.

It is so slow that it is driving me nuts.  It will load a page and then either refuse to load a link from that page or will take forever to load the link.

I believe that it is a bug in the foxfire update, which was included with the many others.

I have a new HP Pavillion with everything on it on the way so I do not want to completely clean this machine and start over as I will have enough of that with setting up the new machine, but I did remove foxfire, reboot and use computer janitor to clean up the odds and ends and then reinstalled.

Same thing.  No better.

It loads simple pages like the weather radar and does so reasonably although slower than it once did.

But pages with lots of stuff and links are unbearable.

---

### Post by cssutto on 2012-03-20
I have learned a little more.

My browser loads original pages fairly well.  The difficulty is primarily links.

Links within web sites either do not work or take many minutes and many clicks.

ctrl-R helps in very few instances.

Looking at system resources, the CPU's are running near capacity.

Looking at processes, firefox is the hog.

---

### Post by TBABill on 2012-03-21
> **gunksta said:**
> That is an interesting post.
 
First -- I REALLY don't understand why Ubuntu would suddenly start browsing slowly. I'm not saying I don't believe you. I do. I just don't get the "why" part.
 
Second -- I am feeling the itch to upgrade. Are updates still coming in fast and furious?
 I'm not sure which post you were referring to being interesting, but in my situation it started from initial install so I couldn't point to an update throwing it off. I still can't say why, but Mint 12 does the exact same thing while Ultimate Edition 3.2, also based on 11.10, does not exhibit this behavior. The only difference is in UE I am using the Gnome "classic" DE (2 panels, looks similar to Gnome 2), in Mint I was using Cinnamon and in Ubuntu I tried Unity, Xfce (xubuntu-desktop), LXDE (lubuntu-desktop). None of them performed well in Ubuntu 11.10, but installing the beta was a world of difference. And it can't be the kernel because UE 3.2 uses the same kernel as Ubuntu.
 
Beats me what the problem is, but I did lots of installs just to confirm it rather than making assumptions in a live environment. 12.04 had freezing issues with the catalyst driver (12.2, same as I used in 11.10, Mint and UE 3.2 right now) so I moved to UE 3.2 full time for now pending performance/CPU usage improvements in Cinnamon.

---

