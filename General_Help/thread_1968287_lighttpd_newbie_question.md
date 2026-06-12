---
title: "lighttpd newbie question"
date: 2012-04-28
forum: General Help
---

### Post by test006 on 2012-04-28
Hi,
I am trying to install tikiwiki on Ubuntu server 12.04. For my webserver i am using lighttpd. I have installed lighttpd server and it is working. Under /var/www i have created a folder called tiki. All the tiki files i have copied to /var/www/tiki dir.
On my browser i browse to localhost and i get displayed the index of page and i see the tiki directory and when i click on the directory i get 403 - Forbidden message.
Tiki directory has a index.php file and tiki-install.php file but when i try browse these files i get 403 - Forbidden message. 
tiki directory and all files inside tiki dir is owned by www-data for user and group. What am i doing worng. Please advise....
My lighttpd conf file is the default conf file.
[PHP]
erver.modules = (
        "mod_access",
        "mod_alias",
        "mod_compress",
        "mod_redirect",
#       "mod_rewrite",
)

server.document-root        = "/var/www"
server.upload-dirs          = ( "/var/cache/lighttpd/uploads" )
server.errorlog             = "/var/log/lighttpd/error.log"
server.pid-file             = "/var/run/lighttpd.pid"
server.username             = "www-data"
server.groupname            = "www-data"

index-file.names            = ( "index.php", "index.html",
                                "index.htm", "default.htm",
                               " index.lighttpd.html" )

url.access-deny             = ( "~", ".inc" )

static-file.exclude-extensions = ( ".php", ".pl", ".fcgi" )

## Use ipv6 if available
#include_shell "/usr/share/lighttpd/use-ipv6.pl"

dir-listing.encoding        = "utf-8"
server.dir-listing          = "enable"

compress.cache-dir          = "/var/cache/lighttpd/compress/"
compress.filetype           = ( "application/x-javascript", "text/css", "text/html", "text/plain" )

include_shell "/usr/share/lighttpd/create-mime.assign.pl"
include_shell "/usr/share/lighttpd/include-conf-enabled.pl
[/PHP]

---

