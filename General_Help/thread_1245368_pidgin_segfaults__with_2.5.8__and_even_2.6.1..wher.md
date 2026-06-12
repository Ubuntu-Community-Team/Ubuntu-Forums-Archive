---
title: "pidgin segfaults  with 2.5.8  and even 2.6.1..where are the developers?"
date: 2009-08-20
forum: General Help
---

### Post by dumblebee100 on 2009-08-20
[SIZE="4"]This bug was solved when I used the same pidgin version 2.6.1 in karmic alpha 4[/SIZE]


I used the pidgin 2.5.6 it worked fine 
--------------------------------------------------------------------------

when I upgraded to 2.5.8 google talk always crashes pidgin ...I mean segmentation fault ...this bug is is one hell of a bug which developers forgot I think so ...when there is no main module working at all then whats the fun of developing inner code for improvements
---------------------------------------------------------------------------
out of curiosity I tried the latest 2.6.1 ....whats the result ..

the history repeats itself 
--------------------------------------------------------------------------

when Im coding my project in my academics I got a null pointer error ...then some experienced person said that this error was worst error a programmer can make ....

I feel the same with segmentation fault ( code dumped ) error 

I would also like to present my debug log 
```
(22:52:53) prefs: Reading /home/sam/.purple/prefs.xml
(22:52:53) prefs: Finished reading /home/sam/.purple/prefs.xml
(22:52:53) dbus: okkk
(22:52:53) plugins: probing /usr/lib/pidgin/themeedit.so
(22:52:53) plugins: probing /usr/lib/pidgin/sendbutton.so
(22:52:53) plugins: probing /usr/lib/pidgin/ticker.so
(22:52:53) plugins: probing /usr/lib/pidgin/timestamp.so
(22:52:53) plugins: probing /usr/lib/pidgin/xmppconsole.so
(22:52:53) plugins: probing /usr/lib/pidgin/pidginrc.so
(22:52:53) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(22:52:53) plugins: probing /usr/lib/pidgin/gestures.so
(22:52:53) plugins: probing /usr/lib/pidgin/extplacement.so
(22:52:53) plugins: probing /usr/lib/pidgin/notify.so
(22:52:53) plugins: probing /usr/lib/pidgin/markerline.so
(22:52:53) plugins: probing /usr/lib/pidgin/spellchk.so
(22:52:53) plugins: probing /usr/lib/pidgin/convcolors.so
(22:52:53) plugins: probing /usr/lib/pidgin/xmppdisco.so
(22:52:53) plugins: probing /usr/lib/pidgin/musicmessaging.so
(22:52:53) plugins: probing /usr/lib/pidgin/gevolution.so
(22:52:53) plugins: probing /usr/lib/pidgin/iconaway.so
(22:52:53) plugins: probing /usr/lib/pidgin/cap.so
(22:52:53) plugins: probing /usr/lib/pidgin/nautilus.so
(22:52:53) plugins: probing /usr/lib/pidgin/history.so
(22:52:53) plugins: probing /usr/lib/pidgin/timestamp_format.so
(22:52:53) plugins: probing /usr/lib/purple-2/joinpart.so
(22:52:53) plugins: probing /usr/lib/purple-2/libnovell.so
(22:52:53) plugins: probing /usr/lib/purple-2/dbus-example.so
(22:52:53) plugins: probing /usr/lib/purple-2/libbonjour.so
(22:52:53) plugins: probing /usr/lib/purple-2/libjabber.so
(22:52:53) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:52:53) plugins: probing /usr/lib/purple-2/libirc.so
(22:52:53) plugins: probing /usr/lib/purple-2/libsametime.so
(22:52:53) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(22:52:53) plugins: probing /usr/lib/purple-2/libmyspace.so
(22:52:53) plugins: probing /usr/lib/purple-2/ssl-nss.so
(22:52:53) plugins: probing /usr/lib/purple-2/libqq.so
(22:52:53) plugins: probing /usr/lib/purple-2/liboscar.so
(22:52:53) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:52:53) plugins: probing /usr/lib/purple-2/libymsg.so
(22:52:53) plugins: /usr/lib/purple-2/libymsg.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:52:53) plugins: probing /usr/lib/purple-2/libyahoo.so
(22:52:53) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(22:52:53) plugins: probing /usr/lib/purple-2/libxmpp.so
(22:52:53) util: Reading file xmpp-caps.xml from directory /home/sam/.purple
(22:52:53) util: File /home/sam/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(22:52:53) jabber: creating hash tables for data objects
(22:52:53) plugins: probing /usr/lib/purple-2/libsimple.so
(22:52:53) plugins: probing /usr/lib/purple-2/libicq.so
(22:52:53) plugins: probing /usr/lib/purple-2/offlinemsg.so
(22:52:53) plugins: probing /usr/lib/purple-2/autoaccept.so
(22:52:53) plugins: probing /usr/lib/purple-2/idle.so
(22:52:53) plugins: probing /usr/lib/purple-2/psychic.so
(22:52:53) plugins: probing /usr/lib/purple-2/libzephyr.so
(22:52:53) plugins: probing /usr/lib/purple-2/libaim.so
(22:52:53) plugins: probing /usr/lib/purple-2/buddynote.so
(22:52:53) plugins: probing /usr/lib/purple-2/libyahoojp.so
(22:52:53) plugins: probing /usr/lib/purple-2/ssl.so
(22:52:53) plugins: probing /usr/lib/purple-2/newline.so
(22:52:53) plugins: probing /usr/lib/purple-2/perl.so
(22:52:53) plugins: probing /usr/lib/purple-2/statenotify.so
(22:52:53) plugins: probing /usr/lib/purple-2/libmsn.so
(22:52:53) plugins: probing /usr/lib/purple-2/libgg.so
(22:52:53) plugins: probing /usr/lib/purple-2/log_reader.so
(22:52:53) plugins: probing /usr/lib/purple-2/tcl.so
(22:52:53) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(22:52:53) prefs: /purple/status/scores/offline changed, scheduling save.
(22:52:53) prefs: /purple/status/scores/available changed, scheduling save.
(22:52:53) prefs: /purple/status/scores/invisible changed, scheduling save.
(22:52:53) prefs: /purple/status/scores/away changed, scheduling save.
(22:52:53) prefs: /purple/status/scores/extended_away changed, scheduling save.
(22:52:53) prefs: /purple/status/scores/idle changed, scheduling save.
(22:52:53) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(22:52:53) util: Reading file accounts.xml from directory /home/sam/.purple
(22:52:53) util: Reading file status.xml from directory /home/sam/.purple
(22:52:53) certificate: CertificateVerifier x509, singleuse requested but not found.
(22:52:53) certificate: CertificateVerifier singleuse registered
(22:52:53) certificate: CertificatePool x509, ca requested but not found.
(22:52:53) certificate: CertificateScheme x509 requested but not found.
(22:52:53) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(22:52:53) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(22:52:53) certificate: CertificatePool ca registered
(22:52:53) certificate: CertificatePool x509, tls_peers requested but not found.
(22:52:53) certificate: CertificatePool tls_peers registered
(22:52:53) certificate: CertificateVerifier x509, tls_cached requested but not found.
(22:52:53) certificate: CertificateVerifier tls_cached registered
(22:52:53) prefs: /purple/logging/format changed, scheduling save.
(22:52:53) prefs: /purple/logging/format changed, scheduling save.
(22:52:53) prefs: /purple/proxy/type changed, scheduling save.
(22:52:53) prefs: /purple/proxy/host changed, scheduling save.
(22:52:53) prefs: /purple/proxy/port changed, scheduling save.
(22:52:53) prefs: /purple/proxy/username changed, scheduling save.
(22:52:53) prefs: /purple/proxy/password changed, scheduling save.
(22:52:53) certificate: CertificateScheme x509 requested but not found.
(22:52:53) certificate: CertificateScheme x509 registered
(22:52:53) util: Reading file smileys.xml from directory /home/sam/.purple
(22:52:53) util: File /home/sam/.purple/smileys.xml does not exist (this is not necessarily an error)
(22:52:53) stun: using server 
(22:52:53) prefs: purple_prefs_get_string: Unknown pref /pidgin/icon/status/theme
(22:52:53) sound: Initializing sound output drivers.
(22:52:53) prefs: /pidgin/conversations/placement changed, scheduling save.
(22:52:54) gtkblist: added visibility manager: 1
(22:52:54) docklet: created
(22:52:54) util: Reading file blist.xml from directory /home/sam/.purple
(22:52:54) plugins: Loading saved plugin /usr/lib/purple-2/dbus-example.so
(22:52:54) plugins: Loading saved plugin /usr/lib/pidgin/gevolution.so
(22:52:54) plugins: Loading saved plugin /usr/lib/purple-2/ssl-nss.so
(22:52:54) plugins: Loading saved plugin /usr/lib/pidgin/nautilus.so
(22:52:54) nautilus: saved blist online
(22:52:54) plugins: Loading saved plugin /usr/lib/purple-2/ssl.so
(22:52:54) plugins: Loading saved plugin /usr/lib/pidgin/sendbutton.so
(22:52:54) pounce: Error reading pounces: Failed to open file '/home/sam/.purple/pounces.xml': No such file or directory
(22:52:54) Session Management: ICE initialized.
(22:52:54) Session Management: Connecting with no previous ID
(22:52:54) Session Management: Handling new ICE connection... 
(22:52:54) done.
(22:52:54) Session Management: Connected to manager (gnome-session) with client ID xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
(22:52:54) Session Management: Using pidgin as command
(22:52:55) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(22:52:55) dbus: The signal "gtkblist-unhiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(22:52:55) Session Management: Received first save_yourself
(22:52:55) util: requesting to fetch a URL
(22:52:55) dns: DNS query for '192.168.2.1' queued
(22:52:55) Session Management: Received save_complete
(22:52:55) dnsquery: IP resolved for 192.168.2.1
(22:52:55) proxy: Attempting connection to 192.168.2.1
(22:52:55) proxy: Connecting to 192.168.2.1:80 with no proxy
(22:52:55) proxy: Connection in progress
(22:52:55) docklet: embedded
(22:52:59) util: Writing file prefs.xml to directory /home/sam/.purple
(22:52:59) util: Writing file /home/sam/.purple/prefs.xml
(22:53:00) util: Writing file blist.xml to directory /home/sam/.purple
(22:53:00) util: Writing file /home/sam/.purple/blist.xml
(22:53:16) account: Connecting to account vbsamapth@gmail.com/.
(22:53:16) connection: Connecting. gc = 0x973efc8
(22:53:16) dnssrv: querying SRV record for gmail.com: _xmpp-client._tcp.gmail.com
(22:53:16) dnssrv: found 5 SRV entries
(22:53:16) dns: DNS query for 'talk.l.google.com' queued
(22:53:16) dns: Created new DNS child 16143, there are now 1 children.
(22:53:16) dns: Successfully sent DNS request to child 16143
(22:53:16) dns: Got response for 'talk.l.google.com'
(22:53:16) dnsquery: IP resolved for talk.l.google.com
(22:53:16) proxy: Attempting connection to 74.125.155.125
(22:53:16) proxy: Connecting to talk.l.google.com:5222 with no proxy
(22:53:16) proxy: Connection in progress
(22:53:16) proxy: Connecting to talk.l.google.com:5222.
(22:53:16) proxy: Connected to talk.l.google.com:5222.
(22:53:16) jabber: Sending: <?xml version='1.0' ?>
(22:53:16) jabber: Sending: <stream:stream to='gmail.com' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
(22:53:17) jabber: Recv (138): <stream:stream from="gmail.com" id="xxxxxxxxxxxx" version="1.0" xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client">
(22:53:17) jabber: Recv (210): <stream:features><starttls xmlns="urn:ietf:params:xml:ns:xmpp-tls"><required/></starttls><mechanisms xmlns="urn:ietf:params:xml:ns:xmpp-sasl"><mechanism>X-GOOGLE-TOKEN</mechanism></mechanisms></stream:features>
(22:53:17) jabber: Sending: <starttls xmlns='urn:ietf:params:xml:ns:xmpp-tls'/>
(22:53:17) jabber: Recv (50): <proceed xmlns="urn:ietf:params:xml:ns:xmpp-tls"/>
(22:53:18) nss: subject=CN=gmail.com,O=Google Inc.,L=Mountain View,ST=California,C=US issuer=OU=Equifax Secure Certificate Authority,O=Equifax,C=US
(22:53:18) nss: subject=OU=Equifax Secure Certificate Authority,O=Equifax,C=US issuer=OU=Equifax Secure Certificate Authority,O=Equifax,C=US
(22:53:18) certificate/x509/tls_cached: Starting verify for gmail.com
(22:53:18) certificate/x509/tls_cached: Checking for cached cert...
(22:53:18) certificate/x509/tls_cached: ...Found cached cert
(22:53:18) nss/x509: Loading certificate from /home/sam/.purple/certificates/x509/tls_peers/gmail.com
(22:53:18) certificate/x509/tls_cached: Peer cert matched cached
(22:53:18) certificate: Successfully verified certificate for gmail.com
dns[16143]: Oops, father has gone, wait for me, wait...!
Segmentation fault (core dumped)

```

for your extra information I cleaned every instance of pidgin and related things and I installed again with these packages pidgin pidgin-data libpurple0 libpurple-bin ..downloaded from getdeb

all I think is the error related to dns and not the core of pidgin .so is there any workaround for this major problem

---

### Post by philinux on 2009-08-20
Sounds like you need to visit launchpad and raise a bug.

2.5.5 works fine on jaunty.

---

### Post by dumblebee100 on 2009-08-21
if somebody has working pidgin 2.6.1 with googletalk in your accounts then please tell me how did u do that ..

all the problem resides on the dns issue ..I donno what really happening ..if you could assist ...it will be helpful

---

