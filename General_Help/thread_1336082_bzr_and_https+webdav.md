---
title: "bzr and https+webdav"
date: 2009-11-24
forum: General Help
---

### Post by tobias81 on 2009-11-24
Hey everybody,

    anybody some experience with bazaar (bzr) and https+webdav URLs?

for some reason I can't pull a bzr-rep from my companies server. I tried with all ubuntu packets and after it didn't work I tried installing the newer version from launchpad, but I get exact the same error... anybody an Idea (it works fine from my mac os x)

any help is greatly appreciated

thanks


details following:



-> cmd I'm running / trying to run:
bzr checkout --lightweight https+webdav://xxxxx:xxxx@xxxx/source/

-> I get this error:
not installing http[s]+webdav:// support (only supported for bzr 1.12 and above)
bzr: ERROR: Unsupported protocol for url "https+webdav://xxxxx:xxxx@xxxx/source/source/"



these are the versions installed  (I'm running ubuntu server kermic)

dpkg -l | grep bzr
==============

ii  bzr                                        2.0.2-1~bazaar1~karmic            easy to use distributed version control syst
ii  bzr-avahi                                  0.2+bzr36-3                       mDNS plugin for Bazaar
ii  bzr-dbus                                   0.1~bzr39-1                       D-Bus announcements plugin for Bazaar
ii  bzr-fastimport                             0.9.0~bzr188-1                    Fast-import/fast-export plugin for Bazaar
ii  bzr-search                                 1.7.0~bzr70-1                     search plugin for Bazaar
ii  bzr-svn                                    1.0.0-1~bazaar2~karmic            Bazaar plugin providing Subversion integrati
ii  bzr-webdav                                 1.12.0~bzr63-0ubuntu1             WebDAV transport support for Bazaar
ii  bzr-xmloutput                              0.8.3+bzr123-1                    XML Communication plugin for Bazaar
ii  bzrtools                                   2.0.1-1                           Collection of tools for bzr








bzr plugins
===============



not installing http[s]+webdav:// support (only supported for bzr 1.12 and above)
avahi 0.3.0dev
    Advertise and browse branches on the local network via mDNS.

bzrtools 2.0.1
    Various useful commands for working with bzr.

dbus 0.1.0dev
    D-Bus integration for bzr/bzrlib. 

fastimport 0.9.0dev
    FastImport Plugin

launchpad 2.0.2
    Launchpad.net integration plugin for Bazaar.

netrc_credential_store 2.0.2
    Use ~/.netrc as a credential store for authentication.conf.

search 1.7.0dev
    search is a bzr plugin for searching bzr content.

svn 1.0.0
    Support for Subversion branches

webdav 1.12.0
    An http transport, using webdav to allow pushing.

xmloutput 0.8.3
    This plugin provides xml output for status, log, annotate, missing, info,

---

### Post by tobias81 on 2009-12-08
if somebody cares, I fixed this myself in the meantime:

bazaar webdav plugin has a bug: it needs version 1.12 or newer, well now we're at 2.0 so the plugin hangs at seeing the minor release being <.12 (it doesn't look at the major release number) you gotta add that to the source of the pluging

---

### Post by cben on 2009-12-31
Thanks, tobias!

Turns out it's fixed in revision 64 (tobias81), still not released in ubuntu.

---

### Post by rmessier on 2011-07-20
Still not fixed in latest Ubuntu release. In case someone is interested, here's how I fixed it in Ubuntu 11.04:

[LIST=1]
[*]navigate to bzr-webdav plugin folder (usually located in /usr/share/pyshared/bzrlib/plugins/webdav)
[*]edit file __init__.py
[*]change line 31 from ```
if major < 1 or minor < 12:
``` to ```
if (major < 1) or (major == 1 and minor < 12):
```
[/LIST]

---

