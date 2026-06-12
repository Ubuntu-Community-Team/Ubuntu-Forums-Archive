---
title: "dungeon crawl key error"
date: 2011-08-19
forum: General Help
---

### Post by coreyscx on 2011-08-19
i added the ppa, so i was going to add the authentication key to download the new version of this game, when i typed what they said into my terminal i got this..





corey@Corey:~$ wget [http://crawl.develz.org/debian/pubkey](http://crawl.develz.org/debian/pubkey) -O - | apt-key add -
--2011-08-19 11:11:18--  [http://crawl.develz.org/debian/pubkey](http://crawl.develz.org/debian/pubkey)
Resolving crawl.develz.org... 46.4.68.88, 2a01:4f8:140:3041::2:2
Connecting to crawl.develz.org|46.4.68.88|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1735 (1.7K) [application/octet-stream]
Saving to: `STDOUT'

100%[======================================>] 1,735       --.-K/s   in 0s      

2011-08-19 11:11:19 (24.7 MB/s) - written to stdout [1735/1735]

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

---

