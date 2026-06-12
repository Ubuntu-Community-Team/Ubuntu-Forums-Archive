---
title: "Regulating Download Speeds"
date: 2012-03-10
forum: General Help
---

### Post by erbad on 2012-03-10
When I use Transmission, Internet browsing slows to a complete grind.

Is there a way to set it so that Transmission uses the full bandwidth but if I am browsing, the webpage request gets the highest priority and is processed as fast as possible.

Right now, I can't use Transmission when browsing because it takes literally 30 seconds for a webpage to show up.

I did take a look at QOS on the router, but that didn't really work very well.

Thank you

---

### Post by synaptix on 2012-03-10
Just simply reduce the speed cap used by transmission for downloads/uploads, as it sounds like you are either maxxing out your download or upload streams.

---

### Post by sanderj on 2012-03-10
> **erbad said:**
> When I use Transmission, Internet browsing slows to a complete grind.

Is there a way to set it so that Transmission uses the full bandwidth but if I am browsing, the webpage request gets the highest priority and is processed as fast as possible.

Right now, I can't use Transmission when browsing because it takes literally 30 seconds for a webpage to show up.

I did take a look at QOS on the router, but that didn't really work very well.

Thank you

Simple: lower the max on the UPstream traffic to 25% of you realstream. And please note that your ISP and network reports in bits per second, whereas transmission reports in bytes per second. So if you Internet UPstream is 1 Mbps, that is 0.1 MB/s, so then set transmission UPstream to 25 kB/s

---

### Post by erbad on 2012-03-10
> **sanderj said:**
> Simple: lower the max on the UPstream traffic to 25% of you realstream. And please note that your ISP and network reports in bits per second, whereas transmission reports in bytes per second. So if you Internet UPstream is 1 Mbps, that is 0.1 MB/s, so then set transmission UPstream to 25 kB/s

Thank you.  can you confirm that I've done this right, I've never been comfortable with the abbreviations for kilobits, kilobytes, etc.  I just did a speed test and my download speed is 0.38 Mbps

When I use the Google converter, I get 0.38 Mbps = 48.64 kilobytes / second

Does that mean I set the Transmission upload to (48.64*0.25)= 12.16?

Also, I guess I don't have to worry about the Download, just the upload?

---

### Post by hawthornso23 on 2012-03-10
Limiting upload is usually enough.

The problem is buffer bloat. According to the protocol packets should be simply dropped if not delivered in a timely fashion.  However often people who write network software are loathe to drop packets if they cannot be delivered immediately and will store them up in a buffer instead. When the stream of packets hits a slow part of the pipe any buffers before the constriction will fill up introducing a delay. The network software tries to push packets through at the maximum speed possible without packets being dropped. This unfortunately means that those buffers will fill right up and be kept full. With memory cheap some of these buffers can be huge introducing a massive delay in the delivery of packets.

Upload is more of a critical problem than download because for most  people local networking is a lot faster than the internet. That means the upload buffers are the ones that fill up while the download buffers don't cause a problem because usually empty faster than they are filled. However a delay in upload speeds interferes with download speeds as well since control packets needed for the control of download also end up being massively delayed. 

Throttle your upload speed just slow enough to stop those buffers from filling and the problem will go away.

---

### Post by JC Cheloven on 2012-03-10
Hint: have you seen the turtle at the bottom of transmission window? It sets a reduced download & upload rate (which is configurable) when pressed. 

I set up that to something suitable for concurrent web browsing etc, and I press the button when I need some bandwith for my own use.

Hope that helps.

---

### Post by erbad on 2012-03-10
> **sanderj said:**
> Simple: lower the max on the UPstream traffic to 25% of you realstream. And please note that your ISP and network reports in bits per second, whereas transmission reports in bytes per second. So if you Internet UPstream is 1 Mbps, that is 0.1 MB/s, so then set transmission UPstream to 25 kB/s

This was amazing advice, I can't believe what a difference this has made.

Thank you

---

