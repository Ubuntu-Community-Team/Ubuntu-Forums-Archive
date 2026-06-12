---
title: "Automatically connecting to wireless (WPA) network on wireless PCMCIA card insertion"
date: 2006-03-28
forum: General Help
---

### Post by mjgumbley on 2006-03-28
How can I get a wireless connection to be set up completely automatically upon insertion of my PCMCIA wireless network card?

I'm using a Belkin Wireless G Notebook PCMCIA card on a WPA network, via ndiswrapper, wpasupplicant, and Breezy. IBM Thinkpad T21 and D-Link DSL-G604T wireless router, if this makes a difference.

If I insert the card, the ndiswrapper driver is loaded, the relevant pre-up commands (iwconfig commands to set the channel) are run, the lights on the card start flickering, but it never finishes making the connection to my network. If I then run the networking utility from the admin menu, select the wireless card, and Activate it, it connects, with no problems. The applet at the top of the screen shows an active connection, and all is wonderful.

Why do I have to manually activate the card? What might I need to add to the relevant config files to get a perfect connection automatically upon insertion of the card?

Regards,
Matt

---

### Post by ronmarley1 on 2006-03-28
Hi Matt,
I had a similar situation.  I installed Wifi-radar, and that does a "nicer" job (I think) of creating preferred wifi network profiles than the Networking tool.  Even though I created different Locations in the network tool, I still had to switch them manually from home and work.  Once I created a profile for home and work in Wifi-radar, my IBM R51 connects at boot automatically, wherever I'm at.  At home, I use WEP, and at work (a public high school), it's an unsecured wireless network.  Wifi-radar can manage both secure and unsecure wireless.  It also has a WPA section, but since I don't use WPA, I'm not sure if it works well.

---

### Post by mjgumbley on 2006-03-28
Hi, thanks for the speedy reply - I'll take a look at Wifi-radar. I don't tend to keep the wireless card in the laptop, since it slows the boot down, attempting to synchronize the time (which doesn't work, presumably because the interface isn't up, due to the problem I'm having here)... I don't particularly need to switch locations. Also, the connection was mostly set up manually, since in Hoary, at least, the tool didn't set up WPA connections.

But if Wifi-radar makes the connection activation easier than the current mouse-intensive route, it'll be worth it!

Thanks,
Matt

---

### Post by mjgumbley on 2006-04-07
I've fixed my original problem, thanks to an earlier post:
[http://www.ubuntuforums.org/showthread.php?t=142430&highlight=activate+insert+pcmcia+wifi](http://www.ubuntuforums.org/showthread.php?t=142430&highlight=activate+insert+pcmcia+wifi)

looks like adding 'map wlan0' and 'auto wlan0' fixed it.

/etc/network/interfaces reads: (lines relating to eth0 removed)

mapping hotplug
        script grep
        map wlan0


# WPAHowto suggests we need wireless-wpa foo here
iface wlan0 inet static
        wireless-wpa foo
        wireless-essid MYNETWORK
        address 192.168.0.40
        netmask 255.255.255.0
        gateway 192.168.0.61
pre-up modprobe ndiswrapper
pre-up iwconfig wlan0 channel 6 rate 11M
up ifconfig wlan0 up
post-down rmmod ndiswrapper

auto wlan0

---

### Post by DavidTangye on 2006-04-07
Gee, I hope this sort of thing is fixed / tidied up in Dapper. If users get autoconnection under windows and not under linux, 3 guesses where 99% will go. Its become very obvious to me that unless this sort of thing is as automatic as it is in windows, very few people will move to linux. Sorting this sort of thing out is way beyond the capability of at least 80% of users out there.

---

### Post by Gus Engstrom on 2006-04-19
David, you got it exactly right! I am a noobie,just installed Ubuntu 5.10 and can't get my wireless card to work. Look at the suggestions in the posts above! I know these guys mean well and are trying, but for me, they might as well be writing in russian. If you are not a hacker this just doesn't work. I don't know what the answer is. I'm going to try my local LUG.

---

### Post by DavidTangye on 2006-04-23
Agreed. I am not going to start grizzling here, but it has become very obvious to me that this whole concept of free/non-profit driven software has serious problems that in my opinion are not probably never going to go away. The free software world is one where nerds get stuff working, often really nicely, but the presentation and documentation is so poor, haphazard, etc, that for the vast majority of computer users, the software will never be adopted. Even with excellent documentation the effort to move from Windows is too great for most. Add to that the lack of easy to find and properly written instructions, help, etc, and for most people it becomes far too hard. Damn pity - I have spent years in Linux, and love using it myself. However I have pretty well decided that it will never be adopted in any numbers to allow me to make any significant income from supporting it. There will never be close to the number of paying customers to make it feasible.

---

### Post by mjgumbley on 2006-04-30
David, (a little off-topic, but never mind) you're possibly right in that Linux will not be adopted by enough "paying customers" to permit you to derive an income for it. Perhaps you might only be able to earn a living from it if you work for a distributor, e.g. RedHat, Canonical, etc.

I've used it for years (remember Beta-Tamu 1.0A, anyone? Yggdrasil Plug'n'Play Linux?) - and it's still my OS of choice. I also use Windows XP and Mac OS X and both are excellent OS's.

Yes, the documentation could be improved (saying this, last time I tried getting Windows working on my WPA network, I had even less success, and with no reasonable diagnostic logs of the failures I encountered, there's no easy way of working out why it fails).

It'll probably never be perfect, but one thing that differentiates Linux from other OS's, for me at least (I'm a software engineer in my day job), is the ability for anyone to improve it.

I've had a problem, above, which others are bound to have. I worked out why things weren't working as I'd like, and have now fixed it. Now I shouldn't have had to mess about with configuration files to fix this, in 2006. So now I have the opportunity to get involved, and make Ubuntu better for everyone.

It's only in this way, gradually, gradually, that we build a better system.

Perhaps, in Edgy + x, there'll be a slightly different network control panel that allows you to set up WPA networks so that they autoconnect upon card insertion, and I might look at it, and see that I did something useful to help others.

I'll never be able to do that with Windows or OS X (unless I get a job at Microsoft or Apple - highly unlikely)...



Gus, can you explain where you are with your network problems, and I'll see if I can help.

---

### Post by cthornhill on 2006-05-04
David,

Just saw the post...ABSOLUTLY RIGHT ON! I have been futzing with WPA off and on for a few months now (I don't have to have it today, but I was hoing to update my network at home to test some security items for clients). I work with Windows software and Linux and I am pushing to get people to Linux and this is a big problem. WEP is not secure - no way, no how. It is a matter of degree, but for most of my friends and clients WEP is not a viable choice. If you run a business or medical operation and have sensitive data WEP is just not for you. 

I know that there is real progress in WPA support under Dapper, but get real - can we really expect everyone to wait for that? And what about servers you can't just go and update? Also, as a matter of credibility how can people expect Dapper to be supported if they can't get such a basic fix under 5.10? Fix what you have, then move the fix to the new code - SOP in large projects for real world customers.

This is not a little thing. This is your access to the net. I just don't know how to get the attention of the powers that be to get them to realize how serious this is. The people running things have to understand that every day companies and individuals buy wireless stuff that is now default configured for WPA (say from all major US phone companies or cable providers), and it all just works out of the box with Windows. Then when you try and get Linux to run with it you fall of a cliff into the dark world of finding the right lib/headers/etc... and compiling who knows what code. 

I can tell you that the compiles are not easy and don't allways work. It is better now than 90 days ago, but this has got to be fixed NOW.

Thanks so much for saying so.

Cecil Thornhill

---

### Post by mjgumbley on 2006-05-08
... and of course, now my network connection has failed. I insert the card, and nothing happens. I'm having to use ndiswrapper with the rt2500 driver, then wpa_supplicant to ensure any degree of security. But I'm getting NO HELPFUL messages in the logs to help me work out what's changed.

I boot into W2K and it works fine.

I think there needs to be some extra logging going on in this stack, to aid troubleshooting.

---

### Post by mjgumbley on 2006-05-08
[terrible habit, replying to my own threads...]

Fixed. Again. Had to completely reinstall my Windows drivers via ndiswrapper.

Was following the ndiswrapper troubleshooting guide, and they get to the stage where the card's inserted, and iwconfig should then show details for the wlan0 adapter. However, I wasn't seeing wlan0, just lo, sit0 and ra0 (the RaLink RT2500 adapter), despite /etc/modprobe.d/ndiswrapper stating 'alias wlan0 ndiswrapper'. The networking applet network-admin was showing ra0 too.

After a complete cleardown of the files in /etc/ndiswrapper, reinstall of the windows drivers, and hotplug information, and a reboot, and a genuflection towards my Richard Stallman shrine, I inserted the card, and lo! (no, not the local loopback interface) a happy, shiny wlan0, happily associating with my AP via wpa_supplicant.

Now, four hours after discovering that something mysterious had broken, I can get on...

There's something deeply wrong with reinstallation as a cure. Even reinstallation of one application's state. In this case, it seems like the hotplug info for the card had been broken. Pity there wasn't something in the log to tell me!

---

