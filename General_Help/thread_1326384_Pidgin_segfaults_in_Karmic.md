---
title: "Pidgin segfaults in Karmic"
date: 2009-11-14
forum: General Help
---

### Post by eleifsp on 2009-11-14
Hi all.  Upgraded recently to Ubuntu Karmic.  Been having a few problems. 

The recent update (which included Kernel 2.6.31-15) seems to have messed with Pidgin.  Or at least, maybe the kernel did.  

When I run Pidgin (through the terminal), it outputs the words "Segmentation Fault".  Running pidgin -d (debug option) turns out: 

> (11:55:43) prefs: Reading /home/daniel/.purple/prefs.xml
(11:55:43) prefs: Finished reading /home/daniel/.purple/prefs.xml
(11:55:43) dbus: okkk
(11:55:43) plugins: probing /usr/lib/pidgin/plonkers.so
(11:55:43) plugins: probing /usr/lib/pidgin/convbadger.so
(11:55:43) plugins: probing /usr/lib/pidgin/gestures.so
(11:55:43) plugins: probing /usr/lib/pidgin/gRIM.so
(11:55:43) plugins: probing /usr/lib/pidgin/irssi.so
(11:55:43) plugins: probing /usr/lib/pidgin/xmppdisco.so
(11:55:43) plugins: probing /usr/lib/pidgin/nicksaid.so
(11:55:43) plugins: probing /usr/lib/pidgin/album.so
(11:55:43) plugins: probing /usr/lib/pidgin/switchspell.so
(11:55:43) plugins: probing /usr/lib/pidgin/gevolution.so
(11:55:43) plugins: probing /usr/lib/pidgin/timestamp_format.so
(11:55:43) plugins: probing /usr/lib/pidgin/libfacebookarm.so
(11:55:43) plugins: /usr/lib/pidgin/libfacebookarm.so is not loadable: cannot open shared object file: No such file or directory
(11:55:43) plugins: probing /usr/lib/pidgin/libextprefs.so
(11:55:43) plugins: probing /usr/lib/pidgin/infopane.so
(11:55:43) plugins: probing /usr/lib/pidgin/musicmessaging.so
(11:55:43) plugins: probing /usr/lib/pidgin/libawayonlock.so
(11:55:43) plugins: probing /usr/lib/pidgin/history.so
(11:55:43) plugins: probing /usr/lib/pidgin/difftopic.so
(11:55:43) plugins: probing /usr/lib/pidgin/timestamp.so
(11:55:43) plugins: probing /usr/lib/pidgin/xmppconsole.so
(11:55:43) plugins: probing /usr/lib/pidgin/vvconfig.so
(11:55:43) plugins: probing /usr/lib/pidgin/nautilus.so
(11:55:43) plugins: probing /usr/lib/pidgin/pidgin-schedule.so
(11:55:43) plugins: probing /usr/lib/pidgin/convcolors.so
(11:55:43) plugins: probing /usr/lib/pidgin/iconaway.so
(11:55:43) plugins: probing /usr/lib/pidgin/enhancedhist.so
(11:55:43) plugins: probing /usr/lib/pidgin/themeedit.so
(11:55:43) plugins: probing /usr/lib/pidgin/sendbutton.so
(11:55:43) plugins: probing /usr/lib/pidgin/sepandtab.so
(11:55:43) plugins: probing /usr/lib/pidgin/extplacement.so
(11:55:43) plugins: probing /usr/lib/pidgin/mystatusbox.so
(11:55:43) plugins: probing /usr/lib/pidgin/cap.so
(11:55:43) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(11:55:43) plugins: probing /usr/lib/pidgin/blistops.so
(11:55:43) plugins: probing /usr/lib/pidgin/markerline.so
(11:55:43) plugins: probing /usr/lib/pidgin/pidginrc.so
(11:55:43) plugins: probing /usr/lib/pidgin/timelog.so
(11:55:43) plugins: probing /usr/lib/pidgin/xchat-chats.so
(11:55:43) plugins: probing /usr/lib/pidgin/notify.so
(11:55:43) plugins: probing /usr/lib/pidgin/listlog.so
(11:55:43) plugins: probing /usr/lib/pidgin/spellchk.so
(11:55:43) plugins: probing /usr/lib/pidgin/ticker.so
(11:55:43) plugins: probing /usr/lib/pidgin/guifications.so
(11:55:43) plugins: probing /usr/lib/pidgin/lastseen.so
(11:55:43) plugins: probing /usr/lib/purple-2/slashexec.so
(11:55:43) plugins: probing /usr/lib/purple-2/libqq.so
(11:55:43) plugins: probing /usr/lib/purple-2/bash.so
(11:55:43) plugins: probing /usr/lib/purple-2/libskype_dbus.so
(11:55:43) plugins: probing /usr/lib/purple-2/bot-sentry.so
(11:55:43) bot-sentry: bindtextdomain = /usr/share/locale(11:55:43) bot-sentry: bind_textdomain_codeset = UTF-8(11:55:43) plugins: probing /usr/lib/purple-2/joinpart.so
(11:55:43) plugins: probing /usr/lib/purple-2/libxmpp.so
(11:55:43) util: Reading file xmpp-caps.xml from directory /home/daniel/.purple
(11:55:43) jabber: creating hash tables for data objects
(11:55:43) plugins: probing /usr/lib/purple-2/libskype_dbus64.so
(11:55:43) plugins: /usr/lib/purple-2/libskype_dbus64.so is not loadable: wrong ELF class: ELFCLASS64
(11:55:43) plugins: probing /usr/lib/purple-2/psychic.so
(11:55:43) plugins: probing /usr/lib/purple-2/google.so
(11:55:43) plugins: probing /usr/lib/purple-2/ssl-nss.so
(11:55:43) plugins: probing /usr/lib/purple-2/libgg.so
(11:55:43) plugins: probing /usr/lib/purple-2/libfacebook.so
(11:55:43) plugins: probing /usr/lib/purple-2/libyahoojp.so
(11:55:43) plugins: probing /usr/lib/purple-2/splitter.so
(11:55:43) plugins: probing /usr/lib/purple-2/irc-more.so
(11:55:43) plugins: probing /usr/lib/purple-2/autoaccept.so
(11:55:43) plugins: probing /usr/lib/purple-2/libymsg.so
(11:55:43) plugins: /usr/lib/purple-2/libymsg.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(11:55:43) plugins: probing /usr/lib/purple-2/pidgin-libnotify.so
(11:55:43) plugins: probing /usr/lib/purple-2/newline.so
(11:55:43) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(11:55:43) plugins: probing /usr/lib/purple-2/offlinemsg.so
(11:55:43) plugins: probing /usr/lib/purple-2/libicq.so
(11:55:43) plugins: probing /usr/lib/purple-2/napster.so
(11:55:43) plugins: probing /usr/lib/purple-2/libsimple.so
(11:55:43) plugins: probing /usr/lib/purple-2/libskypearm.so
(11:55:43) plugins: /usr/lib/purple-2/libskypearm.so is not loadable: cannot open shared object file: No such file or directory
(11:55:43) plugins: probing /usr/lib/purple-2/showoffline.so
(11:55:43) plugins: probing /usr/lib/purple-2/autoprofile.so
(11:55:43) autoprofile: general: Initializing AutoProfile
(11:55:43) autoprofile: general: Initializing preference defaults if necessary
(11:55:43) plugins: probing /usr/lib/purple-2/idle.so
(11:55:43) plugins: probing /usr/lib/purple-2/dice.so
(11:55:43) plugins: probing /usr/lib/purple-2/libskype64.so
(11:55:43) plugins: /usr/lib/purple-2/libskype64.so is not loadable: wrong ELF class: ELFCLASS64
(11:55:43) plugins: probing /usr/lib/purple-2/highlight.so
(11:55:43) plugins: probing /usr/lib/purple-2/libyahoo.so
(11:55:43) plugins: probing /usr/lib/purple-2/oldlogger.so
(11:55:43) plugins: probing /usr/lib/purple-2/libaim.so
(11:55:43) plugins: probing /usr/lib/purple-2/libirc.so
(11:55:43) plugins: probing /usr/lib/purple-2/irchelper.so
(11:55:43) plugins: probing /usr/lib/purple-2/log_reader.so
(11:55:43) plugins: probing /usr/lib/purple-2/statenotify.so
(11:55:43) plugins: probing /usr/lib/purple-2/libmyspace.so
(11:55:43) plugins: probing /usr/lib/purple-2/ignore.so
(11:55:43) plugins: probing /usr/lib/purple-2/libnovell.so
(11:55:43) plugins: probing /usr/lib/purple-2/simfix.so
(11:55:43) plugins: probing /usr/lib/purple-2/libfacebookppc.so
(11:55:43) plugins: /usr/lib/purple-2/libfacebookppc.so is not loadable: ELF file data encoding not little-endian
(11:55:43) plugins: probing /usr/lib/purple-2/autoreply.so
(11:55:43) plugins: probing /usr/lib/purple-2/liboscar.so
(11:55:43) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(11:55:43) plugins: probing /usr/lib/purple-2/libsnpp.so
(11:55:43) plugins: probing /usr/lib/purple-2/libzephyr.so
(11:55:43) plugins: probing /usr/lib/purple-2/sslinfo.so
(11:55:43) plugins: probing /usr/lib/purple-2/tcl.so
(11:55:43) plugins: probing /usr/lib/purple-2/dewysiwygification.so
(11:55:43) plugins: probing /usr/lib/purple-2/colorize.so
(11:55:43) plugins: probing /usr/lib/purple-2/libskype.so
(11:55:43) plugins: probing /usr/lib/purple-2/ssl.so
(11:55:43) plugins: probing /usr/lib/purple-2/eight_ball.so
(11:55:43) plugins: probing /usr/lib/purple-2/buddynote.so
(11:55:43) plugins: probing /usr/lib/purple-2/libbonjour.so
(11:55:43) plugins: probing /usr/lib/purple-2/libsametime.so
(11:55:43) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(11:55:43) plugins: probing /usr/lib/purple-2/xmppprio.so
(11:55:43) plugins: probing /usr/lib/purple-2/groupmsg.so
(11:55:43) plugins: probing /usr/lib/purple-2/libjabber.so
(11:55:43) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(11:55:43) plugins: probing /usr/lib/purple-2/flip.so
(11:55:43) plugins: probing /usr/lib/purple-2/dbus-example.so
(11:55:43) plugins: probing /usr/lib/purple-2/listhandler.so
(11:55:43) plugins: probing /usr/lib/purple-2/libmsn.so
(11:55:43) plugins: probing /usr/lib/purple-2/perl.so
(11:55:43) prefs: /purple/status/scores/offline changed, scheduling save.
(11:55:43) prefs: /purple/status/scores/available changed, scheduling save.
(11:55:43) prefs: /purple/status/scores/invisible changed, scheduling save.
(11:55:43) prefs: /purple/status/scores/away changed, scheduling save.
(11:55:43) prefs: /purple/status/scores/extended_away changed, scheduling save.
(11:55:43) prefs: /purple/status/scores/idle changed, scheduling save.
(11:55:43) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(11:55:43) util: Reading file accounts.xml from directory /home/daniel/.purple
(11:55:43) util: Reading file status.xml from directory /home/daniel/.purple
(11:55:43) certificate: CertificateVerifier x509, singleuse requested but not found.
(11:55:43) certificate: CertificateVerifier singleuse registered
(11:55:43) certificate: CertificatePool x509, ca requested but not found.
(11:55:43) certificate: CertificateScheme x509 requested but not found.
(11:55:43) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(11:55:43) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(11:55:43) certificate: CertificatePool ca registered
(11:55:43) certificate: CertificatePool x509, tls_peers requested but not found.
(11:55:43) certificate: CertificatePool tls_peers registered
(11:55:43) certificate: CertificateVerifier x509, tls_cached requested but not found.
(11:55:43) certificate: CertificateVerifier tls_cached registered
(11:55:43) prefs: /purple/logging/format changed, scheduling save.
(11:55:43) prefs: /purple/logging/format changed, scheduling save.
(11:55:43) prefs: /purple/proxy/type changed, scheduling save.
(11:55:43) prefs: /purple/proxy/host changed, scheduling save.
(11:55:43) prefs: /purple/proxy/port changed, scheduling save.
(11:55:43) prefs: /purple/proxy/username changed, scheduling save.
(11:55:43) prefs: /purple/proxy/password changed, scheduling save.
(11:55:43) certificate: CertificateScheme x509 requested but not found.
(11:55:43) certificate: CertificateScheme x509 registered
(11:55:43) util: Reading file smileys.xml from directory /home/daniel/.purple
(11:55:43) util: File /home/daniel/.purple/smileys.xml does not exist (this is not necessarily an error)
(11:55:43) stun: using server 
(11:55:43) GLib-GObject: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(11:55:43) sound: Initializing sound output drivers.
(11:55:44) prefs: /pidgin/conversations/placement changed, scheduling save.
(11:55:44) gtkmedia: Registering media element types
(11:55:44) util: Reading file blist.xml from directory /home/daniel/.purple
(11:55:44) g_log: purple_presence_set_status_active: assertion `status != NULL' failed
(11:55:44) g_log: purple_presence_set_status_active: assertion `status != NULL' failed
(11:55:44) g_log: purple_presence_set_status_active: assertion `status != NULL' failed
(11:55:44) g_log: purple_presence_set_status_active: assertion `status != NULL' failed
(11:55:44) g_log: purple_presence_set_status_active: assertion `status != NULL' failed
(11:55:44) g_log: purple_presence_set_status_active: assertion `status != NULL' failed
(11:55:44) g_log: purple_presence_set_status_active: assertion `status != NULL' failed
(11:55:44) plugins: Loading saved plugin /usr/lib/purple-2/bot-sentry.so
(11:55:44) plugins: Loading saved plugin /usr/lib/pidgin/libextprefs.so
(11:55:44) prefs: purple_prefs_get_int: Unknown pref /pidgin/blist/tooltip_delay
(11:55:44) plugins: Loading saved plugin /usr/lib/purple-2/pidgin-libnotify.so
(11:55:44) plugins: Loading saved plugin /usr/lib/purple-2/ssl-nss.so
(11:55:44) plugins: Loading saved plugin /usr/lib/pidgin/nautilus.so
(11:55:45) nautilus: saved blist online
(11:55:45) plugins: Loading saved plugin /usr/lib/purple-2/psychic.so
(11:55:45) plugins: Loading saved plugin /usr/lib/purple-2/ssl.so
(11:55:45) pounce: Error reading pounces: Failed to open file '/home/daniel/.purple/pounces.xml': No such file or directory
(11:55:45) Session Management: ICE initialized.
(11:55:45) Session Management: Connecting with no previous ID
(11:55:45) Session Management: Handling new ICE connection... 
(11:55:45) done.
(11:55:45) Session Management: Connected to manager (gnome-session) with client ID 1036226e67ea694dfb12582177455304100000019440041
(11:55:45) Session Management: Using pidgin as command
(11:55:45) account: Connecting to account --Edit--.
(11:55:45) connection: Connecting. gc = 0x914d700
(11:55:45) oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
(11:55:45) oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
(11:55:45) oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
(11:55:45) oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
(11:55:45) oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
(11:55:45) oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
(11:55:45) oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
(11:55:45) oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
(11:55:45) oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
(11:55:45) oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
(11:55:45) oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
(11:55:45) oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
(11:55:45) oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
(11:55:45) oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
(11:55:45) oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
(11:55:45) oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
(11:55:45) oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
(11:55:45) oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
(11:55:45) oscar: Adding handler for ffff/0003
(11:55:45) oscar: Adding handler for ffff/0006
(11:55:45) oscar: Adding handler for 0007/0003
(11:55:45) oscar: Adding handler for 0007/0005
(11:55:45) oscar: Adding handler for 0007/0007
(11:55:45) oscar: Adding handler for 0018/0001
(11:55:45) oscar: Adding handler for 0018/0007
(11:55:45) oscar: Adding handler for 0017/0003
(11:55:45) oscar: Adding handler for 0017/0007
(11:55:45) oscar: Adding handler for 0017/000a
(11:55:45) oscar: Adding handler for 0010/0005
(11:55:45) oscar: Adding handler for 0009/0001
(11:55:45) oscar: Adding handler for 0009/0003
(11:55:45) oscar: Adding handler for 0003/0001
(11:55:45) oscar: Adding handler for 0003/0003
(11:55:45) oscar: Adding handler for 0003/000b
(11:55:45) oscar: Adding handler for 0003/000c
(11:55:45) oscar: Adding handler for 000e/0001
(11:55:45) oscar: Adding handler for 000e/0003
(11:55:45) oscar: Adding handler for 000e/0004
(11:55:45) oscar: Adding handler for 000e/0002
(11:55:45) oscar: Adding handler for 000e/0006
(11:55:45) oscar: Adding handler for 000d/0001
(11:55:45) oscar: Adding handler for 000d/0009
(11:55:45) oscar: Adding handler for 0013/0001
(11:55:45) oscar: Adding handler for 0013/0003
(11:55:45) oscar: Adding handler for 0013/0006
(11:55:45) oscar: Adding handler for 0013/000e
(11:55:45) oscar: Adding handler for 0013/0008
(11:55:45) oscar: Adding handler for 0013/0009
(11:55:45) oscar: Adding handler for 0013/0015
(11:55:45) oscar: Adding handler for 0013/0019
(11:55:45) oscar: Adding handler for 0013/001b
(11:55:45) oscar: Adding handler for 0013/001c
(11:55:45) oscar: Adding handler for 0004/0007
(11:55:45) oscar: Adding handler for 0004/000a
(11:55:45) oscar: Adding handler for 0004/000b
(11:55:45) oscar: Adding handler for 0004/0001
(11:55:45) oscar: Adding handler for 0004/0014
(11:55:45) oscar: Adding handler for 0004/000c
(11:55:45) oscar: Adding handler for 0015/00f3
(11:55:45) oscar: Adding handler for 0015/00f2
(11:55:45) oscar: Adding handler for 0002/0003
(11:55:45) oscar: Adding handler for 0002/0006
(11:55:45) oscar: Adding handler for 0002/0001
(11:55:45) oscar: Adding handler for 0001/0001
(11:55:45) oscar: Adding handler for 0001/000f
(11:55:45) oscar: Adding handler for 0001/001f
(11:55:45) oscar: Adding handler for 0001/0021
(11:55:45) oscar: Adding handler for 0001/000a
(11:55:45) oscar: Adding handler for 0001/0005
(11:55:45) oscar: Adding handler for 0001/0013
(11:55:45) oscar: Adding handler for 0001/0010
(11:55:45) oscar: Adding handler for 0008/0002
(11:55:45) oscar: Adding handler for 000a/0001
(11:55:45) oscar: Adding handler for 000a/0003
(11:55:45) oscar: oscar_login: gc = 0x914d700
(11:55:45) dns: DNS query for 'login.messaging.aol.com' queued
(11:55:45) account: Connecting to account [email]--Edit--@gmail.com[/email]/.
(11:55:45) connection: Connecting. gc = 0x914e2d8
(11:55:45) dnssrv: querying SRV record for gmail.com: _xmpp-client._tcp.gmail.com
(11:55:45) account: Connecting to account [email]--Edit--@live.com[/email].
(11:55:45) connection: Connecting. gc = 0x914f1d0
(11:55:45) msn: new httpconn (0x914f678)
(11:55:45) dns: DNS query for 'messenger.hotmail.com' queued
(11:55:45) account: Connecting to account --Edit--.
(11:55:45) connection: Connecting. gc = 0x914fb48
(11:55:45) dns: DNS query for 'scsa.msg.yahoo.com' queued
(11:55:45) account: Connecting to account --Edit--.
(11:55:45) connection: Connecting. gc = 0x91501c0
Segmentation Fault

It seems to be right around the Yahoo login that things happen.  Anyone know what's up?   I know that kernel 14 didn't work at all for me, and 13 worked almost perfectly.  I was kinda hoping 15 would be much better, but... I'm not so sure.

EDIT:  Made the error easier to read.

---

### Post by kentpend on 2009-11-15
It looks like you have the facebook plugin- try disabling it.  I had the same problem in jaunty, and disabling facebook solved the problem.  No guarantees that's your problem though.

---

### Post by Simstud on 2009-11-30
This exact thing was happening to me too. I fixed it by downloading and installing the older version of the facebookchat plugin:

[http://pidgin-facebookchat.googlecode.com/files/pidgin-facebookchat-1.62.deb](http://pidgin-facebookchat.googlecode.com/files/pidgin-facebookchat-1.62.deb)

You'll have to remove the version you have beforehand by typing 'sudo apt-get remove pidgin-facebookchat'

EDIT: well, maybe not 'fixed'. facebookchat plugin still crashes pidgin once a day or so. Everyone donate $5 so they can fix it.

---

