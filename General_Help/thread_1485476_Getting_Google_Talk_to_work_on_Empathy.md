---
title: "Getting Google Talk to work on Empathy"
date: 2010-05-16
forum: General Help
---

### Post by Bradj47 on 2010-05-16
Every time I open up Empathy I get a red bar at the top of my buddy list that says "Network Error" with the Google Talk logo next to it. I did some Googling and it said that if I change the server name to talk.google.com, the port number to 5223, and check the "Use old SSL" box it would work. It didn't. I still get the same error. But that's what every site I found told me to do. So now what? I'm using Ubuntu 10.04 Netbook Remix using a LAN connection, if it matters.

---

### Post by snahrck on 2010-05-19
I have the same problem no matter what configuration I try.
Just to see if there was a firewall or something like that blocking my connection I tried the google's gtalk running under virtual box and it connects just fine on this machine.

Here I paste some gabber logs:

default options (just created Google Talk account)
```

tp-glib-DEBUG: 19-05-2010 13:32:13.542414: started version 0.8.12 (telepathy-glib version 0.10.1)
gabble/connection-DEBUG: 19-05-2010 13:32:13.543111: gabble_connection_class_init: Initializing (GabbleConnectionClass *)0x8dbb4c0
gabble/connection-DEBUG: 19-05-2010 13:32:13.543287: gabble_connection_init: Initializing (GabbleConnection *)0x8dc1008
gabble/muc-DEBUG: 19-05-2010 13:32:13.543783: gabble_roomlist_manager_constructed: 0x8db35b8
gabble/connection-DEBUG: 19-05-2010 13:32:13.544971: gabble_connection_constructor: Post-construction: (GabbleConnection *)0x8dc1008
gabble/jid-DEBUG: 19-05-2010 13:32:13.545206: gabble_signal_connect_weak: connecting to 0x8db57c0:item-found with context 0x8db0380
gabble/jid-DEBUG: 19-05-2010 13:32:13.545213: gabble_signal_connect_weak: connecting to 0x8dc1008:status-changed with context 0x8db0400
gabble/connection-DEBUG: 19-05-2010 13:32:13.545296: gabble_connection_constructed: defaulted resource to ecc58192
gabble/connection-DEBUG: 19-05-2010 13:32:13.552211: _gabble_connection_connect: disabling SRV because "server" or "old-ssl" was specified or port was not 5222, will connect to talk.google.com
gabble/connection-DEBUG: 19-05-2010 13:32:13.552782: do_connect: calling lm_connection_open
LM-DEBUG: 19-05-2010 13:32:13.553133: Connecting to: talk.google.com:5222
LM-DEBUG: 19-05-2010 13:32:13.553406: SRV lookup disabled for talk.google.com
LM-DEBUG: 19-05-2010 13:32:13.553669: Going to connect to talk.google.com:5222
gabble/roster-DEBUG: 19-05-2010 13:32:13.554286: connection_status_changed_cb: adding callbacks
gabble/im-DEBUG: 19-05-2010 13:32:13.554615: connection_status_changed_cb: adding callbacks
gabble/muc-DEBUG: 19-05-2010 13:32:13.554892: connection_status_changed_cb: adding callbacks
LM-DEBUG: 19-05-2010 13:32:23.603220: Trying 74.125.65.125 port 5222...
LM-DEBUG: 19-05-2010 13:32:44.602807: Connection failed.
LM-DEBUG: 19-05-2010 13:32:44.602960: Connection failed: Connection timed out (error 110)

```

All checkboxes marked
server: talk.google.com
port: 5223
```

tp-glib-DEBUG: 19-05-2010 13:29:46.484771: started version 0.8.12 (telepathy-glib version 0.10.1)
gabble/connection-DEBUG: 19-05-2010 13:29:46.485407: gabble_connection_class_init: Initializing (GabbleConnectionClass *)0x82c1d68
gabble/connection-DEBUG: 19-05-2010 13:29:46.485579: gabble_connection_init: Initializing (GabbleConnection *)0x82c8008
gabble/muc-DEBUG: 19-05-2010 13:29:46.485860: gabble_roomlist_manager_constructed: 0x82ba5b8
gabble/connection-DEBUG: 19-05-2010 13:29:46.486136: gabble_connection_constructor: Post-construction: (GabbleConnection *)0x82c8008
gabble/jid-DEBUG: 19-05-2010 13:29:46.486351: gabble_signal_connect_weak: connecting to 0x82bc7c0:item-found with context 0x82b7380
gabble/jid-DEBUG: 19-05-2010 13:29:46.486358: gabble_signal_connect_weak: connecting to 0x82c8008:status-changed with context 0x82b7400
gabble/connection-DEBUG: 19-05-2010 13:29:46.486413: gabble_connection_constructed: defaulted resource to ecc58192
LM-DEBUG: 19-05-2010 13:29:56.538706: Trying 74.125.65.125 port 5223...
LM-DEBUG: 19-05-2010 13:30:17.538808: Connection failed.
LM-DEBUG: 19-05-2010 13:30:17.538965: Connection failed: Connection timed out (error 110)

```


TSL/SSL: checked
Ignore SSL errors: checked
Use SSL: unchecked
server: talk.google.com
port: 5222
```

tp-glib-DEBUG: 19-05-2010 13:34:46.121026: started version 0.8.12 (telepathy-glib version 0.10.1)
gabble/connection-DEBUG: 19-05-2010 13:34:46.121938: gabble_connection_class_init: Initializing (GabbleConnectionClass *)0x9a16bb0
gabble/connection-DEBUG: 19-05-2010 13:34:46.126143: gabble_connection_init: Initializing (GabbleConnection *)0x9a1c008
gabble/muc-DEBUG: 19-05-2010 13:34:46.126580: gabble_roomlist_manager_constructed: 0x9a0e5b8
gabble/connection-DEBUG: 19-05-2010 13:34:46.126878: gabble_connection_constructor: Post-construction: (GabbleConnection *)0x9a1c008
gabble/jid-DEBUG: 19-05-2010 13:34:46.127095: gabble_signal_connect_weak: connecting to 0x9a107c0:item-found with context 0x9a0b380
gabble/jid-DEBUG: 19-05-2010 13:34:46.127103: gabble_signal_connect_weak: connecting to 0x9a1c008:status-changed with context 0x9a0b400
gabble/connection-DEBUG: 19-05-2010 13:34:46.127163: gabble_connection_constructed: defaulted resource to ecc58192
gabble/connection-DEBUG: 19-05-2010 13:34:46.139507: _gabble_connection_connect: disabling SRV because "server" or "old-ssl" was specified or port was not 5222, will connect to talk.google.com
gabble/connection-DEBUG: 19-05-2010 13:34:46.139605: do_connect: calling lm_connection_open
LM-DEBUG: 19-05-2010 13:34:46.139664: Connecting to: talk.google.com:5222
LM-DEBUG: 19-05-2010 13:34:46.139718: SRV lookup disabled for talk.google.com
LM-DEBUG: 19-05-2010 13:34:46.139767: Going to connect to talk.google.com:5222
gabble/roster-DEBUG: 19-05-2010 13:34:46.140166: connection_status_changed_cb: adding callbacks
gabble/im-DEBUG: 19-05-2010 13:34:46.140245: connection_status_changed_cb: adding callbacks
gabble/muc-DEBUG: 19-05-2010 13:34:46.140302: connection_status_changed_cb: adding callbacks
LM-DEBUG: 19-05-2010 13:34:56.150656: Trying 74.125.65.125 port 5222...
LM-DEBUG: 19-05-2010 13:35:17.150804: Connection failed.
LM-DEBUG: 19-05-2010 13:35:17.150960: Connection failed: Connection timed out (error 110)

```

TSL/SSL: unchecked
Ignore SSL errors: unchecked
Use SSL: checked
server: talk.google.com
port: 5223
```

gabble/connection-DEBUG: 19-05-2010 13:37:24.983926: gabble_connection_init: Initializing (GabbleConnection *)0x9a1c008
gabble/muc-DEBUG: 19-05-2010 13:37:24.984144: gabble_roomlist_manager_constructed: 0x9a0e5b8
gabble/connection-DEBUG: 19-05-2010 13:37:24.984397: gabble_connection_constructor: Post-construction: (GabbleConnection *)0x9a1c008
gabble/jid-DEBUG: 19-05-2010 13:37:24.984610: gabble_signal_connect_weak: connecting to 0x9a21c40:item-found with context 0x9a32820
gabble/jid-DEBUG: 19-05-2010 13:37:24.984700: gabble_signal_connect_weak: connecting to 0x9a1c008:status-changed with context 0x9a31b20
gabble/connection-DEBUG: 19-05-2010 13:37:24.984795: gabble_connection_constructed: defaulted resource to ecc58192
gabble/connection-DEBUG: 19-05-2010 13:37:24.997677: _gabble_connection_connect: disabling SRV because "server" or "old-ssl" was specified or port was not 5222, will connect to talk.google.com
gabble/connection-DEBUG: 19-05-2010 13:37:24.997745: do_connect: calling lm_connection_open
LM-DEBUG: 19-05-2010 13:37:24.997800: Connecting to: talk.google.com:5223
LM-DEBUG: 19-05-2010 13:37:24.997848: SRV lookup disabled for talk.google.com
LM-DEBUG: 19-05-2010 13:37:24.997898: Going to connect to talk.google.com:5223
gabble/roster-DEBUG: 19-05-2010 13:37:24.998465: connection_status_changed_cb: adding callbacks
gabble/im-DEBUG: 19-05-2010 13:37:24.998574: connection_status_changed_cb: adding callbacks
gabble/muc-DEBUG: 19-05-2010 13:37:24.998641: connection_status_changed_cb: adding callbacks
LM-DEBUG: 19-05-2010 13:37:35.15938: Trying 74.125.65.125 port 5223...
LM-DEBUG: 19-05-2010 13:37:56.14791: Connection failed.
LM-DEBUG: 19-05-2010 13:37:56.14925: Connection failed: Connection timed out (error 110)

```

Just to mention a few tries...

Anyone can help?

---

### Post by nvsbl on 2010-07-18
Anyone have any luck with this? I'm currently experiencing the same problem with GTalk and Facebook Chat. Not sure if they're related, but they both stopped working at about the same time.

---

### Post by Bradj47 on 2010-07-20
> **nvsbl said:**
> Anyone have any luck with this? I'm currently experiencing the same problem with GTalk and Facebook Chat. Not sure if they're related, but they both stopped working at about the same time.

Yeah, my Facebook chat also quit out on me. But only on my netbook. On my desktop Empathy still works fine.

---

### Post by nvsbl on 2010-07-20
> **Bradj47 said:**
> Yeah, my Facebook chat also quit out on me. But only on my netbook. On my desktop Empathy still works fine.
I got Google Talk working by instead setting my account as Jabber with a server at talk.google.com. As for the Facebook Chat, that simply seems to come and go as it pleases these days.

---

### Post by manjulapra on 2010-08-01
Quote:
I got Google Talk working by instead setting my account as Jabber with a  server at talk.google.com.

It worked fine on my Ubuntu 10.04. But Facebook, Yahoo are having the same problem. Microsoft Live connects well. Any help Facebook and Yahoo

---

### Post by Loki_Trickster on 2010-08-03
I just installed Ubuntu netbook remix at toshiba nb200. I also found problem with gtalk while using from Empathy IM client. Checking that old SSL box works for me. I can chat now.

---

