---
title: "Rtorrent Settings Help"
date: 2011-06-16
forum: General Help
---

### Post by false_chicken on 2011-06-16
I am running ubuntu server 10.10. And I have rtorrent and ruTorrent installed and fully working except one thing. The settings I set do not seem to apply. Specifically the download location. I have set the location in /home/server/.rtorrent.rc and in the rutorrent Webui and restarted the whole server and still nothing. Any download I tell it to start still goes to the default directory. Any suggestions? This makes me nervous because I have also set it to require encryption. And so far I have no idea if my settings are taking effect. Thanks.


EDIT: Also I have noticed that when I let a download finish anyway "Automove" Does not seem to work either :/. Unless my understanding of it is wrong. I assumed it would move the finished download there. Any help would be greatly appreciated.

---

### Post by nothingspecial on 2011-06-16
I'm assuming you've removed the # from the beginning of the line.

What does that particular line in your .rtorrent.rc say

---

### Post by false_chicken on 2011-06-16
directory = /media/storage/download

Exactly that. Also it seems as nothing that I set in rutorrent is applying. I have AutoMove and AutoWatch enabled. Both pointing to valid, writable directories. Yet they both do not function. I put a torrent file into the watch directory and its not doing anything. If it means anything I installed both rtorrent and rutorrent using this script:

[http://forums.rutorrent.org/index.php?topic=608.0](http://forums.rutorrent.org/index.php?topic=608.0)

Also I had installed rtorrent from the repository before I ran the script. I had a fresh server install then installed rtorrent and forgot to remove it before the script was ran. So Idk if it might cause some conflict.

This is my config file in its entirety:
 
scgi_port = 127.0.0.1:23876
encoding_list = UTF-8
umask = 022
port_range = 23877-23877
port_random = no
check_hash = no
directory = /media/storage/download
session = /media/storage/.session
encryption = require
schedule = watch_directory,1,1,"load_start=/media/storage/incoming/*.torrent"
#schedule = untied_directory,5,5,"stop_untied=/home/server/rtorrent/watch/*.torrent"
enable_trackers = yes
#min_peers = 40
#max_peers = 100
#min_peers_seed = 10
#max_peers_seed = 50
#max_uploads = 15
#download_rate = 0
#upload_rate = 0
use_udp_trackers = yes
dht = auto
dht_port = 6881
peer_exchange = yes
#hash_read_ahead = 10
#hash_interval = 100
#hash_max_tries = 10
execute = {sh,-c,/usr/bin/php /var/rutorrent/rutorrent/php/initplugins.php server &}

---

### Post by nothingspecial on 2011-06-16
I don't know, it looks right to me.

Are you sure that script is safe, did you read it first?

---

### Post by false_chicken on 2011-06-16
I skimmed through it. Didn't really read much for the most part I relied on the comments on the thread.

---

### Post by andrew.46 on 2011-06-18
I am not familiar with rutorrent at all (although I spend too much time with rtorrent itself) but am I correct in thinking that you want to move the completed torrent downloads? This can be done in rtorrent 0.8.6 with something like the following:

```

# Move the completed torrents
system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,~/Desktop/;d.set_directory=~/Desktop/"

```

This is my own setting which moves a completed torrent to my Desktop. My apologies if I have misunderstood your question and even more apologies for being unfamiliar with rutorrent...

---

