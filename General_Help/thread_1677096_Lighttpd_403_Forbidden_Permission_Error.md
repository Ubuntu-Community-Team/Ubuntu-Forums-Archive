---
title: "Lighttpd 403 Forbidden Permission Error"
date: 2011-01-28
forum: General Help
---

### Post by Peter_APIIT on 2011-01-28
Hello to all, 

i have installed the lighttpd server but i get 403 forbidden error during loading of php file. 

I do have php5, php5-cgi installed. 

The lighttpd server is running using user www-data.
Is it the user who logged in has no access to the /var/www file. 


My /etc/lighttpd/lighttpd.conf

```

# Debian lighttpd configuration file
#

############ Options you really have to take care of ####################

## modules to load
server.modules = (
            "mod_alias",
            "mod_compress",
	    "mod_fastcgi",	
#	    "mod_userdir",	
#           "mod_rewrite",
#           "mod_redirect",
#           "mod_usertrack",
#           "mod_expire",
#           "mod_flv_streaming",
#           "mod_evasive"
)

## a static document-root, for virtual-hosting take look at the
## server.virtual-* options
server.document-root       = "/var/www/"
#server.document-root = "/home/peterwkc/Desktop/www"


## where to upload files to, purged daily.
server.upload-dirs = ( "/var/cache/lighttpd/uploads" )

## where to send error-messages to
server.errorlog            = "/var/log/lighttpd/error.log"

## files to check for if .../ is requested
index-file.names           = ( "index.php", "index.html",
                               "index.htm", "default.htm",
                               "index.lighttpd.html" )


## Use the "Content-Type" extended attribute to obtain mime type if possible
# mimetype.use-xattr = "enable"

##
# which extensions should not be handle via static-file transfer
#
# .php, .pl, .fcgi are most often handled by mod_fastcgi or mod_cgi
static-file.exclude-extensions = ( ".php", ".pl", ".fcgi" )
#static-file.exclude-extensions = (".pl", ".fcgi")

######### Options that are good to be but not neccesary to be changed #######

## Use ipv6 only if available. (disabled for while, check #560837)
#include_shell "/usr/share/lighttpd/use-ipv6.pl"

## bind to port (default: 80)
# server.port               = 81

## bind to localhost only (default: all interfaces)
## server.bind                = "localhost"

## error-handler for status 404
#server.error-handler-404  = "/error-handler.html"
#server.error-handler-404  = "/error-handler.php"

## to help the rc.scripts
server.pid-file            = "/var/run/lighttpd.pid"

##
## Format: <errorfile-prefix><status>.html
## -> ..../status-404.html for 'File not found'
#server.errorfile-prefix    = "/var/www/"

## virtual directory listings
dir-listing.encoding        = "utf-8"
server.dir-listing          = "enable"

### only root can use these options
#
# chroot() to directory (default: no chroot() )
#server.chroot            = "/"

## change uid to <uid> (default: don't change)
server.username            = "www-data"

## change gid to <gid> (default: don't change)
server.groupname           = "www-data"

#### compress module
compress.cache-dir          = "/var/cache/lighttpd/compress/"
compress.filetype           = ("text/plain", "text/html", "application/x-javascript", "text/css")

#### url handling modules (rewrite, redirect, access)
# url.rewrite                 = ( "^/$"             => "/server-status" )
# url.redirect                = ( "^/wishlist/(.+)" => "http://www.123.org/$1" )

#### expire module
# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### external configuration files
## mimetype mapping
include_shell "/usr/share/lighttpd/create-mime.assign.pl"

## load enabled configuration files,
## read /etc/lighttpd/conf-available/README first
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"

#userdir.path = "/home/peterwkc/Desktop/www/www/"
debug-log-request-handling = "enable"
dir-listing.activate = "enable"

url.access.deny = ("~", ".inc")

#fastcgi.server = (“.php” => ((
#“bin-path” => “/usr/bin/php5-cgi”,
#“socket” => “/tmp/php.socket”
#)))

```


Please help. 


Thanks.

---

### Post by Peter_APIIT on 2011-01-31
I not intend to bump the thread but just required a solution for this problem. 

Thanks.

---

### Post by ionplay on 2012-04-18
had the same problem on fresh lighttpd on ubuntu 10.04 install

triple checked permissions
and copying fastcgi.conf to enabled directory
etc....

ultimately the modules were not loaded (not sure how or why), but executed the following and it works properly now

sudo lighttpd-enable-mod fastcgi fastcgi-php

hope this helps anyone else landing on this page

---

### Post by oldos2er on 2012-04-18
Closed. Please do not bump old threads.

---

