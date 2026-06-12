---
title: "Slow X11 but fast computer and bandwidth? (100mbit)"
date: 2010-09-19
forum: General Help
---

### Post by antdgar on 2010-09-19
I am trying to tunnel firefox through SSH X11 forwarding, running on my server, to my computer at home.

I use the command:
```
SSH -X [EMAIL="user@server.com"]user@server.com[/EMAIL]
```then ```
firefox
```This launches firefox, but it takes FOREVER to load up. Then FOREVER when I simply type a web address, etc.

It takes minutes for even one typed character to appear. Let alone load a web page.
I have also tried blowfish and a-something-four compression. No difference at all!

My computer shows only 10-15KB/s transferring when tunneling X11 firefox... This is the same on both Windows and Mac OS X x11 clients. ALL X11 forwrded applications run slowly, even xclock! 

If I use VNC on the server, I can use firefox very quickly, as fast as native speed. BUT, I want X11 to work here, not VNC...
[B]
_Any ideas on why it is going so slowly?_[/B]

I get full speed if I tunnel FTP through the server (10 megabytes per second)

[SIZE=1]My server is fast:
Core 2 Duo, 4Gb RAM
Low cpu usage (0-1%)
Bandwidth: 100mbit

desktop is fast:
Core 2 Duo, 4GB RAM
Low cpu usage (0-1%)
Bandwidth: 100mbit[/SIZE]

---

### Post by mamthor on 2011-01-15
I have a similar question, though my problem doesn't seem as acute.  In my case I am using xemacs etc. remotely for work.  I connect over the internet and the speed I find is usable but frustrating.  

I read recently a suggestion to use -XC when connecting over ssh instead of simply -X, in order to compress things and make them faster.  When I tried it I found basically no improvement in the speed, BUT, the compression IS working.  I know this because when I look at the network traffic required to open xemacs from the remote machine it is much less (about 20% as much) when I use compression, even though the operation takes almost exactly the same amount of time (22 seconds instead of 24 seconds).

If I scp a file from the same machine it will make a good use of the bandwidth, but somehow X11 tunneling just goes slowly.  Clearly this is a software limitation.  Is it on my end or the server side?  Can it be fixed somehow?

I know I used to have this experience also when working in the building (then operating remotely but only over the much faster LAN connection).  The x11 connection never seemed to make good use of the bandwidth.

---

