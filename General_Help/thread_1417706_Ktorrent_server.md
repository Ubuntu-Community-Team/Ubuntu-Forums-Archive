---
title: "Ktorrent server"
date: 2010-02-27
forum: General Help
---

### Post by sideaway on 2010-02-27
I have a server running ktorrent, it seems to crash often whenever its downloading, here's the terminal's output.

```
server@server:~$ ktorrent
kbuildsycoca running...
DCOP Cleaning up dead connections.
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
server@server:~$ kio_http_debug: WARNING: (16166) closeCacheEntry: error renaming cache entry. (/var/tmp/kdecache-server/http/e/www.ezrss.it_search_index.php_7484e040.new -> /var/tmp/kdecache-server/http/e/www.ezrss.it_search_index.php_7484e040)
kio_http_debug: WARNING: (16166) closeCacheEntry: error closing cache entry. (/var/tmp/kdecache-server/http/e/www.ezrss.it_search_index.php_7484e040.new)
kio_http_debug: WARNING: (16167) closeCacheEntry: error renaming cache entry. (/var/tmp/kdecache-server/http/e/www.ezrss.it_search_index.php_7484e040.new -> /var/tmp/kdecache-server/http/e/www.ezrss.it_search_index.php_7484e040)
kio_http_debug: WARNING: (16167) closeCacheEntry: error closing cache entry. (/var/tmp/kdecache-server/http/e/www.ezrss.it_search_index.php_7484e040.new)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x6000392
KCrash: Application 'ktorrent' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
ICE default IO error handler doing an exit(), pid = 16031, errno = 11

```

Anyone tell me what's wrong?

---

### Post by sideaway on 2010-02-27
bump :)

---

### Post by sideaway on 2010-02-28
... bumpy?

---

### Post by sideaway on 2010-03-02
I live in a constant state of hope!

---

### Post by sideaway on 2010-03-03
Bugger. PSU just died.

Ok time to upgrade for the server I think. Everything I tried isn't working, and this PSU is fluctuating between working and not working, I need something a *little* more stable. Cheers to anyone who read :)

---

