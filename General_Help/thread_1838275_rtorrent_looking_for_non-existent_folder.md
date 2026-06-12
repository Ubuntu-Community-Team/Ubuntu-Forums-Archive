---
title: "rtorrent looking for non-existent folder"
date: 2011-09-03
forum: General Help
---

### Post by bonfire89 on 2011-09-03
Hey all,

This isn't a very urgent question but something that has be stumped.

When I start rtorrent I get

```

( 9:27:40) Using 'epoll' based polling.
( 9:27:40) XMLRPC initialized with 519 functions.
( 9:27:40) The SCGI socket is bound to a specific network device yet may still pose a security risk, consider using 'scgi_local'.
( 9:27:40) Could not create directory '/mnt/other/sdc1/torrent/downloading': No such file or directory
( 9:27:40) Could not create directory '/mnt/other/sdc1/torrent/downloading': No such file or directory

```


my issue is with "/mnt/other/sdc1/torrent/downloading': No such file or directory."

I can't figure out who it is trying to access that directory. The directory did in fact used to exist but it does not any longer.

I checked my config file in ~/ for anything referring to it and nothing, and I "grep -r 'other' ." some other related folders and got nothing relevant.

~/.rtorrent.rc
```


# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
#max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
#upload_rate = 0

# Default directory to save the downloaded torrents.
directory = /mnt/sdc1/downloads/torrent/downloading/
system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,/mnt/sdc1/downloads/torrent/complete/;d.set_directory=/mnt/sdc1/downloads/torrent$


# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /mnt/sdc1/downloads/torrent/session/

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/mnt/sdc1/downloads/torrent/toStart/*.torrent
#schedule = untied_directory,5,5,stop_untied=

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
#port_range = 6890-6999

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
# encryption = allow_incoming,enable_retry,prefer_plaintext

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


# as per rutorrent install guide
# http://code.google.com/p/rutorrent/wiki/MainInstall
scgi_port = 127.0.0.1:5001

```

If anyone has any clue to this mystery let me know.

Thanks :)

---

### Post by pyroscope on 2011-09-04
You very likely still have items in your session dir initially loaded with the old config. The easiest solution is to place a symlink.

---

### Post by andrew.46 on 2011-09-08
Hmmmm.... but what about these entries:

```

# Default directory to save the downloaded torrents.
directory = **[COLOR="Red"]/mnt/sdc1/downloads/torrent/downloading/[/COLOR]**
system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,**[COLOR="Red"]/mnt/sdc1/downloads/torrent/complete/[/COLOR]**;d.set_directory=**[COLOR="Red"]/mnt/sdc1/downloads/torrent[/COLOR]**$


# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = **[COLOR="Red"]/mnt/sdc1/downloads/torrent/session/[/COLOR]**

```

My apologies if I am missing your point entirely. I imagine this is some sort of removable storage medium?

---

### Post by bonfire89 on 2011-09-10
hehe yeah they are pretty similar but it is

directory = /mnt/sdc1/downloads/torrent/downloading/
vs
"/mnt/other/sdc1/torrent/downloading': No such file or directory

I was doing some upgrades and went back on a file system layout decision made other and removed one of the directories.

The only place I can see it being is in the session. I've grep'd the files looking for "/mnt/other" and it isn't to be found. And the session files are binary thus the grep'ing wont cover them.

At some point I will try and refresh the session but at the moment I have 30 open-source ISOs that would have to be manually added back. So, perhaps during the winter holidays when I have time off. heh

Thanks though!

---

