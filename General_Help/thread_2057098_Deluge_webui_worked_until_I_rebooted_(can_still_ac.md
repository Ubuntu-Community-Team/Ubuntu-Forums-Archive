---
title: "Deluge webui worked until I rebooted (can still access locally)"
date: 2012-09-12
forum: General Help
---

### Post by ralewis on 2012-09-12
I seem to no longer be able to access Deluge webui within the same network.  It was working fine, I decided to reboot my platform, and now it no longer works.

I have deluged and deluge-web running on my headless box.  When I go to IP:8112 I now see:

Error 324 (net::ERR_EMPTY_RESPONSE): The server closed the connection without sending any data.

I've tried removing deluge and reinstalling with no luck.

I also have these two config files set up:

/etc/init/deluge.conf

----
start on (filesystem and networking) or runlevel [2345]
stop on runlevel [016]

env uid=****
env gid=****
env umask=022

exec start-stop-daemon -S -c $uid:$gid -k $umask -x /usr/bin/deluged -- -d
----

/etc/init/deluge-web.conf

----
start on started deluge
stop on stopping deluge

env uid=****
env gid=****
env umask=027

exec start-stop-daemon -S -c $uid:$gid -k $umask -x /usr/bin/deluge-web
----



Edit: Solved

Had to delete ~/.config/deluge

---

