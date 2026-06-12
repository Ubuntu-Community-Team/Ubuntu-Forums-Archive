---
title: "Empathy, Pidgin: bus error"
date: 2010-07-22
forum: General Help
---

### Post by toothlost on 2010-07-22
Hello all,
 
    I have a weird problem with ubuntu 10.04 amd64...
 
       Both Pidgin and Empathy don't start either in shell or in the Applications menu


```

prene@boo:~$ empathy -v
Empathy 2.30.2
prene@boo:~$ empathy 
Bus error
prene@boo:~$ pidgin 
Bus error
prene@boo:~$ pidgin -v
Pidgin 2.6.6 (libpurple 2.6.6)
prene@boo:~$ pidgin -d
(00:38:02) prefs: Reading /home/prene/.purple/prefs.xml
(00:38:02) prefs: Reading /etc/purple/prefs.xml
(00:38:02) dbus: okkk
(00:38:02) plugins: probing /usr/lib/pidgin/markerline.so
(00:38:02) plugins: probing /usr/lib/pidgin/iconaway.so
(00:38:02) plugins: probing /usr/lib/pidgin/timestamp_format.so
(00:38:02) plugins: probing /usr/lib/pidgin/pidginrc.so
(00:38:02) plugins: probing /usr/lib/pidgin/spellchk.so
(00:38:02) plugins: probing /usr/lib/pidgin/xmppdisco.so
(00:38:02) plugins: probing /usr/lib/pidgin/sendbutton.so
(00:38:02) plugins: probing /usr/lib/pidgin/timestamp.so
(00:38:02) plugins: probing /usr/lib/pidgin/convcolors.so
(00:38:02) plugins: probing /usr/lib/pidgin/cap.so
(00:38:03) plugins: probing /usr/lib/pidgin/gevolution.so
(00:38:03) plugins: probing /usr/lib/pidgin/ticker.so
(00:38:03) plugins: probing /usr/lib/pidgin/gestures.so
(00:38:03) plugins: probing /usr/lib/pidgin/extplacement.so
(00:38:03) plugins: probing /usr/lib/pidgin/notify.so
(00:38:03) plugins: probing /usr/lib/pidgin/history.so
(00:38:03) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(00:38:03) plugins: probing /usr/lib/pidgin/musicmessaging.so
(00:38:03) plugins: probing /usr/lib/pidgin/themeedit.so
(00:38:03) plugins: probing /usr/lib/pidgin/xmppconsole.so
(00:38:03) plugins: probing /usr/lib/pidgin/vvconfig.so
(00:38:03) plugins: probing /usr/lib/purple-2/joinpart.so
(00:38:03) plugins: probing /usr/lib/purple-2/ssl.so
(00:38:03) plugins: probing /usr/lib/purple-2/libnovell.so
(00:38:03) plugins: probing /usr/lib/purple-2/libirc.so
(00:38:03) plugins: probing /usr/lib/purple-2/libicq.so
(00:38:03) plugins: probing /usr/lib/purple-2/psychic.so
(00:38:03) plugins: probing /usr/lib/purple-2/ssl-nss.so
(00:38:03) plugins: probing /usr/lib/purple-2/log_reader.so
(00:38:03) plugins: probing /usr/lib/purple-2/pidgin-libnotify.so
(00:38:03) plugins: probing /usr/lib/purple-2/libxmpp.so
(00:38:03) util: Reading file xmpp-caps.xml from directory /home/prene/.purple
(00:38:03) util: File /home/prene/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(00:38:03) jabber: creating hash tables for data objects
(00:38:03) plugins: probing /usr/lib/purple-2/buddynote.so
(00:38:03) plugins: probing /usr/lib/purple-2/libmyspace.so
(00:38:03) plugins: probing /usr/lib/purple-2/libyahoojp.so
(00:38:03) plugins: probing /usr/lib/purple-2/perl.so
(00:38:03) plugins: probing /usr/lib/purple-2/newline.so
(00:38:03) plugins: probing /usr/lib/purple-2/dbus-example.so
(00:38:03) plugins: probing /usr/lib/purple-2/libjabber.so
(00:38:03) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(00:38:03) plugins: probing /usr/lib/purple-2/autoaccept.so
(00:38:03) plugins: probing /usr/lib/purple-2/libmsn.so
(00:38:03) plugins: probing /usr/lib/purple-2/idle.so
(00:38:03) plugins: probing /usr/lib/purple-2/libgg.so
(00:38:03) plugins: probing /usr/lib/purple-2/libymsg.so
(00:38:03) plugins: /usr/lib/purple-2/libymsg.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(00:38:03) plugins: probing /usr/lib/purple-2/libsimple.so
(00:38:03) plugins: probing /usr/lib/purple-2/libbonjour.so
(00:38:03) plugins: probing /usr/lib/purple-2/libaim.so
(00:38:03) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(00:38:03) plugins: probing /usr/lib/purple-2/statenotify.so
(00:38:03) plugins: probing /usr/lib/purple-2/tcl.so
(00:38:03) plugins: probing /usr/lib/purple-2/libzephyr.so
(00:38:03) plugins: probing /usr/lib/purple-2/libsametime.so
(00:38:03) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(00:38:03) plugins: probing /usr/lib/purple-2/liboscar.so
(00:38:03) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(00:38:03) plugins: probing /usr/lib/purple-2/libqq.so
(00:38:03) plugins: probing /usr/lib/purple-2/offlinemsg.so
(00:38:03) plugins: probing /usr/lib/purple-2/libyahoo.so
(00:38:03) plugins: probing /usr/lib/purple-2/libmxit.so
(00:38:03) prpl-loubserp-mxit: Loading MXit libPurple plugin...
(00:38:03) prefs: /purple/status/scores/offline changed, scheduling save.
(00:38:03) prefs: /purple/status/scores/available changed, scheduling save.
(00:38:03) prefs: /purple/status/scores/invisible changed, scheduling save.
(00:38:03) prefs: /purple/status/scores/away changed, scheduling save.
(00:38:03) prefs: /purple/status/scores/extended_away changed, scheduling save.
(00:38:03) prefs: /purple/status/scores/idle changed, scheduling save.
(00:38:03) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(00:38:03) util: Reading file accounts.xml from directory /home/prene/.purple
(00:38:03) util: File /home/prene/.purple/accounts.xml does not exist (this is not necessarily an error)
(00:38:03) util: Reading file status.xml from directory /home/prene/.purple
(00:38:03) util: File /home/prene/.purple/status.xml does not exist (this is not necessarily an error)
(00:38:03) certificate: CertificateVerifier x509, singleuse requested but not found.
(00:38:03) certificate: CertificateVerifier singleuse registered
(00:38:03) certificate: CertificatePool x509, ca requested but not found.
(00:38:03) certificate: CertificateScheme x509 requested but not found.
(00:38:03) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(00:38:03) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(00:38:03) certificate: CertificatePool ca registered
(00:38:03) certificate: CertificatePool x509, tls_peers requested but not found.
(00:38:03) certificate: CertificatePool tls_peers registered
(00:38:03) certificate: CertificateVerifier x509, tls_cached requested but not found.
(00:38:03) certificate: CertificateVerifier tls_cached registered
(00:38:03) prefs: /purple/logging/format changed, scheduling save.
(00:38:03) prefs: /purple/logging/format changed, scheduling save.
(00:38:03) prefs: /purple/proxy/type changed, scheduling save.
(00:38:03) prefs: /purple/proxy/host changed, scheduling save.
(00:38:03) prefs: /purple/proxy/port changed, scheduling save.
(00:38:03) prefs: /purple/proxy/username changed, scheduling save.
(00:38:03) prefs: /purple/proxy/password changed, scheduling save.
(00:38:03) certificate: CertificateScheme x509 requested but not found.
(00:38:03) certificate: CertificateScheme x509 registered
(00:38:03) util: Reading file smileys.xml from directory /home/prene/.purple
(00:38:03) util: File /home/prene/.purple/smileys.xml does not exist (this is not necessarily an error)
(00:38:03) stun: using server 
(00:38:03) sound: Initializing sound output drivers.
Bus error

```
If somebody has the same problem or can point me in the right direction to fix this...
 
 I've tried to compile the latest empathy source, but I got a "glib-compile-schemas not found" error which I haven't found a solution yet to fix..
 
 But since, both Pidgin and Empathy don't work, I'm more suspecting a problem with Ubuntu... I'm open to any suggestions...


Thanks a lot,

---

