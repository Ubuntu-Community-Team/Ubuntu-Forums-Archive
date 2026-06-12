---
title: "Pidgin crashes with segmentation fault"
date: 2010-02-19
forum: General Help
---

### Post by VinisLentoje on 2010-02-19
Hello, I have this problem for more than a week now.
Using Ubuntu 9.10 & Pidgin 2.5.5 (upgraded from 2.5.2 while writing this post, but it did not fix the problem)
This problem appeared after closing pidgin and trying to run it again i.e. restarting it (I have to restart it at some point after a long runtime, but that is another issue), it fully loads up (at least, it looks like it) and then instantly crashes with segmentation fault message. Judging from the first glance on the log, the crash has something to do with the windows live protocol.
Of course, I have tried searching the web and this forum for an answer, but could not find any suitable one. There is one solution I have found, that is: (re)moving the .purple folder, but that "solution" is not really an option.

Any ideas, fellow Ubuntueers?

pidgin -d  output below (had to remove a small portion of it, as it is the activity of an e-mail checker and contains confidential data. The place of the removed data is marked with a blue line):

```
vinis@g44:~$ pidgin -d
(22:32:02) prefs: Reading /home/vinis/.purple/prefs.xml
(22:32:02) prefs: Finished reading /home/vinis/.purple/prefs.xml
(22:32:02) dbus: okkk
(22:32:02) plugins: probing /usr/lib/pidgin/notify.so
(22:32:02) plugins: probing /usr/lib/pidgin/sendbutton.so
(22:32:02) plugins: probing /usr/lib/pidgin/iconaway.so
(22:32:02) plugins: probing /usr/lib/pidgin/pidgin-otr.so
(22:32:02) plugins: probing /usr/lib/pidgin/gestures.so
(22:32:02) plugins: probing /usr/lib/pidgin/spellchk.so
(22:32:02) plugins: probing /usr/lib/pidgin/cap.so
(22:32:02) plugins: probing /usr/lib/pidgin/markerline.so
(22:32:02) plugins: probing /usr/lib/pidgin/convcolors.so
(22:32:02) plugins: probing /usr/lib/pidgin/guifications.so
(22:32:02) plugins: probing /usr/lib/pidgin/timestamp_format.so
(22:32:02) plugins: probing /usr/lib/pidgin/gevolution.so
(22:32:02) plugins: probing /usr/lib/pidgin/xmppdisco.so
(22:32:02) plugins: probing /usr/lib/pidgin/xmppconsole.so
(22:32:02) plugins: probing /usr/lib/pidgin/vvconfig.so
(22:32:02) plugins: probing /usr/lib/pidgin/ticker.so
(22:32:02) plugins: probing /usr/lib/pidgin/timestamp.so
(22:32:02) plugins: probing /usr/lib/pidgin/nautilus.so
(22:32:02) plugins: probing /usr/lib/pidgin/pidginrc.so
(22:32:02) plugins: probing /usr/lib/pidgin/history.so
(22:32:02) plugins: probing /usr/lib/pidgin/extplacement.so
(22:32:02) plugins: probing /usr/lib/pidgin/musicmessaging.so
(22:32:02) plugins: probing /usr/lib/pidgin/musictracker.so
(22:32:02) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(22:32:02) plugins: probing /usr/lib/pidgin/themeedit.so
(22:32:02) plugins: probing /usr/lib/pidgin/libgadu.so
(22:32:02) plugins: /usr/lib/pidgin/libgadu.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:32:02) plugins: probing /usr/lib/purple-2/libjabber.so
(22:32:02) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:32:02) plugins: probing /usr/lib/purple-2/libnovell.so
(22:32:02) plugins: probing /usr/lib/purple-2/libaim.so
(22:32:02) plugins: probing /usr/lib/purple-2/buddynote.so
(22:32:02) plugins: probing /usr/lib/purple-2/libsimple.so
(22:32:02) plugins: probing /usr/lib/purple-2/libxmpp.so
(22:32:02) util: Reading file xmpp-caps.xml from directory /home/vinis/.purple
(22:32:02) jabber: creating hash tables for data objects
(22:32:02) plugins: probing /usr/lib/purple-2/libmsn-pecan.so
(22:32:02) plugins: probing /usr/lib/purple-2/libirc.so
(22:32:02) plugins: probing /usr/lib/purple-2/liboscar.so
(22:32:02) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:32:02) plugins: probing /usr/lib/purple-2/libyahoo.so
(22:32:02) plugins: probing /usr/lib/purple-2/dbus-example.so
(22:32:02) plugins: probing /usr/lib/purple-2/libyahoojp.so
(22:32:02) plugins: probing /usr/lib/purple-2/log_reader.so
(22:32:02) plugins: probing /usr/lib/purple-2/perl.so
(22:32:02) plugins: probing /usr/lib/purple-2/statenotify.so
(22:32:02) plugins: probing /usr/lib/purple-2/autoaccept.so
(22:32:02) plugins: probing /usr/lib/purple-2/ssl-nss.so
(22:32:02) plugins: probing /usr/lib/purple-2/libsametime.so
(22:32:02) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(22:32:02) plugins: probing /usr/lib/purple-2/libbonjour.so
(22:32:02) plugins: probing /usr/lib/purple-2/libicq.so
(22:32:02) plugins: probing /usr/lib/purple-2/libmyspace.so
(22:32:02) plugins: probing /usr/lib/purple-2/pidgin-libnotify.so
(22:32:02) plugins: probing /usr/lib/purple-2/newline.so
(22:32:02) plugins: probing /usr/lib/purple-2/tcl.so
(22:32:02) plugins: probing /usr/lib/purple-2/psychic.so
(22:32:02) plugins: probing /usr/lib/purple-2/libymsg.so
(22:32:02) plugins: /usr/lib/purple-2/libymsg.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:32:02) plugins: probing /usr/lib/purple-2/libmsn.so
(22:32:02) plugins: probing /usr/lib/purple-2/libqq.so
(22:32:02) plugins: probing /usr/lib/purple-2/libgg.so
(22:32:02) plugins: probing /usr/lib/purple-2/libmxit.so
(22:32:02) prpl-loubserp-mxit: Loading MXit libPurple plugin...
(22:32:02) plugins: probing /usr/lib/purple-2/idle.so
(22:32:02) plugins: probing /usr/lib/purple-2/libzephyr.so
(22:32:02) plugins: probing /usr/lib/purple-2/festival.so
(22:32:02) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(22:32:02) plugins: probing /usr/lib/purple-2/joinpart.so
(22:32:02) plugins: probing /usr/lib/purple-2/offlinemsg.so
(22:32:02) plugins: probing /usr/lib/purple-2/ssl.so
(22:32:02) prefs: /purple/status/scores/offline changed, scheduling save.
(22:32:02) prefs: /purple/status/scores/available changed, scheduling save.
(22:32:02) prefs: /purple/status/scores/invisible changed, scheduling save.
(22:32:02) prefs: /purple/status/scores/away changed, scheduling save.
(22:32:02) prefs: /purple/status/scores/extended_away changed, scheduling save.
(22:32:02) prefs: /purple/status/scores/idle changed, scheduling save.
(22:32:02) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(22:32:02) util: Reading file accounts.xml from directory /home/vinis/.purple
(22:32:02) util: Reading file status.xml from directory /home/vinis/.purple
(22:32:02) certificate: CertificateVerifier x509, singleuse requested but not found.
(22:32:02) certificate: CertificateVerifier singleuse registered
(22:32:02) certificate: CertificatePool x509, ca requested but not found.
(22:32:02) certificate: CertificateScheme x509 requested but not found.
(22:32:02) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(22:32:02) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(22:32:02) certificate: CertificatePool ca registered
(22:32:02) certificate: CertificatePool x509, tls_peers requested but not found.
(22:32:02) certificate: CertificatePool tls_peers registered
(22:32:02) certificate: CertificateVerifier x509, tls_cached requested but not found.
(22:32:02) certificate: CertificateVerifier tls_cached registered
(22:32:02) prefs: /purple/logging/format changed, scheduling save.
(22:32:02) prefs: /purple/logging/format changed, scheduling save.
(22:32:02) prefs: /purple/proxy/type changed, scheduling save.
(22:32:02) prefs: /purple/proxy/host changed, scheduling save.
(22:32:02) prefs: /purple/proxy/port changed, scheduling save.
(22:32:02) prefs: /purple/proxy/username changed, scheduling save.
(22:32:02) prefs: /purple/proxy/password changed, scheduling save.
(22:32:02) certificate: CertificateScheme x509 requested but not found.
(22:32:02) certificate: CertificateScheme x509 registered
(22:32:02) util: Reading file smileys.xml from directory /home/vinis/.purple
(22:32:02) util: File /home/vinis/.purple/smileys.xml does not exist (this is not necessarily an error)
(22:32:02) stun: using server 
(22:32:02) sound: Initializing sound output drivers.
(22:32:02) prefs: /pidgin/conversations/placement changed, scheduling save.
(22:32:02) gtkblist: added visibility manager: 1
(22:32:02) docklet: created
(22:32:03) gtkmedia: Registering media element types
(22:32:03) util: Reading file blist.xml from directory /home/vinis/.purple
(22:32:03) plugins: Loading saved plugin /usr/lib/purple-2/autoaccept.so
(22:32:03) plugins: Loading saved plugin /usr/lib/purple-2/statenotify.so
(22:32:03) plugins: Loading saved plugin /usr/lib/pidgin/cap.so
(22:32:03) cap: Database connection successfully made.
(22:32:03) cap: Adding plugin functionality.
(22:32:03) plugins: Loading saved plugin /usr/lib/pidgin/history.so
(22:32:03) plugins: Loading saved plugin /usr/lib/purple-2/idle.so
(22:32:03) plugins: Loading saved plugin /usr/lib/purple-2/pidgin-libnotify.so
(22:32:03) plugins: Loading saved plugin /usr/lib/purple-2/log_reader.so
(22:32:03) plugins: Loading saved plugin /usr/lib/pidgin/notify.so
(22:32:03) plugins: Loading saved plugin /usr/lib/pidgin/musictracker.so
(22:32:03) musictracker: Plugin loading.
(22:32:03) musictracker: Checking if we need to set default preferences for 8081413 on protocol Gadu-Gadu
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/string_custom_8081413_Gadu-Gadu
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/bool_custom_8081413_Gadu-Gadu
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/bool_broken_now_listening_8081413_Gadu-Gadu
(22:32:03) musictracker: Checking if we need to set default preferences for vinislentoje@gmail.com on protocol AIM
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/string_custom_vinislentoje@gmail.com_AIM
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/bool_custom_vinislentoje@gmail.com_AIM
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/bool_broken_now_listening_vinislentoje@gmail.com_AIM
(22:32:03) musictracker: Checking if we need to set default preferences for vinislentoje@gmail.com on protocol WLM
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/string_custom_vinislentoje@gmail.com_WLM
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/bool_custom_vinislentoje@gmail.com_WLM
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/bool_broken_now_listening_vinislentoje@gmail.com_WLM
(22:32:03) musictracker: Checking if we need to set default preferences for vinislentoje@gmail.com/Home on protocol XMPP
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/string_custom_vinislentoje@gmail.comHome_XMPP
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/bool_custom_vinislentoje@gmail.comHome_XMPP
(22:32:03) musictracker: build_pref: /plugins/core/musictracker/bool_broken_now_listening_vinislentoje@gmail.comHome_XMPP
(22:32:03) musictracker: Registering nowplaying command.
(22:32:03) musictracker: Plugin loaded.
(22:32:03) plugins: Loading saved plugin /usr/lib/purple-2/ssl-nss.so
(22:32:03) plugins: Loading saved plugin /usr/lib/pidgin/nautilus.so
(22:32:03) nautilus: saved blist online
(22:32:03) plugins: Loading saved plugin /usr/lib/purple-2/offlinemsg.so
(22:32:03) plugins: Loading saved plugin /usr/lib/pidgin/pidginrc.so
(22:32:03) plugins: Loading saved plugin /usr/lib/purple-2/ssl.so
(22:32:03) Session Management: ICE initialized.
(22:32:03) Session Management: Connecting with no previous ID
(22:32:03) Session Management: Handling new ICE connection... 
(22:32:03) done.
(22:32:03) Session Management: Connected to manager (gnome-session) with client ID 10c697bcc63c7349d126661152352244500000024490173
(22:32:03) Session Management: Using pidgin as command
(22:32:03) account: Connecting to account 8081413.
(22:32:03) connection: Connecting. gc = 0x32d8eb0
(22:32:03) gg: ggp_to_gg_status: Requested status = available
(22:32:03) gg: Trying to retrieve address from gg appmsg service
(22:32:03) gg: ** gg_login(0x32d8f80: [uin=8081413, async=1, ...]);
(22:32:03) gg: ** gg_resolve(0x32d9a80, 0x32d9ab4, "appmsg.gadu-gadu.pl");
(22:32:03) account: Connecting to account vinislentoje@gmail.com.
(22:32:03) connection: Connecting. gc = 0x32d9f40
(22:32:03) oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
(22:32:03) oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
(22:32:03) oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
(22:32:03) oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
(22:32:03) oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
(22:32:03) oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
(22:32:03) oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
(22:32:03) oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
(22:32:03) oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
(22:32:03) oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
(22:32:03) oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
(22:32:03) oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
(22:32:03) oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
(22:32:03) oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
(22:32:03) oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
(22:32:03) oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
(22:32:03) oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
(22:32:03) oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
(22:32:03) oscar: Adding handler for ffff/0003
(22:32:03) oscar: Adding handler for ffff/0006
(22:32:03) oscar: Adding handler for 0007/0003
(22:32:03) oscar: Adding handler for 0007/0005
(22:32:03) oscar: Adding handler for 0007/0007
(22:32:03) oscar: Adding handler for 0018/0001
(22:32:03) oscar: Adding handler for 0018/0007
(22:32:03) oscar: Adding handler for 0017/0003
(22:32:03) oscar: Adding handler for 0017/0007
(22:32:03) oscar: Adding handler for 0017/000a
(22:32:03) oscar: Adding handler for 0010/0005
(22:32:03) oscar: Adding handler for 0009/0001
(22:32:03) oscar: Adding handler for 0009/0003
(22:32:03) oscar: Adding handler for 0003/0001
(22:32:03) oscar: Adding handler for 0003/0003
(22:32:03) oscar: Adding handler for 0003/000b
(22:32:03) oscar: Adding handler for 0003/000c
(22:32:03) oscar: Adding handler for 000e/0001
(22:32:03) oscar: Adding handler for 000e/0003
(22:32:03) oscar: Adding handler for 000e/0004
(22:32:03) oscar: Adding handler for 000e/0002
(22:32:03) oscar: Adding handler for 000e/0006
(22:32:03) oscar: Adding handler for 000d/0001
(22:32:03) oscar: Adding handler for 000d/0009
(22:32:03) oscar: Adding handler for 0013/0001
(22:32:03) oscar: Adding handler for 0013/0003
(22:32:03) oscar: Adding handler for 0013/0006
(22:32:03) oscar: Adding handler for 0013/000e
(22:32:03) oscar: Adding handler for 0013/0008
(22:32:03) oscar: Adding handler for 0013/0009
(22:32:03) oscar: Adding handler for 0013/0015
(22:32:03) oscar: Adding handler for 0013/0019
(22:32:03) oscar: Adding handler for 0013/001b
(22:32:03) oscar: Adding handler for 0013/001c
(22:32:03) oscar: Adding handler for 0004/0007
(22:32:03) oscar: Adding handler for 0004/000a
(22:32:03) oscar: Adding handler for 0004/000b
(22:32:03) oscar: Adding handler for 0004/0001
(22:32:03) oscar: Adding handler for 0004/0014
(22:32:03) oscar: Adding handler for 0004/000c
(22:32:03) oscar: Adding handler for 0015/00f3
(22:32:03) oscar: Adding handler for 0015/00f2
(22:32:03) oscar: Adding handler for 0002/0003
(22:32:03) oscar: Adding handler for 0002/0006
(22:32:03) oscar: Adding handler for 0002/0001
(22:32:03) oscar: Adding handler for 0001/0001
(22:32:03) oscar: Adding handler for 0001/000f
(22:32:03) oscar: Adding handler for 0001/001f
(22:32:03) oscar: Adding handler for 0001/0021
(22:32:03) oscar: Adding handler for 0001/000a
(22:32:03) oscar: Adding handler for 0001/0005
(22:32:03) oscar: Adding handler for 0001/0013
(22:32:03) oscar: Adding handler for 0001/0010
(22:32:03) oscar: Adding handler for 0008/0002
(22:32:03) oscar: Adding handler for 000a/0001
(22:32:03) oscar: Adding handler for 000a/0003
(22:32:03) oscar: oscar_login: gc = 0x32d9f40
(22:32:03) dns: DNS query for 'login.messaging.aol.com' queued
(22:32:03) account: Connecting to account vinislentoje@gmail.com.
(22:32:03) connection: Connecting. gc = 0x32db660
(22:32:03) dns: DNS query for 'messenger.hotmail.com' queued
(22:32:03) account: Connecting to account vinislentoje@gmail.com/Home.
(22:32:03) connection: Connecting. gc = 0x32dcd20
(22:32:03) util: Writing file /home/vinis/.purple/icons/552480e2b06514bd36b9de655a9a50654a5f6f31.png
(22:32:03) dns: DNS query for 'talk.google.com' queued
(22:32:03) Session Management: Received first save_yourself
Failed to receive messages at scim_bridge_client_read_and_dispatch ()
An IOException occurred at handle_message ()
(22:32:03) gg: login_handler: session: check = 2; state = 1;
(22:32:03) gg: GG_STATE_RESOLVING
(22:32:03) gg: ** gg_watch_fd(0x32d9a80);
(22:32:03) gg: // gg_watch_fd() GG_STATE_RESOLVING
(22:32:03) gg: // gg_watch_fd() resolved, connecting to 91.197.13.212:80
(22:32:03) gg: ** gg_connect(91.197.13.212, 80, 1);
(22:32:03) gg: // gg_connect() connect() in progress
(22:32:03) gg: login_handler: session->fd = 24
(22:32:03) gg: login_handler: session: check = 1; state = 5;
(22:32:03) gg: GG_EVENT_NONE
(22:32:03) gg: ** gg_event_free(0x32de930);
(22:32:03) dns: Created new DNS child 25012, there are now 1 children.
(22:32:03) dns: Successfully sent DNS request to child 25012
(22:32:03) dns: Created new DNS child 25013, there are now 2 children.
(22:32:03) dns: Successfully sent DNS request to child 25013
(22:32:03) dns: Created new DNS child 25014, there are now 3 children.
(22:32:03) dns: Successfully sent DNS request to child 25014
(22:32:04) Session Management: Received save_complete
(22:32:04) gtkblist: added visibility manager: 2
(22:32:04) docklet: embedded
(22:32:04) dns: Got response for 'talk.google.com'
(22:32:04) dnsquery: IP resolved for talk.google.com
(22:32:04) proxy: Attempting connection to 209.85.137.125
(22:32:04) proxy: Connecting to talk.google.com:5222 with no proxy
(22:32:04) proxy: Connection in progress
(22:32:04) gg: login_handler: session: check = 1; state = 5;
(22:32:04) gg: GG_STATE_CONNECTING_HUB
(22:32:04) gg: ** gg_watch_fd(0x32d9a80);
(22:32:04) gg: // gg_watch_fd() GG_STATE_CONNECTING_HUB
(22:32:04) gg: // gg_watch_fd() connected to hub, sending query
(22:32:04) gg: => -----BEGIN-HTTP-QUERY-----
GET /appsvc/appmsg4.asp?fmnumber=8081413&version=7%2c+7%2c+0%2c+3351&fmt=2&lastmsg=0 HTTP/1.0
Host: appmsg.gadu-gadu.pl
User-Agent: Mozilla/4.7 [en] (Win98; I)
Pragma: no-cache


=> -----END-HTTP-QUERY-----
(22:32:04) gg: login_handler: session->fd = 24
(22:32:04) gg: login_handler: session: check = 2; state = 3;
(22:32:04) gg: GG_EVENT_NONE
(22:32:04) gg: ** gg_event_free(0x24afd60);
(22:32:04) dns: Got response for 'login.messaging.aol.com'
(22:32:04) dnsquery: IP resolved for login.messaging.aol.com
(22:32:04) proxy: Attempting connection to 205.188.251.43
(22:32:04) proxy: Connecting to login.messaging.aol.com:5190 with no proxy
(22:32:04) proxy: Connection in progress
(22:32:04) proxy: Connecting to talk.google.com:5222.
(22:32:04) proxy: Connected to talk.google.com:5222.
(22:32:04) jabber: Sending (vinislentoje@gmail.com/Home): <?xml version='1.0' ?>
(22:32:04) jabber: Sending (vinislentoje@gmail.com/Home): <stream:stream to='gmail.com' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
(22:32:04) dns: Got response for 'messenger.hotmail.com'
(22:32:04) dnsquery: IP resolved for messenger.hotmail.com
(22:32:04) proxy: Attempting connection to 64.4.50.62
(22:32:04) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(22:32:04) proxy: Connection in progress
(22:32:04) gg: login_handler: session: check = 2; state = 3;
(22:32:04) gg: GG_STATE_READING_DATA
(22:32:04) gg: ** gg_watch_fd(0x32d9a80);
(22:32:04) gg: // gg_watch_fd() GG_STATE_READING_DATA
(22:32:04) gg: // gg_watch_fd() received http header (HTTP/1.0 200 OK)
(22:32:04) gg: // gg_read_line() eof reached
(22:32:04) gg: // gg_watch_fd() received http data (19329 0 91.197.13.53:8074 91.197.13.53)
(22:32:04) gg: ** gg_connect(91.197.13.53, 8074, 1);
(22:32:04) gg: // gg_connect() connect() in progress
(22:32:04) gg: login_handler: session->fd = 24
(22:32:04) gg: login_handler: session: check = 1; state = 6;
(22:32:04) gg: strange event: 1
(22:32:04) gg: ** gg_event_free(0x25a31a0);
(22:32:04) jabber: Recv (138): <stream:stream from="gmail.com" id="E92E99E9B90B4573" version="1.0" xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client">
(22:32:04) jabber: Recv (210): <stream:features><starttls xmlns="urn:ietf:params:xml:ns:xmpp-tls"><required/></starttls><mechanisms xmlns="urn:ietf:params:xml:ns:xmpp-sasl"><mechanism>X-GOOGLE-TOKEN</mechanism></mechanisms></stream:features>
(22:32:04) jabber: Sending (vinislentoje@gmail.com/Home): <starttls xmlns='urn:ietf:params:xml:ns:xmpp-tls'/>
(22:32:04) jabber: Recv (50): <proceed xmlns="urn:ietf:params:xml:ns:xmpp-tls"/>
(22:32:04) gg: login_handler: session: check = 1; state = 6;
(22:32:04) gg: GG_STATE_CONNECTING_GG
(22:32:04) gg: ** gg_watch_fd(0x32d9a80);
(22:32:04) gg: // gg_watch_fd() GG_STATE_CONNECTING_GG
(22:32:04) gg: // gg_watch_fd() connected
(22:32:04) gg: login_handler: session->fd = 24
(22:32:04) gg: login_handler: session: check = 2; state = 7;
(22:32:04) gg: GG_EVENT_NONE
(22:32:04) gg: ** gg_event_free(0x3291de0);
(22:32:04) proxy: Connecting to login.messaging.aol.com:5190.
(22:32:04) proxy: Connected to login.messaging.aol.com:5190.
(22:32:04) oscar: connected to FLAP server of type 0x0017
(22:32:04) oscar: Username sent, waiting for response
(22:32:04) nss: subject=CN=gmail.com,O=Google Inc.,L=Mountain View,ST=California,C=US issuer=OU=Equifax Secure Certificate Authority,O=Equifax,C=US
(22:32:04) nss: subject=OU=Equifax Secure Certificate Authority,O=Equifax,C=US issuer=OU=Equifax Secure Certificate Authority,O=Equifax,C=US
(22:32:04) certificate/x509/tls_cached: Starting verify for talk.google.com
(22:32:04) certificate/x509/tls_cached: Checking for cached cert...
(22:32:04) certificate/x509/tls_cached: ...Found cached cert
(22:32:04) nss/x509: Loading certificate from /home/vinis/.purple/certificates/x509/tls_peers/talk.google.com
(22:32:04) certificate/x509/tls_cached: Peer cert matched cached
(22:32:04) nss/x509: Exporting certificate to /home/vinis/.purple/certificates/x509/tls_peers/talk.google.com
(22:32:04) util: Writing file /home/vinis/.purple/certificates/x509/tls_peers/talk.google.com
(22:32:04) certificate: Successfully verified certificate for talk.google.com
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/Home): <stream:stream to='gmail.com' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
(22:32:04) proxy: Connecting to messenger.hotmail.com:1863.
(22:32:04) proxy: Connected to messenger.hotmail.com:1863.
INFO io/pn_node.c:380:connect_cb() connected: conn=0x21512c0,channel=0x2318080
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: VER 1 MSNP12 CVR0
(22:32:04) gg: login_handler: session: check = 2; state = 7;
(22:32:04) gg: GG_STATE_READING_KEY
(22:32:04) gg: ** gg_watch_fd(0x32d9a80);
(22:32:04) gg: // gg_watch_fd() GG_STATE_READING_KEY
(22:32:04) gg: ** gg_recv_packet(0x32d9a80);
(22:32:04) gg: // gg_recv_packet() header recv(24,0x7fffad825e70,8) = 8
(22:32:04) gg: // gg_recv_packet() body recv(24,0x24f9d88,4) = 4
(22:32:04) gg: // gg_watch_fd() challenge 69de5c3 --> SHA1 hash: eacb260f8c659fdf456c0da56c930c1d31810238
(22:32:04) gg: // gg_watch_fd() sending GG_LOGIN70 packet
(22:32:04) gg: ** gg_send_packet(0x32d9a80, 0x19, ...);
(22:32:04) gg: // gg_send_packet() partial write(), 116 sent, 0 left, 0 total left
(22:32:04) gg: login_handler: session->fd = 24
(22:32:04) gg: login_handler: session: check = 2; state = 8;
(22:32:04) gg: GG_EVENT_NONE
(22:32:04) gg: ** gg_event_free(0x3303c20);
(22:32:04) jabber: Recv (ssl)(138): <stream:stream from="gmail.com" id="66B2A1814864ECCC" version="1.0" xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client">
(22:32:04) jabber: Recv (ssl)(166): <stream:features><mechanisms xmlns="urn:ietf:params:xml:ns:xmpp-sasl"><mechanism>PLAIN</mechanism><mechanism>X-GOOGLE-TOKEN</mechanism></mechanisms></stream:features>
(22:32:04) sasl: Mechs found: PLAIN 
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/Home): <auth xmlns='urn:ietf:params:xml:ns:xmpp-sasl' mechanism='PLAIN' xmlns:ga='http://www.google.com/talk/protocol/auth' ga:client-uses-full-bind-result='true'>password removed</auth>
(22:32:04) gg: login_handler: session: check = 2; state = 8;
(22:32:04) gg: GG_STATE_READING_REPLY
(22:32:04) gg: ** gg_watch_fd(0x32d9a80);
(22:32:04) gg: // gg_watch_fd() GG_STATE_READING_REPLY
(22:32:04) gg: ** gg_recv_packet(0x32d9a80);
(22:32:04) gg: // gg_recv_packet() header recv(24,0x7fffad825e70,8) = 8
(22:32:04) gg: // gg_recv_packet() body recv(24,0x32fd808,1) = 1
(22:32:04) gg: // gg_watch_fd() login succeded
(22:32:04) gg: login_handler: session->fd = 24
(22:32:04) gg: login_handler: session: check = 2; state = 9;
(22:32:04) gg: GG_EVENT_CONN_SUCCESS
(22:32:04) gg: ggp_buddylist_send: adding 1126157
(22:32:04) gg: ggp_buddylist_send: adding 1204217
(22:32:04) gg: ggp_buddylist_send: adding 2052388
(22:32:04) gg: ggp_buddylist_send: adding 9900966
(22:32:04) gg: ggp_buddylist_send: adding 1211706
(22:32:04) gg: ggp_buddylist_send: adding 3746528
(22:32:04) gg: ggp_buddylist_send: adding 7791804
(22:32:04) gg: ggp_buddylist_send: adding 8082413
(22:32:04) gg: ggp_buddylist_send: adding 7625752
(22:32:04) gg: ggp_buddylist_send: adding 9343502
(22:32:04) gg: ggp_buddylist_send: adding 7479672
(22:32:04) gg: ggp_buddylist_send: adding 3981344
(22:32:04) gg: ggp_buddylist_send: adding 2294383
(22:32:04) gg: ggp_buddylist_send: adding 1384068
(22:32:04) gg: ** gg_notify_ex(0x32d9a80, 0x22273c0, 0x32c8ca0, 14);
(22:32:04) gg: ** gg_send_packet(0x32d9a80, 0x10, ...);
(22:32:04) gg: // gg_send_packet() partial write(), 78 sent, 0 left, 0 total left
(22:32:04) gg: send: ret=0; size=14
(22:32:04) g_log: purple_connection_update_progress: assertion `step < count' failed
(22:32:04) pidgin-libnotify: event_connection_throttle() called
(22:32:04) connection: Activating keepalive.
(22:32:04) gg: ** gg_event_free(0x21d1460);
(22:32:04) jabber: Recv (ssl)(51): <success xmlns="urn:ietf:params:xml:ns:xmpp-sasl"/>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/Home): <stream:stream to='gmail.com' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: VER 1 MSNP12
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: CVR 2 0x0409 winnt 5.1 i386 MSNMSGR 6.0.0602 MSMSGS vinislentoje@gmail.com
(22:32:04) jabber: Recv (ssl)(138): <stream:stream from="gmail.com" id="697E48040620BB4A" version="1.0" xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client">
(22:32:04) jabber: Recv (ssl)(137): <stream:features><bind xmlns="urn:ietf:params:xml:ns:xmpp-bind"/><session xmlns="urn:ietf:params:xml:ns:xmpp-session"/></stream:features>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/Home): <iq type='set' id='purpled8dca592'><bind xmlns='urn:ietf:params:xml:ns:xmpp-bind'><resource>Home</resource></bind></iq>
(22:32:04) jabber: Recv (ssl)(143): <iq id="purpled8dca592" type="result"><bind xmlns="urn:ietf:params:xml:ns:xmpp-bind"><jid>vinislentoje@gmail.com/HomeEC59471A</jid></bind></iq>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='set' id='purpled8dca593'><session xmlns='urn:ietf:params:xml:ns:xmpp-session'/></iq>
(22:32:04) jabber: Recv (ssl)(1):  
(22:32:04) jabber: Recv (ssl)(39): <iq type="result" id="purpled8dca593"/>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='get' id='purpled8dca594' to='gmail.com'><query xmlns='http://jabber.org/protocol/disco#items'/></iq>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='get' id='purpled8dca595' to='gmail.com'><query xmlns='http://jabber.org/protocol/disco#info'/></iq>
(22:32:04) oscar: inside auth_resp (Username: vinislentoje@gmail.com)
(22:32:04) oscar: Reg status: 3
Email: vinislentoje@gmail.com
BOSIP: 64.12.24.28:5190
(22:32:04) oscar: Closing auth connection...
(22:32:04) oscar: Scheduling destruction of FLAP connection of type 0x0017
(22:32:04) dns: DNS query for '64.12.24.28' queued
(22:32:04) oscar: Destroying oscar connection of type 0x0017.  Disconnect reason is 0
(22:32:04) oscar: Disconnected.  Code is 0x0000 and msg is 
(22:32:04) dnsquery: IP resolved for 64.12.24.28
(22:32:04) proxy: Attempting connection to 64.12.24.28
(22:32:04) proxy: Connecting to 64.12.24.28:5190 with no proxy
(22:32:04) proxy: Connection in progress
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: CVR 2 14.0.8089 14.0.8089 14.0.8089 http://msgruser.dlservice.microsoft.com/download/7/5/8/758BFCC9-1744-48F7-8162-E0AC1E7BF5C8/en/wlsetup-cvr.exe http://download.live.com/?sku=messenger
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: USR 3 TWN I vinislentoje@gmail.com
(22:32:04) jabber: Recv (ssl)(265): <iq type="error" id="purpled8dca594" to="vinislentoje@gmail.com/HomeEC59471A" from="gmail.com"><query xmlns="http://jabber.org/protocol/disco#items"/><error code="501" type="cancel"><feature-not-implemented xmlns="urn:ietf:params:xml:ns:xmpp-stanzas"/></error></iq>
(22:32:04) proxy: Connecting to 64.12.24.28:5190.
(22:32:04) proxy: Connected to 64.12.24.28:5190.
(22:32:04) oscar: connected to FLAP server of type 0x0002
(22:32:04) jabber: Recv (ssl)(582): <iq to="vinislentoje@gmail.com/HomeEC59471A" from="gmail.com" id="purpled8dca595" type="result"><query xmlns="http://jabber.org/protocol/disco#info"><identity category="server" type="im" name="Google Talk"/><feature var="http://jabber.org/protocol/disco#info"/><feature var="google:jingleinfo"/><feature var="google:roster"/><feature var="google:nosave"/><feature var="google:setting"/><feature var="google:shared-status"/><feature var="http://jabber.org/protocol/archive#otr"/><feature var="google:mail:notify"/><feature var="http://jabber.org/protocol/archive#save"/></query></iq>
(22:32:04) jabber: Google Talk!
(22:32:04) jabber: sending google:jingleinfo query
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='get' id='purpled8dca596'><query xmlns='google:jingleinfo'/></iq>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='get' id='purpled8dca597'><query xmlns='jabber:iq:roster' xmlns:gr='google:roster' gr:ext='2'/></iq>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='set' id='purpled8dca598'><usersetting xmlns='google:setting'><mailnotifications value='true'/></usersetting></iq>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='get' id='purpled8dca599'><query xmlns='google:mail:notify'/></iq>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='get' id='purpled8dca59a'><vCard xmlns='vcard-temp'/></iq>
(22:32:04) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='get' id='purpled8dca59b' to='proxy.jabber.org'><query xmlns='http://jabber.org/protocol/bytestreams'/></iq>
(22:32:04) jabber: Recv (ssl)(544): <iq to="vinislentoje@gmail.com/HomeEC59471A" id="purpled8dca596" type="result"><query xmlns="google:jingleinfo"><stun><server host="stun.l.google.com" udp="19302"/><server host="stun3.l.google.com" udp="19302"/><server host="stun2.l.google.com" udp="19302"/><server host="stun1.l.google.com" udp="19302"/><server host="stun4.l.google.com" udp="19302"/></stun><relay><token>CAESHwoWdmluaXNsZW50b2plQGdtYWlsLmNvbRDZisLN7iQaEH2jhX675lJ1LDifQKtGsvk=</token><server host="relay.google.com" udp="19295" tcp="19294" tcpssl="443"/></relay></query></iq>
(22:32:04) jabber: got google:jingleinfo
(22:32:04) dns: DNS query for 'stun.l.google.com' queued
(22:32:04) dns: Successfully sent DNS request to child 25013
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: XFR 3 NS 207.46.124.132:1863 0 64.4.50.62:1863
INFO io/pn_node.c:455:close_impl() closing 'ns'
INFO io/pn_node.c:491:close_impl() stream shutdown: 0x24e2ac0
(22:32:04) dns: DNS query for '207.46.124.132' queued
(22:32:04) dns: Got response for 'stun.l.google.com'
(22:32:04) dnsquery: IP resolved for stun.l.google.com
(22:32:04) jabber: set Google STUN IP/port address: 209.85.137.126:19302
(22:32:04) dnsquery: IP resolved for 207.46.124.132
(22:32:04) proxy: Attempting connection to 207.46.124.132
(22:32:04) proxy: Connecting to 207.46.124.132:1863 with no proxy
(22:32:04) proxy: Connection in progress
(22:32:05) oscar: MOTD: Unknown (5)
(22:32:05) proxy: Connecting to 207.46.124.132:1863.
(22:32:05) proxy: Connected to 207.46.124.132:1863.
INFO io/pn_node.c:380:connect_cb() connected: conn=0x21512c0,channel=0x2249d20
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: VER 4 MSNP12 CVR0
(22:32:05) oscar: FLAP connection of type 0x0002 is now fully connected
(22:32:05) oscar: ssi: requesting rights and list
(22:32:05) gg: ** gg_watch_fd(0x32d9a80);
(22:32:05) gg: // gg_watch_fd() GG_STATE_CONNECTED
(22:32:05) gg: ** gg_watch_fd_connected(0x32d9a80, 0x326dd80);
(22:32:05) gg: ** gg_recv_packet(0x32d9a80);
(22:32:05) gg: // gg_recv_packet() header recv(24,0x7fffad825df0,8) = 8
(22:32:05) gg: // gg_recv_packet() body recv(24,0x32f5198,249) = 249
(22:32:05) gg: // gg_watch_fd_connected() received a notify reply
(22:32:05) gg: notify60_pre: (1126157) status=21; version=0; descr=www.fotozoom.pl
(22:32:05) gg: notify60: (1126157) status=21; version=0; descr=www.fotozoom.pl
(22:32:05) util: requesting to fetch a URL
(22:32:05) dns: DNS query for 'api.gadu-gadu.pl' queued
(22:32:05) gg: st = offline
(22:32:05) blist: Updating buddy status for 1126157 (Gadu-Gadu)
(22:32:05) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(1126157, 8081413, prpl-gg, offline, now());
(22:32:05) gg: notify60: (1204217) status=21; version=0; descr=Jestem na WebGadu
(22:32:05) util: requesting to fetch a URL
(22:32:05) dns: DNS query for 'api.gadu-gadu.pl' queued
(22:32:05) gg: st = offline
(22:32:05) blist: Updating buddy status for 1204217 (Gadu-Gadu)
(22:32:05) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(1204217, 8081413, prpl-gg, offline, now());
(22:32:05) gg: notify60: (1211706) status=21; version=0; descr=www.nocturne.friendhood.net
(22:32:05) util: requesting to fetch a URL
(22:32:05) dns: DNS query for 'api.gadu-gadu.pl' queued
(22:32:05) gg: st = offline
(22:32:05) blist: Updating buddy status for 1211706 (Gadu-Gadu)
(22:32:05) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(1211706, 8081413, prpl-gg, offline, now());
(22:32:05) gg: notify60: (3981344) status=21; version=0; descr=KTC:*/ Brak listy gg :)Weso&#65533;ych
(22:32:05) util: requesting to fetch a URL
(22:32:05) dns: DNS query for 'api.gadu-gadu.pl' queued
(22:32:05) gg: st = offline
(22:32:05) blist: Updating buddy status for 3981344 (Gadu-Gadu)
(22:32:05) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(3981344, 8081413, prpl-gg, offline, now());
(22:32:05) gg: notify60: (7791804) status=21; version=0; descr=12 marca juz blisko...
(22:32:05) util: requesting to fetch a URL
(22:32:05) dns: DNS query for 'api.gadu-gadu.pl' queued
(22:32:05) gg: st = offline
(22:32:05) blist: Updating buddy status for 7791804 (Gadu-Gadu)
(22:32:05) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(7791804, 8081413, prpl-gg, offline, now());
(22:32:05) gg: notify60: (9343502) status=4; version=46; descr=justyna poka&#65533; im <GOLD>
(22:32:05) util: requesting to fetch a URL
(22:32:05) dns: DNS query for 'api.gadu-gadu.pl' queued
(22:32:05) gg: st = available
(22:32:05) blist: Updating buddy status for 9343502 (Gadu-Gadu)
(22:32:05) nautilus: saved blist online
(22:32:05) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(9343502, 8081413, prpl-gg, available, now());
(22:32:05) gg: ** gg_event_free(0x326dd80);
(22:32:05) dns: Successfully sent DNS request to child 25013
(22:32:05) dns: Successfully sent DNS request to child 25012
(22:32:05) dns: Successfully sent DNS request to child 25014
(22:32:05) dns: Created new DNS child 25017, there are now 4 children.
(22:32:05) dns: Successfully sent DNS request to child 25017
(22:32:05) dns: Got response for 'api.gadu-gadu.pl'
(22:32:05) dnsquery: IP resolved for api.gadu-gadu.pl
(22:32:05) proxy: Attempting connection to 91.197.13.248
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80 with no proxy
(22:32:05) proxy: Connection in progress
(22:32:05) dns: Successfully sent DNS request to child 25013
(22:32:05) dns: Got response for 'api.gadu-gadu.pl'
(22:32:05) dnsquery: IP resolved for api.gadu-gadu.pl
(22:32:05) proxy: Attempting connection to 91.197.13.247
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80 with no proxy
(22:32:05) proxy: Connection in progress
(22:32:05) dns: Successfully sent DNS request to child 25012
(22:32:05) dns: Got response for 'api.gadu-gadu.pl'
(22:32:05) dnsquery: IP resolved for api.gadu-gadu.pl
(22:32:05) proxy: Attempting connection to 91.197.13.248
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80 with no proxy
(22:32:05) proxy: Connection in progress
(22:32:05) dns: Got response for 'api.gadu-gadu.pl'
(22:32:05) dnsquery: IP resolved for api.gadu-gadu.pl
(22:32:05) proxy: Attempting connection to 91.197.13.248
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80 with no proxy
(22:32:05) proxy: Connection in progress
(22:32:05) dns: Got response for 'api.gadu-gadu.pl'
(22:32:05) dnsquery: IP resolved for api.gadu-gadu.pl
(22:32:05) proxy: Attempting connection to 91.197.13.247
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80 with no proxy
(22:32:05) proxy: Connection in progress
(22:32:05) dns: Got response for 'api.gadu-gadu.pl'
(22:32:05) dnsquery: IP resolved for api.gadu-gadu.pl
(22:32:05) proxy: Attempting connection to 91.197.13.247
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80 with no proxy
(22:32:05) proxy: Connection in progress
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: VER 4 MSNP12
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: CVR 5 0x0409 winnt 5.1 i386 MSNMSGR 6.0.0602 MSMSGS vinislentoje@gmail.com
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80.
(22:32:05) proxy: Connected to api.gadu-gadu.pl:80.
(22:32:05) util: request constructed
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80.
(22:32:05) proxy: Connected to api.gadu-gadu.pl:80.
(22:32:05) util: request constructed
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80.
(22:32:05) proxy: Connected to api.gadu-gadu.pl:80.
(22:32:05) util: request constructed
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80.
(22:32:05) proxy: Connected to api.gadu-gadu.pl:80.
(22:32:05) util: request constructed
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80.
(22:32:05) proxy: Connected to api.gadu-gadu.pl:80.
(22:32:05) util: request constructed
(22:32:05) proxy: Connecting to api.gadu-gadu.pl:80.
(22:32:05) proxy: Connected to api.gadu-gadu.pl:80.
(22:32:05) util: request constructed
(22:32:05) oscar: locate rights: max sig len = 4096
(22:32:05) oscar: buddy list rights: Max buddies = 1000 / Max watchers = 3000
(22:32:05) oscar: BOS rights: Max permit = 1000 / Max deny = 1000
(22:32:05) oscar: buddy list loaded
(22:32:05) oscar: ssi rights: max type 0x0000=3000, max type 0x0001=100, max type 0x0002=1000, max type 0x0003=1000, max type 0x0004=1, max type 0x0005=1, max type 0x0006=150, max type 0x0007=12, max type 0x0008=12, max type 0x0009=3, max type 0x000a=50, max type 0x000b=50, max type 0x000c=0, max type 0x000d=0, max type 0x000e=0, max type 0x000f=0, max type 0x0010=0, max type 0x0011=1, max type 0x0012=0, max type 0x0013=0, max type 0x0014=15, max type 0x0015=1, max type 0x0016=40, max type 0x0017=1, max type 0x0018=10, max type 0x0019=200, max type 0x001a=1, max type 0x001b=0, max type 0x001c=200, max type 0x001d=1, max type 0x001e=8, max type 0x001f=20, max type 0x0020=0, max type 0x0021=0, max type 0x0022=0, max type 0x0023=0, max type 0x0024=50, max type 0x0025=1, max type 0x0026=5, max type 0x0027=500, max type 0x0028=1, max type 0x0029=8,
(22:32:05) oscar: ssi: syncing local list and server list
(22:32:05) oscar: ssi: activating server-stored buddy list
(22:32:05) util: Writing file /home/vinis/.purple/icons/3d45ac275dff7aa015aea596ee075cb51d989978.jpg
(22:32:05) pidgin-libnotify: event_connection_throttle() called
(22:32:05) connection: Activating keepalive.
(22:32:05) util: Response headers: 'HTTP/1.0 200 OK
Connection: close
Content-Type: text/xml
Date: Fri, 19 Feb 2010 20:32:05 GMT
Server:  lighttpd

'
(22:32:05) util: Response headers: 'HTTP/1.0 200 OK
Connection: close
Content-Type: text/xml
Date: Fri, 19 Feb 2010 20:32:05 GMT
Server:  lighttpd

'
(22:32:05) util: Response headers: 'HTTP/1.0 200 OK
Connection: close
Content-Type: text/xml
Date: Fri, 19 Feb 2010 20:32:05 GMT
Server:  lighttpd

'
(22:32:05) util: Response headers: 'HTTP/1.0 200 OK
Connection: close
Content-Type: text/xml
Date: Fri, 19 Feb 2010 20:32:05 GMT
Server:  lighttpd

'
(22:32:05) util: Response headers: 'HTTP/1.0 200 OK
Connection: close
Content-Type: text/xml
Date: Fri, 19 Feb 2010 20:32:05 GMT
Server:  lighttpd

'
(22:32:05) util: Response headers: 'HTTP/1.0 200 OK
Connection: close
Content-Type: text/xml
Date: Fri, 19 Feb 2010 20:32:05 GMT
Server:  lighttpd

'
(22:32:05) jabber: Recv (ssl)(803): <iq to="vinislentoje@gmail.com/HomeEC59471A" id="purpled8dca597" type="result"><query gr:ext="2" xmlns="jabber:iq:roster" xmlns:gr="google:roster"><item jid="oreige@gmail.com" subscription="both" name="Oreige" gr:w="4" gr:mc="5" gr:emc="5"><group>google</group></item><item jid="andrius.dre@gmail.com" subscription="both" name="DRE" gr:w="1" gr:mc="5" gr:emc="2"><group>google</group></item><item jid="ausragj@gmail.com" subscription="both" name="Mama" gr:w="1" gr:mc="5"><group>google</group></item><item jid="gopatashah@gmail.com" subscription="both" name="Edhead" gr:w="1" gr:mc="5" gr:emc="2" gr:profileurl="http://www.google.com/profiles/103257849890219645608"><group>google</group></item><item jid="koxanie@gmail.com" subscription="both" name="Tomash" gr:w="1" gr:mc="5" gr:emc="5" gr:profileurl="
(22:32:05) jabber: Recv (ssl)(629): http://www.google.com/profiles/101565482109379639803"><group>google</group></item><item jid="liuriss@gmail.com" subscription="both" name="Laurynas" gr:w="1" gr:mc="5" gr:emc="3"><group>google</group></item><item jid="mmikolajunas@gmail.com" subscription="both" name="Medardas" gr:w="1" gr:mc="5" gr:emc="2"><group>google</group></item><item jid="marijus99@gmail.com" subscription="none" name="Marijus" gr:w="0" gr:emc="1" gr:profileurl="http://www.google.com/profiles/104243505098108305467"/><item jid="oseechrist@gmail.com" subscription="both" name="Alain" gr:w="0" gr:mc="3" gr:emc="3"><group>google</group></item></query></iq>
(22:32:05) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <presence><status>http://satva.lt/</status><priority>1</priority><c xmlns='http://jabber.org/protocol/caps' node='http://pidgin.im/' hash='sha-1' ver='lV6i//bt2U8Rm0REcX8h4F3Nk3M=' ext='voice-v1 camera-v1 video-v1'/><x xmlns='vcard-temp:x:update'/></presence>
(22:32:05) jabber: jabber_actions: have pep: NO
(22:32:05) pidgin-libnotify: event_connection_throttle() called
(22:32:05) connection: Activating keepalive.
(22:32:05) jabber: Recv (ssl)(1):  
(22:32:05) jabber: Recv (ssl)(80): <iq to="vinislentoje@gmail.com/HomeEC59471A" id="purpled8dca598" type="result"/>
(22:32:05) jabber: jabber_iq_parse
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: CVR 5 14.0.8089 14.0.8089 14.0.8089 http://msgruser.dlservice.microsoft.com/download/7/5/8/758BFCC9-1744-48F7-8162-E0AC1E7BF5C8/en/wlsetup-cvr.exe http://download.live.com/?sku=messenger
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: USR 6 TWN I vinislentoje@gmail.com
(22:32:05) oscar: Connecting to FLAP server 205.188.248.150:5190 of type 0x0018
(22:32:05) dns: DNS query for '205.188.248.150' queued
(22:32:05) oscar: ssi: status is 0x0003 for a 0x0008 action with name no item
(22:32:05) oscar: ssi: Action 0x0008 was unsuccessful with error 0x0003
(22:32:05) oscar: Connecting to FLAP server 205.188.254.87:5190 of type 0x000d
(22:32:05) dns: DNS query for '205.188.254.87' queued
(22:32:05) dnsquery: IP resolved for 205.188.248.150
(22:32:05) proxy: Attempting connection to 205.188.248.150
(22:32:05) proxy: Connecting to 205.188.248.150:5190 with no proxy
(22:32:05) proxy: Connection in progress
(22:32:05) dnsquery: IP resolved for 205.188.254.87
(22:32:05) proxy: Attempting connection to 205.188.254.87
(22:32:05) proxy: Connecting to 205.188.254.87:5190 with no proxy
(22:32:05) proxy: Connection in progress
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: USR 6 TWN S ct=1266611525,rver=5.5.4182.0,wp=FS_40SEC_0_COMPACT,lc=1033,id=507,ru=http:%2F%2Fmessenger.msn.com,tw=0,kpp=1,kv=4,ver=2.1.6000.1,rn=1lgjBfIL,tpf=b0735e3a873dfb5e75054465196398e0
(22:32:05) dns: DNS query for 'nexus.passport.com' queued
(22:32:05) dns: Successfully sent DNS request to child 25013
(22:32:05) oscar: Connecting to FLAP server 205.188.13.12:5190 of type 0x0010
(22:32:05) dns: DNS query for '205.188.13.12' queued
(22:32:05) blist: Updating buddy status for SillyXSuccubus (AIM)
(22:32:05) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(SillyXSuccubus, vinislentoje@gmail.com, prpl-aim, offline, now());
(22:32:05) dns: Got response for 'nexus.passport.com'
(22:32:05) dnsquery: IP resolved for nexus.passport.com
(22:32:05) proxy: Attempting connection to 65.54.254.139
(22:32:05) proxy: Connecting to nexus.passport.com:443 with no proxy
(22:32:05) proxy: Connection in progress
(22:32:05) proxy: Connecting to 205.188.248.150:5190.
(22:32:05) proxy: Connected to 205.188.248.150:5190.
(22:32:05) oscar: connected to FLAP server of type 0x0018
(22:32:05) proxy: Connecting to 205.188.254.87:5190.
(22:32:05) proxy: Connected to 205.188.254.87:5190.
(22:32:05) oscar: connected to FLAP server of type 0x000d
(22:32:05) dnsquery: IP resolved for 205.188.13.12
(22:32:05) proxy: Attempting connection to 205.188.13.12
(22:32:05) proxy: Connecting to 205.188.13.12:5190 with no proxy
(22:32:05) proxy: Connection in progress
(22:32:05) gg: gg_get_avatar_url_cb: UIN 1126157, IS_BLANK , URL http://avatars.gadu-gadu.pl/big/1126157?ts=1265895265
(22:32:05) gg: gg_get_avatar_url_cb: UIN 9343502, IS_BLANK 1, URL http://3.static.mojageneracja.pl/img/a1.gif
(22:32:05) gg: gg_get_avatar_url_cb: UIN 7791804, IS_BLANK 1, URL http://3.static.mojageneracja.pl/img/a1.gif
(22:32:05) gg: gg_get_avatar_url_cb: UIN 1204217, IS_BLANK 1, URL http://3.static.mojageneracja.pl/img/a1.gif
(22:32:05) gg: gg_get_avatar_url_cb: UIN 1211706, IS_BLANK , URL http://avatars.gadu-gadu.pl/big/1211706?ts=1237463550
(22:32:05) gg: gg_get_avatar_url_cb: UIN 3981344, IS_BLANK 1, URL http://3.static.mojageneracja.pl/img/a1.gif

[COLOR="Blue"]*this part was removed due to privacy reasons*[/COLOR]

(22:32:06) proxy: Connecting to 205.188.13.12:5190.
(22:32:06) proxy: Connected to 205.188.13.12:5190.
(22:32:06) oscar: connected to FLAP server of type 0x0010
(22:32:06) jabber: Recv (ssl)(1):  
(22:32:06) jabber: Recv (ssl)(743): <iq to="vinislentoje@gmail.com/HomeEC59471A" id="purpled8dca59a" type="result"><vCard xmlns="vcard-temp"><FN>Metal Maverick</FN><PHOTO><TYPE>image/jpeg</TYPE><BINVAL>/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAUDBAQODREQEBANERAOExIRDxIQEBEXEA0VEBITEBEQDxUQEhAREhIRFhAQEBYRDxERExUVDhEWGBcSGRESExIBBQUFBwYHDggIDh4UEhQfHxwfHBwdHh4eHx8fHh4fHR4eGxsfGR4eHB4fHRofHhseHhkdHxwWHBkfFx0eFh0cHf/AABEIAFkAYAMBIgACEQEDEQH/xAAdAAACAwADAQEAAAAAAAAAAAAABwUGCAIDBAEJ/8QAPhAAAgIBAgUBBQUDCgcAAAAAAQIDBBEAEgUGBxMhMRQiQVFhCCMyQnEzcpEVJDQ1UlNic7TBJUN0gqGisv/EABoBAAEFAQAAAAAAAAAAAAAAAAYCAwQFBwH/xAAzEQABAwIEBAQFAgcAAAAAAAABAgMRAAQFEiExBkFRYRMUcZEiMoGhwRXwI2KSorHR4f/aAAwDAQACEQMRAD8A2Xo0u+onWHlXh1pK0yW2kkj7w7MDOoQErk7TuPlTkIrY8ZxkZsHInPXKfEELVZkk2eHXDLJEflJG4WRD+8oz8M6SFpKss
(22:32:06) jabber: Recv (ssl)(756): 60gOJKigHUcqsmjRo0ql0aNGqxz1z7yrQh7s8qgZ2oie9LK3wSNFyzMfkBgepIAJ1wkASa4SAJNWfRrP9vrhzxIcwUIIk87TbsHuN8iyQRuE+ZUyE+ceMa5Q9cOek/acOryAHz2LhDYx+VZoEBI+si51VfruHZ8njJn1/O1Uh4lwkL8PzCZ9dPfanHzrzby7RhM1mVIkHgbj7zn4LGoyzsfgqAk/LSt5T66cRucShqQ0JhFJuaSSWQCWKNVOJXiVX7aswVV7sisxbAXPokq/HuJ8Sllnnc+3qH7UMysE4erE9sRIQAw8LumUEuR5Pw16un13qZXkWnRkp+1TEPOywbnkGRusXppWbZGuSEjjRfUKgPnUVnHW3702ydI7ElXcRoE/wAx3+9QrfiVm5xA2iNANNiSruI0CeeY7joNa2ho0DRogoppL/ae4pyGYkrzd57nmSotUKbUDAECXLFVSI/hbusEcZGGx4SvAqPMLLHYOKt+LOyWMjyAfAlVSVeN/wA0TM6+TgjwQx+sXT7mevZt8RjmpPDKFklFp3ieERRhBHG6pKrqduVUqh3OR7xOTVeA3nlhjkKMhkUMUb8SZGcH09P0Gs84tu7y3fQ4lASAfhWD8R6jfbsQfvWVcc39/a3LbqGwgJPwrB+I9Rv8vYgjvrTw6U9UeH3K8rT7K89MfzxGYbIxjInRj6wOAWVm9MMp8rkrHmPq5znfY+xOKlTJEcxjD2LQzjuRrINkMbDypdXcghsLk
(22:32:06) jabber: Recv (ssl)(756): DSg49WocRv9lSe1BHi26MR3w7BkqsUI3KColIOcFfGDnTGjSFFAGFVQAB6BQPAH0A0jE+LLhNs222MrhEq7dI9d+wNN4xxzdIs2m2RkeUJVpt0ieat9dgRUXxDgUk5Js2Ltkn++sSbPqBHGY4gD8gmuXCOWeXYTuighRvTcsahv44z/AOfOvvM/MHDKsYklJVSypkAnBb4nHwABJPwAOufMPGasEDztlkjXeduCSPp5AP8AHQi7dX91HiLUoKMCSYJ6Dl0oEfvMUvQkuuLUFmBJME6aDlzHvUizqPXHnwPr9NVLqlxTjteFZYWRVRx390ZfCHxuABBwpIJwQcZPwwerqGtGzSSRWO0yV5EZGKtgyIMqfVSVYgHGQT9MasHN3AeYOHA+0N7VSYbWn2Ylrg5H85Vcq8ZHgzIFwfxKM51Lw/DHFNi5SM2UkFBGukTE7nX1nkat8G4cu7i2OIMo8QNqIWgjXYbAzOh9QRsapHHouaZVSQwo7qN0NmnKNwDYIzHNsDxt43J3WBH8dcBwnhrQdyeggu2GKJCvvPZlP4doRicMfeOT7gyScDJ6Ol1Pm6UrFUe1PVWWeMGCmJOwqN9z99NJBXdHB/vgyY9CMYf32bk6amzLtsST8Tj3xzLaCLLAFOHSvHGWhCZA3NA8ufi5GBovsuH7pSk5iEoBmUlQUR0iYAPMbDkNaNLDhW9UtIWpKGwZlBUFkb5YmBPMbA7CZptdLeAXKfD61eRzJJBEiO5JOWA8g
(22:32:06) jabber: Recv (ssl)(756): E+dqn3Vz+UDVk0aNHVaTWcev9Pn23xAJ7DampVAjwCLtGOxMy5Msu+VP2We2ilSAd7fEYi7nSvnKatLNfaOpWhRpnrwybrEyxAyFJZhiOJW2+92t5wSNw1qLS3+03anTglzacGRUhJ+SzypA/8A6yNqsfwu1cuPNPDMobTsI6Daqe4wayduvOvpzKTtJkCOg2789azXyNw2Kpw0MiqHMTTtgeC7KZMfouQoHyUaiuFX+J8TpV6zYWe9KYJCoH3axsWmlAzjxGhOM43MBqyc/ShaEojIGU7aEecb8RDGPU+94+uurk3kznmDi9iGnDB3I0dqrTN9zVimZFaxLsyTJL2u3HEMMdsrMAo94DwOy/UlquViVZ83fQEx6SU+1Z/wjhCcZcXiFwPldCieegJj3KfaurptBJcsUK8oD+z9+S0DnBFYPUG8H13yPnB+R14OaqMleG5QJP3EsccO7yexZkTsfvbAzR+vrFjSY59471C4dxS6nelhnMziRox2+6N7OrKBnakm/uhVO07wfPg6efKHIfNv/Cb96WwwuSxpYjn8yo8LTzUiPAxFJhSQ+XBYecNhSd3AQhkJTslWf+6T9pHtRyrhu1No3atjVLviA+q5I/p0+lfeqXBWo2DTQN2bskL0QPRXawnerA+gCkiVQfAVyPy6dfVSrBM1GvIT2bV2OKdc4EyCGaXtNjGVdokDL+YePjq4z1qzEFlVih3LkA7T6ZXPofJGR586hOfeX7FmFRHJ2poZE
(22:32:06) jabber: Recv (ssl)(756): nryYyEkiO5d6+NyHyrL8mPxxpNsGmnc0bmT6wB+J9aLbbCWrPx1MCPFOYjvAB94n1NX6zy7RWpJWrqldXjkROyiosRdSN6Km0Agnd4x51+dPAemXVDhHF6kk1eZBHagAnQFoW3yqn7RcriQNt2uVY7sEA+NbYqdTedhGFfhNlpwMOY7FUV2YerIzzCUI3qN8W4ZwR8dRfTWfi3GrDWbZiSLhtp44acTb1E0apiexLkCVoizKirGiqwJ94gHROh1C/lM1EU2pPzCKdmjRo0ukUaUXXxRbnp8NPmGx3LFxR/zIa2zZGfiFkmeMkgg4jIz667/ALRfOnE60UVas2yzeZlWQeteKMAzTDwRuAKxpn88in4aSHK1ujwu+tiVpWrzRGCaWWSSRoHZ1cSuXZiElICuygAFVJ8elPf4sxbvJtJ+NQ0/fU8qrV43ZW+ItWLyoUvXt2k99hVl5z6PcM9qqipG0ELyBrqxFRAUgxKnuH8MjuEQNGB7u/PoNXWLjEXDuLmab3avEYoYDKfwwTwPJ2hIfyJMszKGPgOmCRka8D9W+U3uV60E1ebvs4kkWVe3EFTcoDDKvI7FVWNTnG8+NoBvfEKVOVCkiI6OMMrqCrD5MDkEfqNRG3VsLCiP+/uPtRV5VlQX4YAKjJjrH+qs/G25ZRe/N7MqqAe7LsAUDyDvb0+Y86THP3PPD70kM6dwcN4c5sSWNjD2yZVMUMdVcb5EVpGJcLtdgiqW8nUtU6W9OUYMtKrke
(22:32:06) jabber: Recv (ssl)(756): RmNSB+inKj6YHj4an+ZuB8PtQPBKCY5V2nBwR8QVI9GUgMpHoQNSncRCxlA33ppuxKTmJqlcT5752VZSvC5VEMSzubFiJCsUhcK5WMTv4Ebs6AFkCHIyQDDcR4h1Civ14rFmMTSzRFK1VEMD1njkaaVpJQZmMZiZMjYMlCAd4Cz8vAeqeXAvVJFeE1xJPUYz9sknLGKaJHkG7G7YAdoO0EsTHxycCo2e7YnlvcTlQQosUYaYRqdyxQQRZEMWTuLyNgk5Z/OunyoSQ0JUfWujzBVLhgCrX1N5sr0ajzEbn/BBH8ZpW8RxqBkncfXHoAT8NZ3XhPBqEEcsk09ebwstmvJKju8mWYyNH+JS2fMoK+g+mpixzFcucQLXVNeeuXSvTkyDEM7WmBbCzPJjAkiygUYGck659Rxc9lcqiyqvmaIjzNHg9xEI9Hx7ykZ8rj46CMVv3W7xFqglEHUg5SfQnl32JPTWsh414mduMWasmCpCUHUg5SSdNCeXIE6GemtMPov1h4oJYa9qaO1DZbt1bibQ4kIykNkLhCXwVWRACWAVly27WiNZj+yryvypdj781LL1JInq23hkia0pHcjaT8KTSwFdplw4YBGySSTpzWiWSXUsgOKzHqRBjuOvXb0o9w5LybdIeXmPUjKY5SOvXb0rNH2v+n3EpDJxD2lkRYYKsUUYYOXkshc7wThT3dzKoBYxICcA5g6t+g7PGrqzRYEigglNwyAw+GR89Ov7RnK/Mt2gsVRU
(22:32:06) jabber: Recv (ssl)(756): aVZ4JdrvtRhE+/3j8lIVsep2+MnA0qLnQLnGo6tSeGV7MKrcknkK7bAZibKqEO5MSMBENuBGo+uhziTAncRhbO6Rp3JI3PYChLi7ht/FocYAlI02EkkAyegSP8AFcemTcjJT4taviI1mmWELJtAl9kgDbIQSMy9yWUKUO4sBjBXwiumPE+pT3nTh8tpZZRJOtew5ZWWNj90DPlJG2MuJCyEmIjcpYYsPWiHhlW2KRJaHhMcUUYIy009lVsTWCPOZJWcAfLafQedSXTupz9Tv8PuLDVkSwZ4o41sectAzbJZFSRFY7SwCB8GIqSM6KGLVi0s0NOEaAAfTn9q1fDcBtsMwJCnHf4hSAhIBmAYKjG0wYnv9Jq71z6lVMJdoRxP8GlFiFX/AEzHMhP7sh8+NR9r7SvMbYEcXDsnwB3ppGJPphURGz/hxk/TTter1EuySSWLM9FPCwQU5Ym2gKN0k0j18uzNuwuAqqAME5J7OUb3HqXEoIJpvaYbyyrFJJFAk0E0Sd3aWgjiV0lQSeqZDIPPk5iI8iteQJ1+tLTeeG1LjIP1UPtP5pdcicudZOMSb78k1Ph4950jj7EljGCEQEtZVT6mR2XIGFU7shr/AGWOXeEw8IrypGiyWlaeR9v3kgmdpE3ucuwVWVRvYnCjTTnTII+YI/jrM/TheotnhlSuZoa9SvmGR6ryrcmSrvgCBiu2Pe0aszRsGwMDGSNSlqat0zECqhRXcuSB9OQ95p/858o8s3ou1
(22:32:06) jabber: Recv (ssl)(813): ahjmT1G8e8h/tRsMMjf4kIP10oONdCeOwtmjczGfWG9ukC/5cqYlAH9mQSfqNUW1Bwad+HSVb/E+3ddkeL+UrJkUNBJIJD985R4WjAZSSnkhh8dPHolx/jUi2atl+7NQmEXdIAaeKSNZYZHAAXftfY20AFoy35tRXW7W/HhvIn1FQMQwhi6by3KAtPf8dKl+j3KU/D+Hw1WdXaIOWZFITMkjylUBJO1S+0Z8kKDgZwLbo0asAABAp0AJECjULz3zHTpVJrMmSteNnIHq5A91F+rnCj6sNTWlT9qz+qT/wBRT/1MWu12k/zL9nvmpyl1w1me1DL/AChAJVWRJbCuvcqtKGiPYSTsrG7IuIlIOSceDlzlznGpLC54fxN44ppbcwStVjzJ7P7NFHFHDOUxtZ3kdTl3wQvveNi6NNOMpc+ankvrTHakrwvql0/kXJt14mHho7EixTRsPVZI5SjqR6HIx8idRzcy8DvcT4fFUljsGvYexO0LB44I1rTxZkdcqCzzIqjOSc/LUt1b/pZ/dX/fV56Vf0Rf+7/7bURrD0NrCwdqecvVLRlIq2azlyhxXmqu9+tDw+zZNa5ZKsktVVxYb2uMP3JkcZE494Iwx9QyjRul907/AK04v/nVf9FDqW6yl1OVVR23VNmU0t+G8zclwSNJJw+etd8iVF4fI0zMcZCTQRMkqufwuJMN4JxpgdFeCcbD2rliMwveePtwtt3wwwIUi7u3IEr7ndlDNtBVfUEaZOjTbNqhpRUKW7cLcTlNGjRo1Jpiv//Z</BINVAL></PHOTO></vCard></iq>
(22:32:06) jabber: Recv (ssl)(382): <presence from="koxanie@gmail.com/fring105B1469" to="vinislentoje@gmail.com/HomeEC59471A"><status>On mobile by www.fring.com</status><priority>0</priority><c node="http://www.google.com/xmpp/client/caps" ver="1.0.0.66" ext="voice-v1" xmlns="http://jabber.org/protocol/caps"/><x stamp="20100220T06:10:55" xmlns="jabber:x:delay"/><x xmlns="vcard-temp:x:update"><photo/></x></presence>
(22:32:06) blist: Updating buddy status for koxanie@gmail.com (XMPP)
(22:32:06) nautilus: saved blist online
(22:32:06) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(koxanie@gmail.com, vinislentoje@gmail.com/Home, prpl-jabber, available, now());
(22:32:06) jabber: Sending (ssl) (vinislentoje@gmail.com/HomeEC59471A): <iq type='get' id='purpled8dca59c' to='koxanie@gmail.com/fring105B1469'><query xmlns='http://jabber.org/protocol/disco#info' node='http://www.google.com/xmpp/client/caps#1.0.0.66'/></iq>
(22:32:06) jabber: Recv (ssl)(272): <iq type="error" id="purpled8dca59b" to="vinislentoje@gmail.com/HomeEC59471A" from="proxy.jabber.org"><query xmlns="http://jabber.org/protocol/bytestreams"/><error code="404" type="cancel"><remote-server-not-found xmlns="urn:ietf:params:xml:ns:xmpp-stanzas"/></error></iq>
(22:32:06) jabber: Discovered bytestream proxy server: jid='proxy.jabber.org' host='' port='0' zeroconf=''
(22:32:06) proxy: Connecting to nexus.passport.com:443.
(22:32:06) proxy: Connected to nexus.passport.com:443.
(22:32:06) oscar: FLAP connection of type 0x0018 is now fully connected
(22:32:06) oscar: FLAP connection of type 0x000d is now fully connected
(22:32:06) oscar: FLAP connection of type 0x0010 is now fully connected
(22:32:06) util: Writing file /home/vinis/.purple/icons/3d45ac275dff7aa015aea596ee075cb51d989978.jpg
(22:32:06) oscar: Uploading icon to icon server
(22:32:06) oscar: no more icons to request
(22:32:06) nss: subject=CN=nexus.passport.com,OU=MSN Passport,O=Microsoft,L=Redmond,ST=Washington,C=US issuer=CN=VeriSign Class 3 Secure Server CA,OU=Terms of use at https://www.verisign.com/rpa (c)05,OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US
(22:32:06) nss: subject=CN=VeriSign Class 3 Secure Server CA,OU=Terms of use at https://www.verisign.com/rpa (c)05,OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US issuer=OU=Class 3 Public Primary Certification Authority,O="VeriSign, Inc.",C=US
(22:32:06) nss: subject=OU=Class 3 Public Primary Certification Authority,O="VeriSign, Inc.",C=US issuer=OU=Class 3 Public Primary Certification Authority,O="VeriSign, Inc.",C=US
(22:32:06) certificate/x509/tls_cached: Starting verify for nexus.passport.com
(22:32:06) certificate/x509/tls_cached: Checking for cached cert...
(22:32:06) certificate/x509/tls_cached: ...Found cached cert
(22:32:06) nss/x509: Loading certificate from /home/vinis/.purple/certificates/x509/tls_peers/nexus.passport.com
(22:32:06) certificate/x509/tls_cached: Peer cert matched cached
(22:32:06) nss/x509: Exporting certificate to /home/vinis/.purple/certificates/x509/tls_peers/nexus.passport.com
(22:32:06) util: Writing file /home/vinis/.purple/certificates/x509/tls_peers/nexus.passport.com
(22:32:06) certificate: Successfully verified certificate for nexus.passport.com
(22:32:06) jabber: Recv (ssl)(341): <iq type="error" id="purpled8dca59c" to="vinislentoje@gmail.com/HomeEC59471A" from="koxanie@gmail.com/fring105B1469"><query node="http://www.google.com/xmpp/client/caps#1.0.0.66" xmlns="http://jabber.org/protocol/disco#info"/><error code="501" type="cancel"><feature-not-implemented xmlns="urn:ietf:params:xml:ns:xmpp-stanzas"/></error></iq>
(22:32:06) oscar: chat info: Chat Rights:
(22:32:06) oscar: chat info: 	Max Concurrent Rooms: 17
(22:32:06) oscar: chat info: 	Exchange List: (15 total)
(22:32:06) oscar: chat info: 		2    
(22:32:06) oscar: chat info: 		4    
(22:32:06) oscar: chat info: 		5    
(22:32:06) oscar: chat info: 		6    
(22:32:06) oscar: chat info: 		7    
(22:32:06) oscar: chat info: 		8    
(22:32:06) oscar: chat info: 		9    
(22:32:06) oscar: chat info: 		10    
(22:32:06) oscar: chat info: 		11    
(22:32:06) oscar: chat info: 		12    
(22:32:06) oscar: chat info: 		13    
(22:32:06) oscar: chat info: 		14    
(22:32:06) oscar: chat info: 		15    
(22:32:06) oscar: chat info: 		16    
(22:32:06) oscar: chat info: 		20    
(22:32:06) dns: DNS query for 'login.live.com' queued
(22:32:06) dns: Successfully sent DNS request to child 25013
(22:32:06) dns: Got response for 'login.live.com'
(22:32:06) dnsquery: IP resolved for login.live.com
(22:32:06) proxy: Attempting connection to 65.54.165.179
(22:32:06) proxy: Connecting to login.live.com:443 with no proxy
(22:32:06) proxy: Connection in progress
(22:32:07) util: Writing file prefs.xml to directory /home/vinis/.purple
(22:32:07) util: Writing file /home/vinis/.purple/prefs.xml
(22:32:07) util: Writing file accounts.xml to directory /home/vinis/.purple
(22:32:07) util: Writing file /home/vinis/.purple/accounts.xml
(22:32:08) util: Writing file blist.xml to directory /home/vinis/.purple
(22:32:08) util: Writing file /home/vinis/.purple/blist.xml
(22:32:09) proxy: Connecting to login.live.com:443.
(22:32:09) proxy: Connected to login.live.com:443.
(22:32:10) nss: subject=CN=login.live.com,OU=Passport,O=Microsoft Corporation,OID.2.5.4.9=One Microsoft Way,L=Redmond,ST=Washington,postalCode=98052,C=US,serialNumber=600413485,OID.2.5.4.15="V1.0, Clause 5.(b)",OID.1.3.6.1.4.1.311.60.2.1.2=Washington,OID.1.3.6.1.4.1.311.60.2.1.3=US issuer=CN=VeriSign Class 3 Extended Validation SSL CA,OU=Terms of use at https://www.verisign.com/rpa (c)06,OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US
(22:32:10) nss: subject=CN=VeriSign Class 3 Extended Validation SSL CA,OU=Terms of use at https://www.verisign.com/rpa (c)06,OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US issuer=CN=VeriSign Class 3 Public Primary Certification Authority - G5,OU="(c) 2006 VeriSign, Inc. - For authorized use only",OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US
(22:32:10) nss: subject=CN=VeriSign Class 3 Public Primary Certification Authority - G5,OU="(c) 2006 VeriSign, Inc. - For authorized use only",OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US issuer=CN=VeriSign Class 3 Public Primary Certification Authority - G5,OU="(c) 2006 VeriSign, Inc. - For authorized use only",OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US
(22:32:10) certificate/x509/tls_cached: Starting verify for login.live.com
(22:32:10) certificate/x509/tls_cached: Checking for cached cert...
(22:32:10) certificate/x509/tls_cached: ...Found cached cert
(22:32:10) nss/x509: Loading certificate from /home/vinis/.purple/certificates/x509/tls_peers/login.live.com
(22:32:10) certificate/x509/tls_cached: Peer cert matched cached
(22:32:10) nss/x509: Exporting certificate to /home/vinis/.purple/certificates/x509/tls_peers/login.live.com
(22:32:10) util: Writing file /home/vinis/.purple/certificates/x509/tls_peers/login.live.com
(22:32:10) certificate: Successfully verified certificate for login.live.com
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: USR 7 TWN S t=9DoK1qeYdGJCsWiNg69YtTKwVY0BukUeQAU81rxHXkVjtKeeYuuW59oMhQIm1T0X3bX*!YabRsofxaqxxsxkV3bTFSAOhNOrs8FGrGSSGkOecr96Q8vktSIVr!!4fZe3MUsgFj4wUOXYqTjrGbc3PNyg$$&p=9sMK*M74pAMRlq!FnuRU6!oUxvWuehZz*UcOZjAWh4PSTgVwIxXQBpRwccDT6EsZzQa7b0zTXtGHtlGJ7f004Xn7G0Up1t83VvcgJOg8qBecxNzQZ3zuCjCkm*viUSJiORTTyaTNWjdOpsCL2Tg3ciXmiztyLhWKyi1Sdeb17CcGDl82Q4ghBgorDhaozOBKok5FoMYIUjLoz!6GDoBZPZ4g$$
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: USR 7 OK vinislentoje@gmail.com 1 0
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: SYN 8 0 0
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: MSG Hotmail Hotmail 555
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: SYN 8 2010-02-11T09:25:15.117-08:00 2009-06-21T11:55:14.32-07:00 7 2
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: GTC A
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: BLP BL
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: PRP MFN Vinis
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: PRP MBE N
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: PRP WWE 0
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LSG Draugai 5144b357-ad9b-4236-ae11-02fa6688e00f
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LSG MSN 083e9866-080c-49a0-bcc6-d654143acc46
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LST N=manon120184@hotmail.com F=#(*)Manon26(*)#%20%20-->%20Homer%20Simpson:%20(_8^(|)%20<--%20Had%20an%20good%20birthday%20:)%20and%20now%20has%20windows%207!%20--> C=8cb466c9-034c-47a7-9a99-0e6ae40a69f4 11 1 083e9866-080c-49a0-bcc6-d654143acc46
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LST N=nenukuh@gmail.com F=Gaoooow%20KiD%20*scared* C=44fe90d5-4856-4850-b112-2195e78bdabe 11 1 083e9866-080c-49a0-bcc6-d654143acc46
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LST N=saskia-laeesna@hotmail.com F=[c=6]Saskia[/c=38] C=346834c2-3a8b-47a1-b3c4-4033299056eb 11 1 083e9866-080c-49a0-bcc6-d654143acc46
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LST N=sir.leks@hotmail.com F=--Nj@mB-- C=39656b24-f101-4c59-a135-8ca395061862 11 1 083e9866-080c-49a0-bcc6-d654143acc46
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LST N=dennisreymen@gmail.com F=Dennis C=86a103f9-8ca5-45fb-8524-d78039a893ee 11 1 083e9866-080c-49a0-bcc6-d654143acc46
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LST N=distroyer_1980@hotmail.com F=Dan~eel%20-%20An%20eye%20for%20an%20eye%20will%20make%20the%20whole%20world%20blind. C=b67779ae-d539-4a98-aea2-e130d1d35c34 11 1 083e9866-080c-49a0-bcc6-d654143acc46
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: LST N=capitanmugroso@hotmail.es 2 1
(22:32:11) util: Writing file /home/vinis/.purple/icons/552480e2b06514bd36b9de655a9a50654a5f6f31.png
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: CHG 9 NLN 1342472228 %3Cmsnobj%20Creator%3D%22vinislentoje%40gmail.com%22%20Size%3D%228410%22%20Type%3D%223%22%20Location%3D%22TFR2C2.tmp%22%20Friendly%3D%22AAA%3D%22%20SHA1D%3D%22VSSA4rBlFL02ud5lWppQZUpfbzE%3D%22%20SHA1C%3D%221MpSdZ7pD%2FM8YKogdTkESqswjD8%3D%22%2F%3E
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: UUX 10 69
(22:32:11) jabber: jabber_actions: have pep: NO
(22:32:11) pidgin-libnotify: event_connection_throttle() called
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: BLP 11 BL
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: CHG 9 NLN 1342472228 %3Cmsnobj%20Creator%3D%22vinislentoje%40gmail.com%22%20Size%3D%228410%22%20Type%3D%223%22%20Location%3D%22TFR2C2.tmp%22%20Friendly%3D%22AAA%3D%22%20SHA1D%3D%22VSSA4rBlFL02ud5lWppQZUpfbzE%3D%22%20SHA1C%3D%221MpSdZ7pD%2FM8YKogdTkESqswjD8%3D%22%2F%3E
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: MSG Hotmail Hotmail 512
WARNING io/pn_ssl_conn.c:246:close_impl() not connected: conn=0x2560f00
(22:32:11) dns: DNS query for 'rsi.hotmail.com' queued
(22:32:11) dns: Successfully sent DNS request to child 25013
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: ILN 0 AWY nenukuh@gmail.com Gaoooow%20KiD%20*untamed* 2789003300 %3cmsnobj%20Creator%3d%22nenukuh%40gmail.com%22%20Type%3d%223%22%20SHA1D%3d%22g495cdXvikx0Lu5G81KRWzLko2Y%3d%22%20Size%3d%223817%22%20Location%3d%220%22%20Friendly%3d%22MQAxAAAA%22%2f%3e
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 000: ns: XFR 12 SB
INFO cvr/pn_peer_msg.c:201:sip_new() send sip: INVITE MSNMSGR:nenukuh@gmail.com MSNSLP/1.0
(22:32:11) blist: Updating buddy status for nenukuh@gmail.com (WLM)
(22:32:11) nautilus: saved blist online
(22:32:11) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(nenukuh@gmail.com, vinislentoje@gmail.com, prpl-msn-pecan, away, now());
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: UBX nenukuh@gmail.com 1089
(22:32:11) blist: Updating buddy status for nenukuh@gmail.com (WLM)
(22:32:11) dns: Got response for 'rsi.hotmail.com'
(22:32:11) dnsquery: IP resolved for rsi.hotmail.com
(22:32:11) proxy: Attempting connection to 65.54.238.254
(22:32:11) proxy: Connecting to rsi.hotmail.com:443 with no proxy
(22:32:11) proxy: Connection in progress
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: BLP 11 BL
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: ILN 0 BSY dennisreymen@gmail.com Dennis 2789003324 %3cmsnobj%20Creator%3d%22dennisreymen%40gmail.com%22%20Type%3d%223%22%20SHA1D%3d%22u5b1hAYLCjpjkvM1eTpGjaZY4gg%3d%22%20Size%3d%222315%22%20Location%3d%220%22%20Friendly%3d%22bQBlADIAAAA%3d%22%2f%3e
(22:32:11) blist: Updating buddy status for dennisreymen@gmail.com (WLM)
(22:32:11) nautilus: saved blist online
(22:32:11) cap: Executing: insert into cap_status (buddy, account, protocol, status, event_time) values(dennisreymen@gmail.com, vinislentoje@gmail.com, prpl-msn-pecan, busy, now());
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: UBX dennisreymen@gmail.com 583
(22:32:11) blist: Updating buddy status for dennisreymen@gmail.com (WLM)
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: UUX 10 0
(22:32:11) proxy: Connecting to rsi.hotmail.com:443.
(22:32:11) proxy: Connected to rsi.hotmail.com:443.
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 000: ns: XFR 12 SB 64.4.35.58:1863 CKI 1431938981.6767133.15412933
(22:32:11) dns: DNS query for '64.4.35.58' queued
(22:32:11) dnsquery: IP resolved for 64.4.35.58
(22:32:11) proxy: Attempting connection to 64.4.35.58
(22:32:11) proxy: Connecting to 64.4.35.58:1863 with no proxy
(22:32:11) proxy: Connection in progress
(22:32:11) proxy: Connecting to 64.4.35.58:1863.
(22:32:11) proxy: Connected to 64.4.35.58:1863.
INFO io/pn_node.c:380:connect_cb() connected: conn=0x256e500,channel=0x32fc710
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 001: nenukuh@gmail.com: USR 1 vinislentoje@gmail.com 1431938981.6767133.15412933
(22:32:12) nss: subject=CN=rsi.hotmail.com,OU=MSN Hotmail,O=Microsoft,L=Mountain View,ST=California,C=US issuer=CN=Microsoft Secure Server Authority,DC=redmond,DC=corp,DC=microsoft,DC=com
(22:32:12) nss: partial certificate chain
(22:32:12) certificate/x509/tls_cached: Starting verify for rsi.hotmail.com
(22:32:12) certificate/x509/tls_cached: Checking for cached cert...
(22:32:12) certificate/x509/tls_cached: ...Found cached cert
(22:32:12) nss/x509: Loading certificate from /home/vinis/.purple/certificates/x509/tls_peers/rsi.hotmail.com
(22:32:12) certificate/x509/tls_cached: Peer cert matched cached
(22:32:12) nss/x509: Exporting certificate to /home/vinis/.purple/certificates/x509/tls_peers/rsi.hotmail.com
(22:32:12) util: Writing file /home/vinis/.purple/certificates/x509/tls_peers/rsi.hotmail.com
(22:32:12) certificate: Successfully verified certificate for rsi.hotmail.com
INFO io/pn_ssl_conn.c:177:connect_cb() connected: conn=0x2560f00,ssl_conn=0x2560f00
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 001: nenukuh@gmail.com: USR 1 OK vinislentoje@gmail.com Vinis
INFO cmd/cmdproc.c:110:show_debug_cmd() C: 001: nenukuh@gmail.com: CAL 2 nenukuh@gmail.com
INFO cmd/cmdproc.c:110:show_debug_cmd() S: 001: nenukuh@gmail.com: CAL 2 RINGING 1431938981
[COLOR="Red"]Segmentation fault[/COLOR]
vinis@g44:~$ dns[25017]: Oops, father has gone, wait for me, wait...!
dns[25014]: Oops, father has gone, wait for me, wait...!
dns[25013]: Oops, father has gone, wait for me, wait...!
dns[25012]: Oops, father has gone, wait for me, wait...!
```

---

### Post by skarychinezeguie on 2010-02-19
looks like you have a couple problems. try disabling all the plugins. also try removing your hotmail account and the certificates. restart. re-add account and see if you get another error. if you still get an error, try making a new email with hotmail or live and try with that one. If that doesn't work, open the synaptic package manager and uninstall, restart, re-install, add accounts and try again. if that doesn't work the problem is probably not with pidgin and you will need to look elsewhere.

---

### Post by VinisLentoje on 2010-02-19
Thank You for the reply.
Deleting the certificates, adding another account, disabling plugins, and so on, did not help.
But finally, I have found a solution - reverted from the "msn-pecan" MSN/WLM implementation (which I had used for a long time) to the original one. And now it works again.
Well, I guess I can mark this one as "solved".
P.S. How can I mark my thread as "solved"? Or is it done by the moderators? Never had to do it before, so I really have no idea...

---

### Post by bushtangu on 2010-02-19
i'm having a problem with pidgin too. i'm trying to log with a gmail account in msn but i'm not able. any help please?

---

### Post by n0dix on 2010-02-19
> **VinisLentoje said:**
> 
P.S. How can I mark my thread as "solved"? Or is it done by the moderators? Never had to do it before, so I really have no idea...

Easy, edit your first post, in the title add the SOLVED tag.

---

