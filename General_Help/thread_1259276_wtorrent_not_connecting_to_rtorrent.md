---
title: "wtorrent not connecting to rtorrent"
date: 2009-09-06
forum: General Help
---

### Post by GamerZFX on 2009-09-06
Ok Im using Ubutnu 9.04 x86 and the latest versions of rTorrent and wTorrent, everythings working EXCEPT wTorrents not connecting to rTorrent and not sure why. I also was never prompted for the rt username and password I used this: [http://ubuntuforums.org/showthread.php?t=1064377](http://ubuntuforums.org/showthread.php?t=1064377) to install on a fresh server (no errors during install) Here are my various config files

.rtorrent.rc:
```
scgi_port = localhost:5000

# Move completed torrents to /home/rt/torrents/done/
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/rt/torrents/done/ ;d.set_directory=/home/rt/torrents/done/"

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
```

user.conf.php:
```
<?php
/* wTorrent autoconfiguration file. Created 6/9/2009 */
define ('LANGUAGE', 'en');
define ('DB_FILE', 'db/database.db');
define ('RT_HOST', 'localhost');
define ('RT_PORT', 5000);
define ('RT_DIR', '/RPC2');
define ('RT_AUTH', false);
define ('RT_USER', '');
define ('RT_PASSWD', '');
define ('NO_MULTICALL', true);
define ('EFFECTS', true);
define ('DIR_TORRENTS', 'torrents/');
define ('DIR_EXEC', '/var/www/');
define ('DIR_DOWNLOAD', '/home/rt/torrents/doing');
?>
```

lighttpd.conf:
```
############ Options you really have to take care of ####################

## modules to load

# mod_access, mod_accesslog and mod_alias are loaded by default

# all other module should only be loaded if neccesary

# - saves some time

# - saves memory

server.modules              = ( 

            "mod_access",

            "mod_alias",

            "mod_accesslog",

			"mod_scgi",

			"mod_fastcgi",

#           "mod_rewrite", 

#           "mod_redirect", 

#           "mod_status", 

#           "mod_evhost",

#           "mod_compress",

#           "mod_usertrack",

#           "mod_rrdtool",

#           "mod_webdav",

#           "mod_expire",

#           "mod_flv_streaming",

#           "mod_evasive"

 )

## a static document-root, for virtual-hosting take look at the 

## server.virtual-* options

server.document-root       = "/var/www/"

## where to send error-messages to

server.errorlog            = "/var/log/lighttpd/error.log"

## files to check for if .../ is requested

index-file.names           = ( "index.php", "index.html", 

                               "index.htm", "default.htm" )

## Use the "Content-Type" extended attribute to obtain mime type if possible

# mimetype.use-xattr = "enable"

#### accesslog module

accesslog.filename         = "/var/log/lighttpd/access.log"

## deny access the file-extensions

#

# ~    is for backupfiles from vi, emacs, joe, ...

# .inc is often used for code includes which should in general not be part

#      of the document-root

url.access-deny            = ( "~", ".inc" )

######### Options that are good to be but not neccesary to be changed #######

## bind to port (default: 80)

server.port               = 80

## bind to localhost only (default: all interfaces)

## server.bind                = "localhost"

## error-handler for status 404

#server.error-handler-404  = "/error-handler.html"

#server.error-handler-404  = "/error-handler.php"

## to help the rc.scripts

server.pid-file            = "/var/run/lighttpd.pid"

## 

## Format: .html

## -> ..../status-404.html for 'File not found'

#server.errorfile-prefix    = "/var/www/"

## virtual directory listings

dir-listing.encoding        = "utf-8"

server.dir-listing          = "enable"

## send unhandled HTTP-header headers to error-log

#debug.dump-unknown-headers  = "enable"

### only root can use these options

#

# chroot() to directory (default: no chroot() )

#server.chroot            = "/"

## change uid to  (default: don't care)

server.username            = "www-data"

## change uid to  (default: don't care)

server.groupname           = "www-data"

#### compress module

#compress.cache-dir          = "/var/tmp/lighttpd/cache/compress/"

#compress.filetype           = ("text/plain", "text/html")

#### status module

# status.status-url = "/server-status"

# status.config-url = "/server-config"

#### url handling modules (rewrite, redirect, access)

# url.rewrite                 = ( "^/$"             => "/server-status" )

# url.redirect                = ( "^/wishlist/(.+)" => "http://www.123.org/$1" )

#

# define a pattern for the host url finding

# %% => % sign

# %0 => domain name + tld

# %1 => tld

# %2 => domain name without tld

# %3 => subdomain 1 name

# %4 => subdomain 2 name

#

# evhost.path-pattern = "/home/storage/dev/www/%3/htdocs/"

#### expire module

# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### rrdtool

# rrdtool.binary = "/usr/bin/rrdtool"

# rrdtool.db-name = "/var/www/lighttpd.rrd"

#### handle Debian Policy Manual, Section 11.5. urls

#### and by default allow them only from localhost

$HTTP["remoteip"] =~ "127.0.0.1" {

	alias.url += ( 

		"/doc/" => "/usr/share/doc/",

		"/images/" => "/usr/share/images/"

	)

	$HTTP["url"] =~ "^/doc/|^/images/" {

		dir-listing.activate = "enable"

	}

}

#### variable usage:

## variable name without "." is auto prefixed by "var." and becomes "var.bar"

#bar = 1

#var.mystring = "foo"

## integer add

#bar += 1

## string concat, with integer cast as string, result: "www.foo1.com"

#server.name = "www." + mystring + var.bar + ".com"

## array merge

#index-file.names = (foo + ".php") + index-file.names

#index-file.names += (foo + ".php")

#### external configuration files

## mimetype mapping

include_shell "/usr/share/lighttpd/create-mime.assign.pl"

## load enabled configuration files, 

## read /etc/lighttpd/conf-available/README first

include_shell "/usr/share/lighttpd/include-conf-enabled.pl"

scgi.server = (

 "/RPC2" => # RT_DIR

  ( "127.0.0.1" =>

   (

    "host" => "127.0.0.1", # Ip where rtorrent is listening

    "port" => 5000, # Port specified in .rtorrent.rc

    "check-local" => "disable"

   )

  )

 )

 fastcgi.server = ( ".php" => (( 

                     "bin-path" => "/usr/bin/php-cgi",

                     "socket" => "/tmp/php.socket"

                 )))

auth.backend = "htdigest"

auth.backend.htdigest.userfile = "/etc/lighttpd/htdigest"

auth.require = ( "/RPC2" =>

 (

  "method" => "basic",

  "realm" => "XML-RPC",

  "require" => "valid-user"

 ),

 "/torrents" =>

 (

  "method" => "basic",

  "realm" => "XML-RPC",

  "require" => "valid-user"

 ),

 "/db" =>

 (

  "method" => "basic",

  "realm" => "XML-RPC",

  "require" => "valid-user"

 )

)

```

---

