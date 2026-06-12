---
title: "Network activity by process"
date: 2012-07-09
forum: General Help
---

### Post by richwein on 2012-07-09
I can use the application System Monitor to see a graph of network activity by upload and download.

But, is there some way to identify the network activity by process or application ?

Thanks

---

### Post by Cheesehead on 2012-07-09
Several tools will show you network activity by type (ICMP, SSH, NTP, HTTP, FTP, etc). Personally, I use etherape for that. Other good ones are available.

None will show you which application is sending (or receiving) a specific set of packets. It's easy enough to do the detective work and figure it out, if you really want to know.

Yes, it's possible to use IPTables to output by-application names for each packet...but you'll be swamped with data and have more questions than answers. I've seen Firefox pull data for one web page from twelve different servers using three different methods - untangling that was quite a waste of time.

In the past, many requests for by-application info were workarounds. Really, users were trying to figure out what was consuming bandwidth on an expensive network, or consuming bandwidth while idle, or diagnosing firewall issues. There are better tools for those tasks than by-application info.

Why do you want to know by application?
What are you really trying to figure out?

---

### Post by richwein on 2012-07-09
Thank you.  I also have wireshark but there is a lot of information that is difficult to decipher.  

The motivation for the question is:  I have a slow internet connection, and sometimes it gets swamped.  My guess is that some of it is checking for updates from various applications or Ubuntu.

Just trying to figure out the best way to see which application running under ubuntu is downloading or uploading data.  I'm less interested in the browser activity and I can exit such applications to eliminate them, such as browser, skype, dropbox which may access the internet without a specific command from me.

I may be able to manage when those accesses occur if I can find out which ones they are.

Somewhere in linux there must be a call to open a connection with ethernet, and there must be a way to capture the data or amount of data from a particular process ID.   

I guess the other way to find the process is to kill process while it is running while monitoring the internet activity graphic in system monitor, but that is messy and might corrupt something too.

Thanks for any advice.

---

### Post by richwein on 2012-07-09
Cheesehead

Thanks for mentioning EtherApe .  It does give a clue to which app based on the destinations.  Very cool graphic display.

---

### Post by Cheesehead on 2012-07-09
Yeah, for the purpose you described (finding a bandwidth hog), I usually find EtherApe to be adequate. Naturally, your mileage may differ.

---

