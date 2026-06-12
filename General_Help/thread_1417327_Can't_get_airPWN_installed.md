---
title: "Can't get airPWN installed"
date: 2010-02-27
forum: General Help
---

### Post by Scrubru on 2010-02-27
I tried to install airPWN following the tutorial made by Tim Ashley

[Installing AirPWN on Ubuntu Linux]("http://www.timashley.me/node/100")

it doesn't work.

When I tried to do ./configure in the LORCON dir, I got the following messages

```
checking linux/if_arp.h usability... no
checking linux/if_arp.h presence... yes
configure: WARNING: linux/if_arp.h: present but cannot be compiled
configure: WARNING: linux/if_arp.h:     check for missing prerequisite headers?
configure: WARNING: linux/if_arp.h: see the Autoconf documentation
configure: WARNING: linux/if_arp.h:     section "Present But Cannot Be Compiled"
configure: WARNING: linux/if_arp.h: proceeding with the preprocessor's result
configure: WARNING: linux/if_arp.h: in the future, the compiler will take precedence
checking for linux/if_arp.h... yes
checking linux/wireless.h usability... no
checking linux/wireless.h presence... yes
configure: WARNING: linux/wireless.h: present but cannot be compiled
configure: WARNING: linux/wireless.h:     check for missing prerequisite headers?
configure: WARNING: linux/wireless.h: see the Autoconf documentation
configure: WARNING: linux/wireless.h:     section "Present But Cannot Be Compiled"
configure: WARNING: linux/wireless.h: proceeding with the preprocessor's result
configure: WARNING: linux/wireless.h: in the future, the compiler will take precedence
checking for linux/wireless.h... yes
configure: WARNING: Missing libnl or libnl too old support will not be able to control mac80211 vaps
configure: WARNING: Missing libnl netlink library will not be able to control mac80211 vaps
no netlink support for mac80211 will not be able to control mac80211 vaps
```

I moved on to make and make install despite of those messages.

```
wtinject.c: In function ‘wtinj_selfack’:
wtinject.c:178: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
wtinject.c:178: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
wtinject.c:193: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
wtinject.c:193: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
```

```
mwnginject.c: In function ‘madwifing_close’:
mwnginject.c:85: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘void *’
mwnginject.c:85: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘void *’
mwnginject.c: In function ‘madwifing_setfuncmode’:
mwnginject.c:110: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘void *’
mwnginject.c:110: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘void *’
mwnginject.c: In function ‘madwifing_selfack’:
mwnginject.c:285: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
mwnginject.c:285: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
mwnginject.c:298: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘void *’
mwnginject.c:298: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘void *’
```

```
tx80211.c: In function ‘tx80211_close’:
tx80211.c:456: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
tx80211.c:456: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
tx80211.c:472: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
tx80211.c:472: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘char *’
```

```
lorcon_decode.c: In function ‘tx80211_decodepkt’:
lorcon_decode.c:151: warning: assignment discards qualifiers from pointer target type
lorcon_decode.c:160: warning: assignment discards qualifiers from pointer target type
lorcon_decode.c:163: warning: assignment discards qualifiers from pointer target type
lorcon_decode.c:168: warning: assignment discards qualifiers from pointer target type
lorcon_decode.c:173: warning: assignment discards qualifiers from pointer target type
lorcon_decode.c:176: warning: assignment discards qualifiers from pointer target type
```

```
install -c .libs/liborcon-1.0.0.so /usr/local/lib/liborcon-1.0.0.so
install: cannot create regular file `/usr/local/lib/liborcon-1.0.0.so': Permission denied
make: *** [install] Error 1
```

Any Ideas?
I can't figure out what did it mean by missing headers, I've had those headers already.

Or does anyone know about any repositories containing airPWN for Karmic?

Thanks

---

### Post by Scrubru on 2010-03-01
Thanks to the efforts of Vladmir Yakovlev, airPWN now has packages for both Jaunty and Karmic.

Please visit 
[https://launchpad.net/~nagos/+archive/ppa]("https://launchpad.net/~nagos/+archive/ppa")

---

