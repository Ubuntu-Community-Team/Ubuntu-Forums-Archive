---
title: "rtorrent experts: rtorrent not seeding/connecting"
date: 2009-11-13
forum: General Help
---

### Post by elcaballo on 2009-11-13
I've got rtorrent + wtorrent running and it downloads fine and seems to upload while it's downloading. But it never really shows that it's connecting to any peers/seeds while it downloads and, once it's completed, it doesn't seed unless it randomly finds a peer through peer discovery.

I don't have UFW enabled and as you can see below, rtorrent encryption is off.

This is what wtorrent looks like:
[IMG]http://i37.tinypic.com/ioorgp.png[/IMG]
(That one peer I'm connecting to is probably just through peer discovery.)

This is what my Tomato port forwarding page looks like:
[IMG]http://i37.tinypic.com/2z6htmt.png[/IMG]

And here is my .rtorrent.rc:
```

scgi_port = localhost:5000

# Move completed torrents to /home/rt/torrents/done/
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/rt/torrents/done/ ;d.set_directory=/home/rt/torrents/done/"

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 2
max_peers = 80

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 1
max_peers_seed = 30

# Maximum number of simultanious uploads per torrent.
max_uploads = 8

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
upload_rate = 100

# Default directory to save the downloaded torrents.
directory = /home/rt/torrents/doing

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/rt/.rtsession

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/rt/torrents/watch/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
port_range = 24669-24669

# Start opening ports at a random position within the port range.
#port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
#use_udp_trackers = yes

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
#encryption = allow_incoming,try_outgoing,enable_retry,prefer_plaintext

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
#
# dht = auto

# UDP port to use for DHT.
#
# dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
peer_exchange = yes

on_finished = do_a_beep,"execute=beeper"

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
```

---

### Post by lovinglinux on 2009-11-13
It's probably a tracker issue. I guess you are able to connect only through DHT. 

I never used rtorrent, so I can't give you more advice, but you could check the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923), specially the troubleshooting section.

---

