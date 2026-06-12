---
title: "some program still running after logout"
date: 2010-06-22
forum: General Help
---

### Post by nolith on 2010-06-22
Hi,

I'm experiencing a strange behavior with lucid.

The computer is always on, and I simply log-in and out without shiching off the pc.

Today I logged-in with a different user and found a lot of programs  running with my old (logged-off) user.

```

# who
adminars pts/0        2010-06-22 11:06 (pc-ars32.arsanita.toscana.it)

```

```

#ps aux | grep alecai
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
alecai    1732  0.0  0.3  78356  3744 ?        Sl   Jun17   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=32
alecai    1873  0.0  0.0   1828   380 ?        S    Jun17   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/etc/xdg/desktop-couch/compulsory-auth.ini\" -a \"/home/alecai/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/alecai/.cache/desktop-couch/desktop-couchdb.pid -o /home/alecai/.cache/desktop-couch/desktop-couchdb.stdout -e /home/alecai/.cache/desktop-couch/desktop-couchdb.stderr -R
alecai    1911  0.0  0.0   1828   156 ?        S    Jun17   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/etc/xdg/desktop-couch/compulsory-auth.ini\" -a \"/home/alecai/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/alecai/.cache/desktop-couch/desktop-couchdb.pid -o /home/alecai/.cache/desktop-couch/desktop-couchdb.stdout -e /home/alecai/.cache/desktop-couch/desktop-couchdb.stderr -R
alecai    1912  0.0  0.7  36016  7764 ?        S    Jun17   1:57 /usr/lib/erlang/erts-5.7.4/bin/beam -Bd -K true -- -root /usr/lib/erlang -progname erl -- -home /home/alecai -- -noshell -noinput -smp auto -sasl errlog_type error -pa /usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin /usr/lib/couchdb/erlang/lib/mochiweb-r97/ebin /usr/lib/couchdb/erlang/lib/ibrowse-1.5.2/ebin /usr/lib/couchdb/erlang/lib/erlang-oauth/ebin -eval application:load(ibrowse) -eval application:load(oauth) -eval application:load(crypto) -eval application:load(couch) -eval crypto:start() -eval ssl:start() -eval ibrowse:start() -eval couch_server:start([ "/etc/couchdb/default.ini", "/etc/xdg/desktop-couch/compulsory-auth.ini", "/home/alecai/.config/desktop-couch/desktop-couchdb.ini"]), receive done -> done end. -pidfile /home/alecai/.cache/desktop-couch/desktop-couchdb.pid -heart
alecai    1916  0.0  0.0   1616   388 ?        Ss   Jun17   0:00 heart -pid 1912 -ht 11
alecai    1920  0.0  0.5  17352  5692 ?        SN   Jun17   2:43 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
alecai    1965  0.0  0.1  19464  1944 ?        Ssl  Jun17   0:05 /usr/lib/couchdb/bin/couchjs /usr/share/couchdb/server/main.js
alecai    3426  0.0  0.3  79392  3700 ?        Sl   Jun18   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=23
alecai    3510  0.0  0.5  17344  5644 ?        SN   Jun18   2:34 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
alecai   10828  0.0  0.3  79372  3696 ?        Sl   Jun21   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=32
alecai   10931  0.0  0.5  17016  5656 ?        SN   Jun21   1:00 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
adminars 13544  0.0  0.0   3340   828 pts/0    S+   11:13   0:00 grep --color=auto alecai
alecai   20247  0.0  0.6  17016  6556 ?        SN   Jun21   0:35 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
alecai   20781  0.0  0.4  78372  4224 ?        Sl   Jun21   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=31
alecai   20867  0.0  0.6  17020  6396 ?        SN   Jun21   0:35 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
alecai   24701  0.0  0.3  78360  4064 ?        Sl   09:53   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=32
alecai   24802  0.1  0.6  17020  6364 ?        SN   09:54   0:05 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
alecai   26219  0.0  0.6  78372  6448 ?        Sl   10:06   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=30
alecai   26308  0.0  0.9  17020 10084 ?        SN   10:06   0:03 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service

```

Any hints?


Bye

---

### Post by bobcollard on 2010-06-22
From the looks of things most of this is your desktop and lib data for it.  It is common for a system to load up things it needs to run.

---

### Post by nolith on 2010-06-22
> **bobcollard said:**
> From the looks of things most of this is your desktop and lib data for it.  It is common for a system to load up things it needs to run.

Is common to have 7 process for /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service associated to an user which isn't logged-in?

When you log out they didn't die, but the restarts when you log-in

---

### Post by bobcollard on 2010-06-22
> **nolith said:**
> Is common to have 7 process for /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service associated to an user which isn't logged-in?

When you log out they didn't die, but the restarts when you log-in
What desktop are you using when you log in with second user?

---

### Post by nolith on 2010-06-22
> **bobcollard said:**
> What desktop are you using when you log in with second user?

ssh from a remote machine.
I'm using another user to be sure to not trigger any startup script related to the first one.

---

### Post by bobcollard on 2010-06-22
> **nolith said:**
> ssh from a remote machine.
I'm using another user to be sure to not trigger any startup script related to the first one.
Sorry, my point is that a desktop is begun before login, otherwise you would not have anything to take your username and password.  If you changed your desktop from, say, KDE to Xfce or gnome, you would still have something waiting for you at startup.

---

### Post by nolith on 2010-06-22
I logged in with gdm, and gnome, with the user alecai on Jun 17, 18, 21 and today.
I never switched off the pc, I had terminated the sessions.

Today I noticed too many process related to alecai, so I termited my session and logged in throgh ssh from another machine, with another user (adminars) and I listed the alecai's running process.

These process where not supposed to be running and as you can see they are aproximatively the same, one for login session (with some excpetion).

---

### Post by bobcollard on 2010-06-22
> **nolith said:**
> I logged in with gdm, and gnome, with the user alecai on Jun 17, 18, 21 and today.
I never switched off the pc, I had terminated the sessions.

Today I noticed too many process related to alecai, so I termited my session and logged in throgh ssh from another machine, with another user (adminars) and I listed the alecai's running process.

These process where not supposed to be running and as you can see they are aproximatively the same, one for login session (with some excpetion).
Yeah, I have no other explanation.

---

