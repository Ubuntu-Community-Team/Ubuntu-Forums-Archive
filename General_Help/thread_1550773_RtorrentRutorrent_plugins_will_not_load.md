---
title: "Rtorrent/Rutorrent: plugins will not load"
date: 2010-08-11
forum: General Help
---

### Post by Fredrik_b on 2010-08-11
I have installed rtorrent and rutorrent, most things seams to work fine. One thing that does not work is the plugins to rutorrent. It is most likely an issue with apache and catalog permissions

I gett error like these:

> 
rTorrent's user can't access settings directory for read/write/execute. ruTorrent will not work.
rTorrent's user can't access file ./test.sh for read/execute. ruTorrent will not work.
rTorrent's user can't access torrents directory for read/execute. You can't add torrents through ruTorrent.
Web server can't access settings directory for read/write/execute. ruTorrent can't save own settings.
Web server can't access torrents directory for read/write/execute. You can't add torrents through ruTorrent.

This group of errors most likely relate to incorrect ruTorrent installation. Say the achive has been unpacked not under a web-server user account.

from:[http://code.google.com/p/rutorrent/wiki/ErrorMessages](http://code.google.com/p/rutorrent/wiki/ErrorMessages)

Unfortunately they don´t explain howto solve this.

If you want to try for you self here is my .sh script I made

```
#Install necessary packages for basic rtorrent
sudo apt-get update

sudo apt-get install -y subversion libncurses5-dev libsigc++-2.0-dev libcurl4-openssl-dev build-essential screen nano wget

#pacages for webbserver, php och XML-RPC
sudo apt-get install -y apache2 libapache2-mod-scgi php5 php5-xmlrpc php5-sqlite libxmlrpc-c3-dev libxmlrpc-c3

# install libtorrent
cd /home/torrent/

wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.12.6.tar.gz

sudo tar xvf libtorrent-0.12.6.tar.gz

cd libtorrent-0.12.6

sudo ./configure

sudo make

sudo make install

#rtorrent
cd /home/torrent/

wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.8.6.tar.gz

sudo tar xvf rtorrent-0.8.6.tar.gz

cd rtorrent-0.8.6

sudo ./configure --with-xmlrpc-c

sudo make

sudo make install

sudo ldconfig

## set up catalogs
sudo mkdir -p /home/torrent/torrents/watch/ /home/torrent/torrent/downloading/ /home/torrent/torrent/complete/ /home/torrent/torrent/.session/ /home/torrent/torrent/torrentfiles/

# setup Rutorrent

cd /var/www/

svn co http://rutorrent.googlecode.com/svn/trunk/rutorrent

svn up

# plugins
# To test
chmod -R 777 /var/www/

#plugins dl
cd /var/www/rutorrent/plugins
svn co http://rutorrent.googlecode.com/svn/trunk/plugins/rpc
svn co http://rutorrent.googlecode.com/svn/trunk/plugins/rss/
svn co http://rutorrent.googlecode.com/svn/trunk/plugins/create/
svn co http://rutorrent.googlecode.com/svn/trunk/plugins/search/
svn co http://rutorrent.googlecode.com/svn/trunk/plugins/autotools/

sudo /etc/init.d/apache2 restart

# just to make sure
sudo chown -R torrent.torrent /home/torrent


```

and an .rtorrent.rc file

```
# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 120
#
# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50
#
# Maximum number of simultanious uploads per torrent.
#max_uploads = 20
#
# Global upload and download rate in KiB. ”0? for unlimited.
#download_rate = 0
#upload_rate = 0
#
# Default directory to save the downloaded torrents.
directory = /home/torrent/torrent/downloading/;
#
# Default session directory.
session = /home/torrent/torrent/.session/;
#
# Watch a directory for new torrents, and stop those that have been deleted.
#chedule = watch_directory,5,5,load_start=/home/torrent/torrents/watch/*.torrent schedule = untied_directory,5,5,stop_untied=
schedule = watch_directory_1,10,10,"load_start=/home/torrent/torrents/watch/*.torren,d.set_custom1=/home/torrent/torrent/complete";
#
# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=100M;
#
#Stop torrents when reaching upload ratio in percent, when also reaching total upload in bytes, or when reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,stop_on_ratio=200,200M,2000
#
# Port range to use for listening.
port_range = 6890-6999;
#
# Start opening ports at a random position within the port range.
#port_random = yes
#
# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes;
#
# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
encryption = allow_incoming,enable_retry,prefer_plaintext;
#
scgi_port = 127.0.0.1:5000;
```

System used: Ubuntu 10.04 server minimal virtualization install (dont remember exactly the name)

---

