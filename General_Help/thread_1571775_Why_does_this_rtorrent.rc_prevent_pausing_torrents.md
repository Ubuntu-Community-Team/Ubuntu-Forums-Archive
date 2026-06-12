---
title: "Why does this rtorrent.rc prevent pausing torrents"
date: 2010-09-10
forum: General Help
---

### Post by metal.lunchbox on 2010-09-10
I'm running rtorrent 0.8.6/0.12.6 with the rtorrent.rc below. I have watch directories set up and all the torrents picked up from the watch directory will automatically resume after a few seconds if I try to pause them. This is not a problem with manually added torrents. Can you find the problem? Everybody that uses rtorrent uses watch directories why should mine be a problem?

#.rtorrent.rc

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 400
upload_rate = 72 

# Default directory to save the downloaded torrents.
directory = /home/robot/watch

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /home/robot/.rtorrent

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory_1,10,10,"load_start=~/watch/tv/*.torrent,d.set_directory=~/incomplete/,d.set_custom1=/media/gLitterbox/TV"
schedule = watch_directory_2,10,10,"load_start=~/watch/movies/*.torrent,d.set_directory=~/incomplete/,d.set_custom1=/media/gLitterbox/Movies"
schedule = watch_directory_3,10,10,"load_start=~/watch/other/*.torrent,d.set_directory=~/incomplete/,d.set_custom1=~/media/gLitterbox/Downloads"
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,stop_untied=

# Move completed downloads
system.method.set_key = event.download.finished,move_complete,"d.set_directory=$d.get_custom1= ;execute=mv,-u,$d.get_base_path=,$d.get_custom1="
system.method.set_key = event.download.finished,log_complete,"execute=/home/james/Websites/tvbuddy/feedmaker.sh,$d.get_name=,$d.get_custom1="

# Close torrents when diskspace is low.
schedule = low_diskspace,10,60,close_low_diskspace=200M

# Enable the default ratio group.
ratio.enable=

# Change the limits, the defaults should be sufficient.
ratio.min.set=150
ratio.max.set=300
ratio.upload.set=20M

# Changing the command triggered when the ratio is reached.
system.method.set = group.seeding.ratio.command, d.close=, d.erase=

# Port range to use for listening.
port_range = 50401-50500

scgi_port = 127.0.0.1:5001

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

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
dht_port = 6881

# Enable peer exchange (for torrents not marked private)
#
peer_exchange = yes

---

### Post by metal.lunchbox on 2010-09-15
"schedule = tied_directory,10,10,start_tied="

automatically restarts the torrents in the watch folder. I removed it, problem solved.

---

