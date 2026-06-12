---
title: "rtorrent config file"
date: 2012-01-25
forum: General Help
---

### Post by Superdude_123 on 2012-01-25
It seems that I can't get my rtorrent to work and I think its the config file that's the problem.

I'm using Ubuntu 11.10 with rtorrent 0.8.7/0.12.7. 

Here's my config file, any input would be great:


#Maximum and minimum number of peers to connect to per torrent.
#min_peers = 0
max_peers = 200
# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 0
max_peers_seed = 50
# Maximum number of simultanious uploads per torrent.
max_uploads = 20
# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 20
# Default directory to save the downloaded torrents.
directory = ~/torrents/completed
# Default session directory.
session = ~/torrents/session
# Watch a directory for new torrents, restart torrents that have been copied back and stop those that have been
# deleted.
schedule = watch_directory,10,10,"load_start=~/torrents/watch/*.torrent"
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=
# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=100M
#Stop torrents when reaching upload ratio 300 percent
ratio.enable= ratio.min.set=300
# Port range to use for listening.
port_range = 6881-6889
# Start opening ports at a random position within the port range.
port_random = no
# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = no
# Encryption options. This can be useful when using an ISP that uses traffic shaping.
encryption=allow_incoming,try_outgoing,enable_retry,prefer_plaintext
#scgi_port = 127.0.0.1:5000
#xmlrpc_dialect=i8
#DHT
dht = disable
#dht_port = 6881
peer_exchange = yes


I've also noticed that I can't seem to kill my rtorrent, and I must reboot the system to do so. Could this be related to all the same problem?

---

### Post by pyroscope on 2012-01-25
Using a stable version (i.e. 0.8.9) would be a good idea, 0.8.7 definitely has problems.

If you actually mentioned what the problem is / symptoms are beyond "don't work", it'd also help to help.

---

