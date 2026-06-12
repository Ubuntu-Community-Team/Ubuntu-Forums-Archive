---
title: "rtorrent help needed - error &quot;Tracker: [Timeout was reached]&quot;"
date: 2009-12-05
forum: General Help
---

### Post by Nixie Pixel on 2009-12-05
Hi! I am using ssh to connect to a headless server where I have installed rtorrent. I am using screen to run rtorrent, anticipating that I will be leaving it running when I drop the ssh tunnel. Unfortunately I can't seem to download anything at the moment. I start the download but I keep getting the error message "Tracker: [Timeout was reached]" whenever it tries to connect.

I have opened two ports on my router (one TCP/UDP for rtorrent, and one UDP for rtorrent's use of DHT) and forwarded them to my server's static ip. I've tested that the ports are open, they are. What other issues could there be with my setup? 

I did install Gnome on my Ubuntu Server 8.10 (long story), but I prefer connecting via ssh. I would just feel dirty giving my server (a) head. :twisted:

I know, I know, sorry! I couldn't help myself! 8-)

Please see my rtorrent.rc file below, if it will help:

```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 1
max_peers_seed = 25

# Maximum number of simultanious uploads per torrent.
max_uploads = 8

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 1000
upload_rate = 150

# Default directory to save the downloaded torrents.
directory = /server/downloads/torrents/

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = ./session/

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/server/downloads/torrents/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=500M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
port_range = 49164-49164

# Start opening ports at a random position within the port range.
port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
encryption = allow_incoming,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
# 
dht = auto

# UDP port to use for DHT. 
# 
dht_port = 49166

# Enable peer exchange (for torrents not marked private)
#
# peer_exchange = yes

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10

handshake_log = yes
```

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
I actually have the same problem starting torrents from my G-phone over ssh but I came to find that it can be done if you ```
ssh -x host
``` then type gnome-session (I think... been a while.) to get the server's gnome session (do this from tty1 or before starting x). From there you have the server's X session and can do as thou wilt. I'm still trying to figure out why it won't work from the terminal...

---

### Post by Nixie Pixel on 2009-12-05
When I try that, it tells me that it can't open the display. I'm pretty sure that I logged into the console before I removed the monitor from my server. So you want me to log out at the console or reboot the server, and then try this?

---

### Post by mobilediesel on 2009-12-05
> **Nixie Pixel said:**
> When I try that, it tells me that it can't open the display. I'm pretty sure that I logged into the console before I removed the monitor from my server. So you want me to log out at the console or reboot the server, and then try this?

You'll actually want it to be -X rather than -x to forward the x-session.

As for the "Tracker: [Timeout was reached]" sometimes I see that error but it downloads anyway. I don't see that error very often but I think it's usually on a very busy torrent that a lot of people are trying to connect to at the same time.

---

### Post by Nixie Pixel on 2009-12-05
Ok, well, I've been trying it all day, and it still isn't working...you would think that it would work at least once.

Here is the result of using X instead of x:

```
nixie@lion:~$ sudo gnome-session
[sudo] password for nixie: 
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.

** (gnome-session:2854): WARNING **: Cannot open display: 
nixie@lion:~$ 
```

---

### Post by mobilediesel on 2009-12-05
> **Nixie Pixel said:**
> Ok, well, I've been trying it all day, and it still isn't working...you would think that it would work at least once.

Here is the result of using X instead of x:

```
nixie@lion:~$ sudo gnome-session
[sudo] password for nixie: 
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.

** (gnome-session:2854): WARNING **: Cannot open display: 
nixie@lion:~$ 
```

Hmm. Are you trying to connect to a gnome session that's already running? Usually when I use the **-X** I'm running a specific program:
```
ssh -X user@machine gedit
```
or
```
ssh -X user@machine gksudo gedit
```

ah! I think I figured out at least part of it by typing that. gksudo is for running gui programs, sudo is for the terminal!

---

### Post by Nixie Pixel on 2009-12-05
Actually, I don't have any need to forward -X, I was only trying it because it was suggested above.

My only goal is to fix rtorrent so that my downloads work.

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
> **mobilediesel said:**
> You'll actually want it to be -X rather than -x to forward the x-session.

As for the "Tracker: [Timeout was reached]" sometimes I see that error but it downloads anyway. I don't see that error very often but I think it's usually on a very busy torrent that a lot of people are trying to connect to at the same time.

Oops... sorry. Anyway... I'm gonna install rtorrent and try a few things. BRB...

---

### Post by mobilediesel on 2009-12-05
> **Nixie Pixel said:**
> Actually, I don't have any need to forward -X, I was only trying it because it was suggested above.

My only goal is to fix rtorrent so that my downloads work.

I guess I was trying to solve a minor problem that may or may not have helped with the main problem!

I had to think because it's been awhile since I set up rtorrent myself. I use [Uncomplicated Firewall (UFW)]("http://en.wikipedia.org/wiki/Uncomplicated_Firewall") to make sure the ports were open. It's less complicated than going through the IP tables. The router isn't the only place you need to have the ports open.

ufw is in the repositories at least starting with Hardy.
Based on your .rtorrentrc, try this after making sure ufw is installed:
```
sudo ufw allow 49164
sudo ufw allow 49166
```

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
Well... actually it works well for me without forwarding X11. Guess that's only a problem with Bittornado. Anyway I would say that the torrent may be dead or broken. Have you tried that torrent on the machine you gave head?

---

### Post by Nixie Pixel on 2009-12-05
The torrent worked on a machine other than the server...hmm...

---

### Post by mobilediesel on 2009-12-05
> **Nixie Pixel said:**
> The torrent worked on a machine other than the server...hmm...

Other than making sure the ports are open on the server in addition to the router, I'm out of ideas as your .rtorrentrc looks like it should.

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
> **Nixie Pixel said:**
> The torrent worked on a machine other than the server...hmm...

All I can say is try another client because I've read a few places that some trackers ban rtorrent for some reason or another. Sorry...

---

### Post by whitethorn on 2009-12-05
Well I can't really help you with rtorrent, but if you're ready to try a different another client I would suggest using deluge.  Here's a good howto.

[http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html](http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html)

---

### Post by Nixie Pixel on 2009-12-05
I guess I'll have to try another client, since I just can't get this one working.

One thing I should note, since it might be missed - I installed rtorrent on Ubuntu Server 8.10. Is there some way I can check to see if there is a difference between server edition and Ubuntu that is causing a problem?

---

### Post by mobilediesel on 2009-12-05
> **Nixie Pixel said:**
> I guess I'll have to try another client, since I just can't get this one working.

One thing I should note, since it might be missed - I installed rtorrent on Ubuntu Server 8.10. Is there some way I can check to see if there is a difference between server edition and Ubuntu that is causing a problem?

I don't know if there would be a difference from the server version or not. I'm running rTorrent on Xubuntu 8.04 and the only time I've seen that error is when a tracker is super-busy.

What torrent are you/were you trying to download? I can try it on my setup and see if it has a problem.

As stated by others in this thread, you could try Deluge since it now has the user interface separate from the daemon. It looks like you can access it through the console as well as a web interface.

---

### Post by Nixie Pixel on 2009-12-06
> **mobilediesel said:**
> I don't know if there would be a difference from the server version or not. I'm running rTorrent on Xubuntu 8.04 and the only time I've seen that error is when a tracker is super-busy.

What torrent are you/were you trying to download? I can try it on my setup and see if it has a problem.

As stated by others in this thread, you could try Deluge since it now has the user interface separate from the daemon. It looks like you can access it through the console as well as a web interface.
I was downloading the latest episode of Dexter. It was busy, but Transmission had no problems downloading it on my local machine, so I don't know what my server's issue (or rtorrent's issue) was.

---

### Post by mobilediesel on 2009-12-07
> **Nixie Pixel said:**
> I was downloading the latest episode of Dexter. It was busy, but Transmission had no problems downloading it on my local machine, so I don't know what my server's issue (or rtorrent's issue) was.

All I can think is that the server has the ports closed that you're trying to use. I run rtorrent using screen on my desktop and I remember having to make sure the ports I used were open on my desktop as well as forwarded in the router.

Other than the occasional private tracker that wasn't marked as being private, I haven't had any trouble with rtorrent. I might just be that the server is more different from the desktop than I thought.

*P.S.* I saw that edit. I just watched the latest "version" of Stargate Universe. ;)

---

### Post by Nixie Pixel on 2009-12-20
> **mobilediesel said:**
> All I can think is that the server has the ports closed that you're trying to use. I run rtorrent using screen on my desktop and I remember having to make sure the ports I used were open on my desktop as well as forwarded in the router.
I tested it with the utorrent test site - it was able to connect to the open ports on the server, so that isn't the problem.

> **mobilediesel said:**
> Other than the occasional private tracker that wasn't marked as being private, I haven't had any trouble with rtorrent. I might just be that the server is more different from the desktop than I thought.
This is possible...but I'm not sure how, I don't have enough experience to say. I'm still a newbie at this!

> **mobilediesel said:**
> *P.S.* I saw that edit. I just watched the latest "version" of Stargate Universe. ;)
I thought I could sneak that by :P

---

### Post by mobilediesel on 2009-12-21
> **Nixie Pixel said:**
> I tested it with the utorrent test site - it was able to connect to the open ports on the server, so that isn't the problem.


This is possible...but I'm not sure how, I don't have enough experience to say. I'm still a newbie at this!

We're all newbies at one time or another. I'm certainly not anywhere near being a Linux genius! At least, not yet. :)

> **Nixie Pixel said:**
> I thought I could sneak that by :P

I only caught the typo because it was emailed before you edited. Plus, I just like messing with people. :D

---

