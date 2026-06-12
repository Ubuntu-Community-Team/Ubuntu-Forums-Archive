---
title: "Is there a simple GUI bandwitdth monitor for linux?"
date: 2010-11-01
forum: General Help
---

### Post by bobdobbs on 2010-11-01
Hi guys.

Back when I used windows, measuring my monthly internet bandwidth consumption was pretty simple. I would download an app and install it. It would run in the background and I would check it from time to time.

I've been using linux for years and I can't find anything comparable. 
Does something like this exist?

There seems to be a wealth of console-based apps that produce an output that you can read if you want to concentrate on the figures for a couple of minutes. Configuring them requires a stupid amount of thought compared to the similar windows tools.

There are also a couple of tools that will produce graphs for you if you set them up to work with a web server.
I could do that, but that seems like a stupid amount of work for a simple home-user application. All I want to do is observe my bandwidth consumption day-to-day or month-to-month.

I've installed netspeed, but that doesn't give me totals or graphs.

Does a simple GUI tool for measuring bandwidth usage exist for linux?

---

### Post by bobdobbs on 2010-11-04
bump

---

### Post by WorMzy on 2010-11-04
I don't know how useful you'll find these, but these are all the relevant apps I could find:

iperf - A tool to measure maximum TCP bandwidth (in repos)
[jperf]("http://xjperf.googlecode.com/") - Front-end to iperf
bwm-ng - A small and simple console-based live bandwidth monitor (in repos)
bandwidthd - Tracks usage of TCP/IP network subnets and builds html files with graphs to display utilization. (in repos)
bmon - Portable bandwidth monitor and rate estimator. (in repos)
[bwstats]("http://developer.berlios.de/projects/bwstats/") - A daemon which grabs bandwidth data and generates a flow chart diagram
nload - A console application which monitors network traffic and bandwidth usage in real time (in repos)

Maybe you'll be able to find something amongst this lot that you can use. It does seem to be quite slim pickings, I'm afraid.

---

### Post by coldraven on 2010-11-04
I know what you want, I previously used "Download Monitor" in Windows but I've seen nothing like that for Linux.
Anyway as we mostly use routers I think most of the total would be my LAN rather than the actual internet usage.
However, I can go to a page at my ISP which shows me the usage of my monthly bandwidth.
Check and see if your ISP offers the same service.

---

### Post by bobdobbs on 2010-11-04
> **coldraven said:**
> I know what you want, I previously used "Download Monitor" in Windows but I've seen nothing like that for Linux.
Anyway as we mostly use routers I think most of the total would be my LAN rather than the actual internet usage.
However, I can go to a page at my ISP which shows me the usage of my monthly bandwidth.
Check and see if your ISP offers the same service.

My ISP is pretty good on this account. 
(actually, they are pretty good all around)

They actually have a firefox plugin that keeps you updated on your bandwidth use.

However, this isn't what I want:
I share a connection to my flat. I want to know my own usage - not the total usage.

---

### Post by bobdobbs on 2010-11-04
> **WorMzy said:**
> I don't know how useful you'll find these, but these are all the relevant apps I could find:

iperf - A tool to measure maximum TCP bandwidth (in repos)
[jperf]("http://xjperf.googlecode.com/") - Front-end to iperf
bwm-ng - A small and simple console-based live bandwidth monitor (in repos)
bandwidthd - Tracks usage of TCP/IP network subnets and builds html files with graphs to display utilization. (in repos)
bmon - Portable bandwidth monitor and rate estimator. (in repos)
[bwstats]("http://developer.berlios.de/projects/bwstats/") - A daemon which grabs bandwidth data and generates a flow chart diagram
nload - A console application which monitors network traffic and bandwidth usage in real time (in repos)

Maybe you'll be able to find something amongst this lot that you can use. It does seem to be quite slim pickings, I'm afraid.

Yeah - it's kind of funny. So many tools to do a similair job. But none of them fits a specific, yet very simple bill.

bmon, bwm-ng and nload are console based. They take ages to figure out, and the output isn't as easy to read. I haven't looked into what it takes to get them to present summaries for periods of time, like months. But after having looked at them, I'm not encouraged that the task would be simple.

iperf/jperf aren't what I'm looking for either. They appear to be for network testing. I'd have to spend ages reading through docs and setting things up before I got simple presentations on how much bandwidth I'm using.

Now, bandwidthd looked really hopeful.
It was in the repos too. That was a good sign.
I installed it earler today.
But I couldn't find any online documentation for it.
It doesn't come with an example config file, but it won't work without one.

I haven't looked at bwstats.
Unfortunately, it doesn't look like it's in the repos.

I'm pretty much a linux fanboy.
But the absence of a simple GUI bandwidth measuring tool is pretty pathetic.

I had a look at cactii too.
But this is both overkill and hard to configure for actually measuring bandwidth.

---

### Post by gregolak on 2011-07-02
I found this one, it seems ok :

[http://sourceforge.net/projects/netramon/](http://sourceforge.net/projects/netramon/)

---

### Post by bobdobbs on 2011-07-13
> **gregolak said:**
> I found this one, it seems ok :

[http://sourceforge.net/projects/netramon/](http://sourceforge.net/projects/netramon/)

Looks like it could be good.

But it's not in the repos.
The package can't be installed by gdebi because I don't have the dependancies. gdebi does not report the names of the required deps.

---

### Post by CatKiller on 2011-07-13
> **bobdobbs said:**
> The package can't be installed by gdebi because I don't have the dependancies. gdebi does not report the names of the required deps.

```
dpkg -I ntm-1.2.4.deb 
...
 Depends: python-webkit, python-rsvg, python-notify

```

---

### Post by spegru on 2011-10-06
I just tried iperf, with the jperf GUI. It's pretty good. All I had to do test a link is set up one PC as server and the other as client.
I've now bought some Gigabit Ethernet USB adaptors and should also be able to test faster connections soon.

iperf is in the repos and you need to install iperf even if you use jperf, which is a java based GUI front end for iperf, complete with graphical performance displays etc. jperf is not in the repos but you can get it from here [http://sourceforge.net/projects/iperf/files/jperf/jperf%202.0.0/](http://sourceforge.net/projects/iperf/files/jperf/jperf%202.0.0/)

You can see screen shots etc (albeit from windows, but they are the same in linux) here [http://code.google.com/p/xjperf/](http://code.google.com/p/xjperf/) 

To get the jperf GUI you have to unzip the archive, mark the jperf.sh as executable inside file properties, and just run the jperf.sh
You can also see the raw iperf commands being created by jperf as you adjust the various settings

---

### Post by ejames on 2011-10-06
try this...

cat /proc/net/dev

as you can see it shows the total bytes received and transmitted since the computer was switched on. If you repeat the command you can see the numbers change as you use the network interfaces.

What you need is to set up a cron job that periodically runs that command in the background, parses the output to get the usage in that time period, then logs it into something like rrdtool. You then need a nice gui program that reads the rrd database and gives you a nice graph.

Sounds like a nice little dev project...I may have a go at it. Python and wxPython to the rescue!

---

### Post by SCIIAM on 2011-11-26
Is there a simple way for my ubuntu server on a specific PC to measure the traffic comming out from my D-Link router (and used by the whole LAN)

---

### Post by cwwilson721 on 2011-11-26
> **SCIIAM said:**
> Is there a simple way for my ubuntu server on a specific PC to measure the traffic comming out from my D-Link router (and used by the whole LAN)

I use UPnP Router Control.

Installable thru the Software Center.

Works great on my Linksys

[https://launchpad.net/upnp-router-control](https://launchpad.net/upnp-router-control)

---

### Post by Sijmen on 2012-01-06
In the Windows days I used DM Monitor, which was awesome. With my Mac I  didn't need a monitor(ADSL), and now with Xubuntu I definitely need one  because I'm on a 3G card.

A GUI-fied app with linux seems nearly impossible! Everything is command line based! vnStat has a GUI, which is PHP based so I have to set up a webserver. The same goes for Cacti. Both are excellent applications and create massive amounts of information for a complete bandwidth database, but to run a web server specifically for bandwidth monitoring is just stupid. I now run vnstat every so often to see how far along the 3G usage is, but I would like a nice window to look at which shows all the relevant information..... I think it's hopeless......

---

### Post by Sijmen on 2012-01-06
I could do a Conky based monitor though.......

---

