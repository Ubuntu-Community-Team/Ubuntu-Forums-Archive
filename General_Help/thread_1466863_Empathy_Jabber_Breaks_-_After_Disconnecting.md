---
title: "Empathy Jabber Breaks - After Disconnecting"
date: 2010-04-30
forum: General Help
---

### Post by tjlytle on 2010-04-30
I was excited to use empathy in 10.04; however, both in the Beta and the Full Release I experience the following. (Note: I'm using 64 bit.)

[LIST]
[*]Setup 'Wizard' adds GTalk and Facebook Chat just fine.
[*]Manually add a IRC account (can't do that from wizard).
[*]Manually add a SIP account.
[*]Enjoy that it's working, and think that the full release fixed the bug.
[*]Disconnect
[/LIST]

Then the next day.

[LIST]
[*]Set status as available.
[*]Get an ambiguous 'network-error' for GTalk and Facebook.
[*]Disable all accounts.
[*]Restart empathy, enable GTalk, get same error.
[*]Delete all accounts, restart system, go through account 'wizard', add GTalk, same error.
[*]Upgrade to dev version of Empathy, notice it's no longer in the nice messaging applet, but GTalk connects.
[*]Disconnect/Reconnect - same error.
[/LIST]

Anyone else having this problem? Seems something is breaking with Jabber on Empathy. But I can't find any related information. I'll post logs when I boot into the 10.04 installation (which I was hoping to switch to, but not so sure right now.)

---

### Post by tjlytle on 2010-04-30
Just tested on another install, same basic problem.

---

### Post by tjlytle on 2010-04-30
So confused, just tested on the two systems in question and it works fine. Perhaps some kind of weird network issue? But other gtalk clients weren't affected. 

In addition I've noticed the same pattern 3 times now.

---

### Post by fuzzel-2 on 2010-05-01
Same Problem Exactly, lemme know if you guys find an answer this is starting o tick me off. Since I used fb as my main chat client...

---

### Post by fuzzel-2 on 2010-05-02
Hey, I have no idea how this happened, but the problem 'solved itself' I was making due by just having the facebook page itself open and I left it that way for about an hour and when I returned empathy had just logged in. Just to test this I closed and opened it and did a restart and it stayed.

Don't know what happend, but something did...

---

### Post by tjlytle on 2010-05-11
Yeah, I've had success, but now it's back. Debug log doesn't seem to help that much:

For facebook:

```
connection_iq_unknown_cb: got unknown iq:
<iq id="XXX386387XXX" type="result">
 <session xmlns="urn:ietf:params:xml:ns:xmpp-session"></session>
</iq>
connection_disco_cb: got disco error, setting no features: Request for info on chat.facebook.com timed out
connection_disco_cb: didn't receive a response to our disco request: disconnect

```

For gtalk:

```

Setting up SSL...
GNUTLS negotiated compression: NULL
Sending stream header
<stream:stream version="1.0" xmlns="jabber:client" xmlns:stream="http://etherx.jabber.org/streams" to="gmail.com" id="XXXX9079XXXX">
Freeing up IOChannel and file descriptor
connection_disconnected_cb: called with reason 3
connection_disconnected_cb: unexpected; calling tp_base_connection_change_status

```

My understanding is that 'reason 3' is basically, 'error'.

Additional gtalk log - it seems there are two different patterns here (note, the above shows a disconnect even when SSL works):

```

Setting up SSL...
Could not begin SSL
*** GNUTLS handshake failed: A TLS packet with unexpected length was received.
Freeing up IOChannel and file descriptor
connection_disconnected_cb: called with reason 3
connection_disconnected_cb: unexpected; calling tp_base_connection_change_status

```

---

### Post by tjlytle on 2010-05-12
Noticed that GTalk finally connected. I wanted to get a log of a good connect so I opened the debug windows and cycled the connection. Can't connect again.

---

### Post by tjlytle on 2010-05-19
Am I the only one having these problems? 

Other Gtalk clients (on different systems) on the network connect fine (for the same account), while Empathy on 10.04 anymore usually gives a 'network error' (sometimes, but not often, it connects successfully).

---

### Post by grahams on 2010-08-27
I have the same issue, with a local jabber server but not with gtalk.

Pigdin does not have an issue with the same jabber server. Using pidgin until this is fixed

---

