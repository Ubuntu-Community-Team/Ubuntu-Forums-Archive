---
title: "Privoxy, Tor, switchproxy"
date: 2006-03-30
forum: General Help
---

### Post by GreveFelix on 2006-03-30
Hi,
I installed Privoxy, Tor and Switchproxy. I followed the intallation text. So I wrote on top of the privoxy config file:

forward-socks4a / localhost:9050 . 

#        Sample Configuration File for Privoxy
#
#  Copyright (C) 2001-2004 Privoxy Developers [http://privoxy.org](http://privoxy.org)
#
#  $Id: config,v $
#
####################################################################
#                                                                  #
#                      Table of Contents                           #
#                                                                  #
#        I. INTRODUCTION                                           #
#       II. FORMAT OF THE CONFIGURATION FILE                       #
#                                                                  #
#        1. CONFIGURATION AND LOG FILE LOCATIONS                   #
#        2. LOCAL SET-UP DOCUMENTATION                             #
#        3. DEBUGGING                                              #
#        4. ACCESS CONTROL AND SECURITY                            #
#        5. FORWARDING                                             #
#        6. WINDOWS GUI OPTIONS                                    #
#                                                                  #
####################################################################
#
#
#  I. INTRODUCTION

..................

After that I started „Firefox“ and added a new proxy under „switchproxy“. I named it „anonym“. I wrote under HTTP Proxy 127.0.0.1 and Port 8118, the same for SSL Proxy. I switched the Socks v5 thing on, and I left the space after „No proxy for“ free. I did not turn „Automatic proxy URL“ thing on.

But as I entered the side [www.privoxy.org/config/](www.privoxy.org/config/) to test if it works. The side tould me that I was not using privoxy. It suggested to empty my cache. I did that and reloaded the side but ... the same ting: I was not using privoxy!


Hey thanks for reading my stupid text that far but ... do you know what to do? ](*,)

---

### Post by j-strap2 on 2006-03-30
Hi

I don't use the switchproxy plugin, so can't advise you how to configure it. It looks like switchproxy or whatever is not configured to route your browser traffic to privoxy listening on port 8118.

You can test to see whether your browser is routing through privoxy by typing 'p.p' (without the quotes) in the address bar - this will take you to the privoxy config. page. If you don't see the config. page, then definitely, you are not connecting to privoxy. 

In this case, I would configure firefox to use privoxy as its default connection - if it works, then your problem is with the switchproxy plugin.


Edit-->Preferences-->General-->Connection Settings
- check Manual Proxy Configuration
- HTTP Proxy = localhost    Port = 8118
- check 'use this proxy for all services'
- OK

Now try - you should be able to p.p to the privoxy config. and browse via Tor. If you can't, then the problem is with privoxy. If you can, return the connection settings to direct internet connection and play around with switchproxy.

---

### Post by GreveFelix on 2006-03-31
I will try it,
but whats also strange is: 
in the time I have installed Tor and privoxy (even as I was not using it, I mean even as I was not trying to use it) my INternet connection was wired. Sometimes it was very slow and sometimes it looked like it was realy broken down. So know I am afraid if I am using privoxy permently it will influence my inernetconnection. So another question is, are ther any problems with privoxy Tor and Ubuntu working together? or is it nomal that using privoxy will slow your Internetconnenction down?
Thanks for your help...

---

### Post by GreveFelix on 2006-03-31
Yes,
and now I deinstalled Privoxy, TOr and switchproxy! And it seems like I dont have any  internetproblems anymore.... is that normal? or maby I did something wrong during the installation? does anybody have a clou?

---

### Post by j-strap2 on 2006-03-31
I use Tor and Privoxy and it has no effect on my unproxied internet speed.

Privoxy will not affect your normal internet connection. Tor will not affect your internet connection unless you are running it as a server - by default it is not configured as a server, so you should be OK.

Which versions of Tor and Privoxy are you using? Which version of ubuntu are you using - Breezy or Dapper?

---

### Post by BoyOfDestiny on 2006-03-31
[http://p.p/](http://p.p/)

Something like this should come up:

This is Privoxy 3.0.3 on localhost (127.0.0.1), port 8118, enabled
Privoxy Menu:

    * View & change the current configuration
    * View the source code version numbers
    * View the request headers.
    * Look up which actions apply to a URL and why
    * Toggle Privoxy on or off
    * Documentation

As for manually setting it, I just go to Preferences -> General -> connection settings, and put localhost 8118 for http...

EDIT: As I read the second post I see all this info was already given... Oh well...

---

### Post by GreveFelix on 2006-03-31
OK now it works, 
maybe i did something wrong the first time i installed it. but somehow my internetconnection is rather slow again. Are your shure about the fact, that privoxy and tor does not affect the internet speed.? And why is my windows internetconnecton faster than the ubuntu connection? :confused: 

by the way i am using the breezy version.

Thanks for your help guys!

---

### Post by j-strap2 on 2006-03-31
Glad you have it working.

You mean your internet connection is slow when you are not routing through Tor ? If so, this should not be the case. Routing through Tor is slow, but non-proxied traffic should go at the same speed.

Running Linux should not get you a slower connection than Windows. What sort of network connection do you have: wireless card, ADSL modem etc.? How are you measuring the speed of your connection?

---

### Post by curtis on 2006-03-31
I'll have to agree with the above poster, running Tor should not affect your non-proxy based traffic.
Also running GNU/Linux or any other operating system should not make your connection any slower than normal.

---

### Post by GreveFelix on 2006-04-01
Yes I think you are right!
Maybe there was just a lot of traffic the first time I tried it. Today is every thing back to normal. But yesterday I switch the privoxy and Tor connection on. And after several hours my internet connection crached!! There was a Networkerror. I had this before but I thought the problem was solved with removing the wirelasscard (because the driver for that was just "experimental" there where Texas Instruments chips in that card). Now I am using the Ethernetcard. Is it possible that this networ error has something to do with using prevoxy and tor? And do you switch of privoxy and tor sometimes or are you using it all time? 


And by the way thanks for all support here! 
this is a very nice forum! =D>

---

### Post by j-strap2 on 2006-04-01
I leave tor and privoxy running as services all the time. Unless you have configured Tor as a server or to run a hidden service (you probably haven't), then they won't use bandwidth when you aren't using them. In fact, surfing through privoxy will save you a small amount of bandwidth because it filters advertisments and stuff.

I can't see that either will affect your wireless card. It is not as if Tor makes a heavy bandwidth load or many connections. Maybe your problem is just co-incidence. I had big trouble getting my wireless card running using ndiswrapper, but it seems OK now.

If you haven't done so already, make sure your packages are all up to date. You probably know how to do this, but in case not:

Run Synaptic Package Manager
Click Reload ...wait
Click Mark All Upgrades
Click Apply ...wait

Before you upgrade your packages (above), make sure you have a repository with the latest Tor packages:

sudo gedit /etc/apt/sources.list
add 2 lines at the end of the file:

deb [http://mirror.noreply.org/pub/tor/](http://mirror.noreply.org/pub/tor/) breezy main 
deb-src [http://mirror.noreply.org/pub/tor/](http://mirror.noreply.org/pub/tor/) breezy main 

save file and upgrade packages as above - this should give you the latest Tor - the standard breezy package is old and buggy.

---

### Post by GreveFelix on 2006-04-01
Yes maybe you are right ...
 I updated Tor and will see how it behaves in the future. Till now there where no problems. Thanks for your help!

---

