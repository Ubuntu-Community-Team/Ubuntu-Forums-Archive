---
title: "Pidgin Problem"
date: 2010-02-19
forum: General Help
---

### Post by clicker4721 on 2010-02-19
Anytime I open Pidgin, I have to enter every account again.  It simply can't hold the settings.  Suggestions anyone?

---

### Post by claracc on 2010-02-20
Have you ticked the box in pidgin -->accounts--> name of the account (yahoo, gmail,...) -->edit account --> basic tab, remember password?.

Only with my hotmail account, when i try to open tray or messages from it with pidgin i have to introduce the password, [http://ubuntuforums.org/showthread.php?t=1407259&highlight=pidgin+hotmail](http://ubuntuforums.org/showthread.php?t=1407259&highlight=pidgin+hotmail), I have asked for help in this thread but I have not get any answer.

For my yahoo or gmail accounts in pidgin I have not any problem, browser (firefox 3.5.8) opens automatically (no need to enter manually passwords).

---

### Post by n0dix on 2010-02-20
> **clicker4721 said:**
> Anytime I open Pidgin, I have to enter every account again.  It simply can't hold the settings.  Suggestions anyone?

There is an error when run pidgin from console?

---

### Post by clicker4721 on 2010-02-20
Let's see:
@ claracc:  No, I've done that, the accounts literally disappear everytime I use the program, even if I never logged off.
@ n0dix:  It's not an error with Pidgin's protocols or anything, it just can't remember any of my accounts--not the passwords, the accounts disappear.  Strangely, plugins stay...I just don't know what it all means.

---

### Post by claracc on 2010-02-21
It is a very strange problem, i have three accounts (yahoo, gmail and hotmail) configured in pidgin 2.6.2 and they don't disappear.
I suggest to unsinstall completely (through synaptic) pidgin, reboot, install pidgin again, configure one of your accounts (remember to keep the settings)and see if the problem is solved.

I hope it can help

---

### Post by clicker4721 on 2010-02-21
> **claracc said:**
> It is a very strange problem, i have three accounts (yahoo, gmail and hotmail) configured in pidgin 2.6.2 and they don't disappear.
I suggest to unsinstall completely (through synaptic) pidgin, reboot, install pidgin again, configure one of your accounts (remember to keep the settings)and see if the problem is solved.

I hope it can help
I'll give it a shot, thanks.

---

### Post by clicker4721 on 2010-02-21
> **claracc said:**
> It is a very strange problem, i have three accounts (yahoo, gmail and hotmail) configured in pidgin 2.6.2 and they don't disappear.
I suggest to unsinstall completely (through synaptic) pidgin, reboot, install pidgin again, configure one of your accounts (remember to keep the settings)and see if the problem is solved.

I hope it can help
Gah! It didn't work! I don't understand, plugnis 'stick.' :(

---

### Post by chewearn on 2010-02-21
Run pidgin from a terminal.  There might be error messages send to stderr (which get lost if you run apps from GUI).

---

### Post by clicker4721 on 2010-02-22
> **chewearn said:**
> Run pidgin from a terminal.  There might be error messages send to stderr (which get lost if you run apps from GUI).
It does nothing.  I'm starting to think it's not saving the configurations...I mean, like, the files for it.  Can this be remedied?

---

### Post by chewearn on 2010-02-23
> **clicker4721 said:**
> It does nothing.  I'm starting to think it's not saving the configurations...I mean, like, the files for it.  Can this be remedied?

Unless we know the error, it's difficult to know the solution.

The configurations for pidgin are stored in "~/.purple", if you are wondering where it is and want to investigate.  Maybe un-install pidgin, delete this directory and reinstall.

I checked the command line interface for pidgin, apparently need a "-d" switch to print the debug info:
```
pidgin -d
```

---

### Post by clicker4721 on 2010-02-23
> **chewearn said:**
> Unless we know the error, it's difficult to know the solution.

The configurations for pidgin are stored in "~./purple", if you are wondering where it is and want to investigate.  Maybe un-install pidgin, delete this directory and reinstall.

I checked the command line interface for pidgin, apparently need a "-d" switch to print the debug info:
```
pidgin -d
```
Alrighty, I tried it out and here's my read:
```
clicker4721@clicker4721d:~$ pidgin -d
(18:01:32) prefs: Reading /home/clicker4721/.purple/prefs.xml
(18:01:32) prefs: Reading /etc/purple/prefs.xml
(18:01:32) dbus: okkk
(18:01:32) plugins: probing /home/clicker4721/.purple/plugins/pidgin_awn.so
(18:01:32) plugins: /home/clicker4721/.purple/plugins/pidgin_awn.so is not loadable: cannot open shared object file: Permission denied
(18:01:32) plugins: probing /usr/lib/pidgin/gevolution.so
(18:01:32) plugins: probing /usr/lib/pidgin/nautilus.so
(18:01:32) plugins: probing /usr/lib/pidgin/timestamp_format.so
(18:01:32) plugins: probing /usr/lib/pidgin/xmppconsole.so
(18:01:32) plugins: probing /usr/lib/pidgin/timestamp.so
(18:01:32) plugins: probing /usr/lib/pidgin/markerline.so
(18:01:32) plugins: probing /usr/lib/pidgin/extplacement.so
(18:01:32) plugins: probing /usr/lib/pidgin/cap.so
(18:01:32) plugins: probing /usr/lib/pidgin/ticker.so
(18:01:32) plugins: probing /usr/lib/pidgin/spellchk.so
(18:01:32) plugins: probing /usr/lib/pidgin/musicmessaging.so
(18:01:32) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(18:01:32) plugins: probing /usr/lib/pidgin/notify.so
(18:01:32) plugins: probing /usr/lib/pidgin/iconaway.so
(18:01:32) plugins: probing /usr/lib/pidgin/history.so
(18:01:32) plugins: probing /usr/lib/pidgin/gestures.so
(18:01:32) plugins: probing /usr/lib/pidgin/sendbutton.so
(18:01:32) plugins: probing /usr/lib/pidgin/convcolors.so
(18:01:32) plugins: probing /usr/lib/pidgin/pidginrc.so
(18:01:32) plugins: probing /usr/lib/purple-2/libsametime.so
(18:01:32) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(18:01:32) plugins: probing /usr/lib/purple-2/libgg.so
(18:01:33) plugins: probing /usr/lib/purple-2/autoaccept.so
(18:01:33) plugins: probing /usr/lib/purple-2/newline.so
(18:01:33) plugins: probing /usr/lib/purple-2/libyahoo.so
(18:01:33) plugins: probing /usr/lib/purple-2/perl.so
(18:01:33) plugins: probing /usr/lib/purple-2/libqq.so
(18:01:33) plugins: probing /usr/lib/purple-2/libjabber.so
(18:01:33) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(18:01:33) plugins: probing /usr/lib/purple-2/joinpart.so
(18:01:33) plugins: probing /usr/lib/purple-2/libzephyr.so
(18:01:33) plugins: probing /usr/lib/purple-2/libxmpp.so
(18:01:33) util: Reading file xmpp-caps.xml from directory /home/clicker4721/.purple
(18:01:33) util: File /home/clicker4721/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(18:01:33) jabber: creating hash tables for data objects
(18:01:33) plugins: probing /usr/lib/purple-2/tcl.so
(18:01:33) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtk8.4.so.0: cannot open shared object file: No such file or directory
(18:01:33) plugins: probing /usr/lib/purple-2/buddynote.so
(18:01:33) plugins: probing /usr/lib/purple-2/ssl-nss.so
(18:01:33) plugins: probing /usr/lib/purple-2/dbus-example.so
(18:01:33) plugins: probing /usr/lib/purple-2/statenotify.so
(18:01:33) plugins: probing /usr/lib/purple-2/ssl.so
(18:01:33) plugins: probing /usr/lib/purple-2/libicq.so
(18:01:33) plugins: probing /usr/lib/purple-2/libaim.so
(18:01:33) plugins: probing /usr/lib/purple-2/log_reader.so
(18:01:33) plugins: probing /usr/lib/purple-2/offlinemsg.so
(18:01:33) plugins: probing /usr/lib/purple-2/libmsn.so
(18:01:33) plugins: probing /usr/lib/purple-2/libirc.so
(18:01:33) plugins: probing /usr/lib/purple-2/psychic.so
(18:01:33) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(18:01:33) plugins: probing /usr/lib/purple-2/libnovell.so
(18:01:33) plugins: probing /usr/lib/purple-2/libsimple.so
(18:01:33) plugins: probing /usr/lib/purple-2/liboscar.so
(18:01:33) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(18:01:33) plugins: probing /usr/lib/purple-2/libbonjour.so
(18:01:33) plugins: probing /usr/lib/purple-2/libmyspace.so
(18:01:33) plugins: probing /usr/lib/purple-2/idle.so
(18:01:33) prefs: /purple/status/scores/offline changed, scheduling save.
(18:01:33) prefs: /purple/status/scores/available changed, scheduling save.
(18:01:33) prefs: /purple/status/scores/invisible changed, scheduling save.
(18:01:33) prefs: /purple/status/scores/away changed, scheduling save.
(18:01:33) prefs: /purple/status/scores/extended_away changed, scheduling save.
(18:01:33) prefs: /purple/status/scores/idle changed, scheduling save.
(18:01:33) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(18:01:33) util: Reading file accounts.xml from directory /home/clicker4721/.purple
(18:01:33) util: File /home/clicker4721/.purple/accounts.xml does not exist (this is not necessarily an error)
(18:01:33) util: Reading file status.xml from directory /home/clicker4721/.purple
(18:01:33) util: File /home/clicker4721/.purple/status.xml does not exist (this is not necessarily an error)
(18:01:33) certificate: CertificateVerifier x509, singleuse requested but not found.
(18:01:33) certificate: CertificateVerifier singleuse registered
(18:01:33) certificate: CertificatePool x509, ca requested but not found.
(18:01:33) certificate: CertificateScheme x509 requested but not found.
(18:01:33) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(18:01:33) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(18:01:33) certificate: CertificatePool ca registered
(18:01:33) certificate: CertificatePool x509, tls_peers requested but not found.
(18:01:33) g_log: x509_tls_peers_init: assertion `ret == 0' failed
(18:01:33) certificate: CertificateVerifier x509, tls_cached requested but not found.
(18:01:33) certificate: CertificateVerifier tls_cached registered
(18:01:33) prefs: /purple/logging/format changed, scheduling save.
(18:01:33) prefs: /purple/logging/format changed, scheduling save.
(18:01:33) prefs: /purple/proxy/type changed, scheduling save.
(18:01:33) prefs: /purple/proxy/host changed, scheduling save.
(18:01:33) prefs: /purple/proxy/port changed, scheduling save.
(18:01:33) prefs: /purple/proxy/username changed, scheduling save.
(18:01:33) prefs: /purple/proxy/password changed, scheduling save.
(18:01:33) certificate: CertificateScheme x509 requested but not found.
(18:01:33) certificate: CertificateScheme x509 registered
(18:01:33) util: Reading file smileys.xml from directory /home/clicker4721/.purple
(18:01:33) util: File /home/clicker4721/.purple/smileys.xml does not exist (this is not necessarily an error)
(18:01:33) stun: using server 
(18:01:33) sound: Initializing sound output drivers.
(18:01:33) prefs: /pidgin/conversations/placement changed, scheduling save.
(18:01:33) util: Reading file blist.xml from directory /home/clicker4721/.purple
(18:01:33) util: File /home/clicker4721/.purple/blist.xml does not exist (this is not necessarily an error)
(18:01:33) pounce: Error reading pounces: Failed to open file '/home/clicker4721/.purple/pounces.xml': No such file or directory
(18:01:33) ui_main: Failed to load the default window icon (scalablepx version)!
(18:01:33) Session Management: ICE initialized.
(18:01:33) Session Management: Connecting with no previous ID
(18:01:33) Session Management: Handling new ICE connection... 
(18:01:33) done.
(18:01:33) Session Management: Connected to manager (gnome-session) with client ID 109fecb1e5211f9f4d126696969320144400000032420039
(18:01:33) Session Management: Using pidgin as command
(18:01:33) prefs: /purple/savedstatus/default changed, scheduling save.
(18:01:33) prefs: /pidgin/blist/list_visible changed, scheduling save.
(18:01:33) Session Management: Received first save_yourself
(18:01:34) prefs: /pidgin/blist/y changed, scheduling save.
(18:01:34) Session Management: Received save_complete
(18:01:34) nautilus: Force loading nautilus plugin
(18:01:34) nautilus: saved blist online
(18:01:34) prefs: /pidgin/plugins/loaded changed, scheduling save.
(18:01:34) prefs: /plugins/gtk/nautilus/auto_loaded changed, scheduling save.
(18:01:38) util: Writing file prefs.xml to directory /home/clicker4721/.purple
(18:01:38) util: Writing file /home/clicker4721/.purple/prefs.xml
(18:01:38) util: Error opening file /home/clicker4721/.purple/prefs.xml.save for writing: Permission denied
(18:01:38) util: Writing file status.xml to directory /home/clicker4721/.purple
(18:01:38) util: Writing file /home/clicker4721/.purple/status.xml
(18:01:38) util: Error opening file /home/clicker4721/.purple/status.xml.save for writing: Permission denied
(18:03:01) certificate: CertificateVerifier tls_cached unregistered
(18:03:01) certificate: CertificateVerifier singleuse unregistered
(18:03:01) certificate: CertificatePool ca unregistered
(18:03:01) main: Unloading all plugins
(18:03:01) plugins: Unloading plugin Nautilus Integration
(18:03:01) nautilus: Stop nautilus plugin
(18:03:01) plugins: Unloading plugin Sametime
(18:03:01) plugins: Unloading plugin Gadu-Gadu
(18:03:01) plugins: Unloading plugin Yahoo
(18:03:01) plugins: Unloading plugin Perl Plugin Loader
(18:03:01) plugins: Unloading plugin QQ
(18:03:01) plugins: Unloading plugin Zephyr
(18:03:01) plugins: Unloading plugin XMPP
(18:03:01) jabber: destroying hash tables for data objects
(18:03:01) plugins: Unloading plugin NSS
(18:03:01) certificate: CertificateScheme x509 unregistered
(18:03:01) plugins: Unloading plugin SSL
(18:03:01) plugins: Unloading plugin ICQ
(18:03:01) plugins: Unloading plugin AIM
(18:03:01) plugins: Unloading plugin MSN
(18:03:01) plugins: Unloading plugin IRC
(18:03:01) plugins: Unloading plugin SILC
(18:03:01) plugins: Unloading plugin GroupWise
(18:03:01) plugins: Unloading plugin SIMPLE
(18:03:01) plugins: Unloading plugin Bonjour
(18:03:01) plugins: Unloading plugin MySpaceIM
(18:03:01) Session Management: Handling closed ICE connection... 
(18:03:01) done.
(18:03:01) Session Management: Connection closed.
clicker4721@clicker4721d:~$ 

```
That is me simply opening and closing Pidgin.  You clearly know a ton more about it than me, so I don't know what all of it means.  What's the diagnosis, Doc?

---

### Post by n0dix on 2010-02-23
Check the permissions of /home/clicker4721/.purple/status.xml.save

---

### Post by clicker4721 on 2010-02-23
> **n0dix said:**
> Check the permissions of /home/clicker4721/.purple/status.xml.save

Hahaha!!! We may have found the problem--it doesn't exist! :P ...So now what?

---

### Post by n0dix on 2010-02-23
> **clicker4721 said:**
>  ...So now what?

Reinstall? Maybe you get the file back. ;)

---

### Post by clicker4721 on 2010-02-23
> **n0dix said:**
> Reinstall? Maybe you get the file back. ;)

I've reinstalled Pidgin at least three times. :(

---

### Post by n0dix on 2010-02-23
Show the permissions of the .purple directory.
```
 ls -la .purple 
```

---

### Post by clicker4721 on 2010-02-23
> **n0dix said:**
> Show the permissions of the .purple directory.
```
 ls -la .purple 
```

```
clicker4721@clicker4721d:~$ ls -la .purple
total 12
drwxr-xr-x  3 root        root        4096 2010-02-17 22:13 .
drwxr-xr-x 58 clicker4721 clicker4721 4096 2010-02-23 19:58 ..
drwxr-xr-x  2 root        root        4096 2010-02-17 22:13 plugins
clicker4721@clicker4721d:~$ 

```
Meaning?

---

### Post by n0dix on 2010-02-23
you have bad permission on the .purple directory.
Try with:
```
 sudo chown -R clicker4721:clicker4721 .purple 
```

---

### Post by clicker4721 on 2010-02-23
> **n0dix said:**
> you have bad permission on the .purple directory.
Try with:
```
 sudo chown -R clicker4721:clicker4721 .purple 
```
```
clicker4721@clicker4721d:~$ sudo chown -R clicker4721:clicker4721 .purple
[sudo] password for clicker4721: 
clicker4721@clicker4721d:~$ ls -la .purple
total 12
drwxr-xr-x  3 clicker4721 clicker4721 4096 2010-02-17 22:13 .
drwxr-xr-x 58 clicker4721 clicker4721 4096 2010-02-23 19:58 ..
drwxr-xr-x  2 clicker4721 clicker4721 4096 2010-02-17 22:13 plugins
clicker4721@clicker4721d:~$ 

```
Is this what it is supposed to look like?

---

### Post by n0dix on 2010-02-23
Yes, try to run pidgin.

---

### Post by clicker4721 on 2010-02-24
**WOOOOOOOHOOOOOO!!!!!!!!!**
I honestly didn't think it would ever work again!
:D:D:D:D:D:D:D
Works like a charm! Thank you all so much, I obviously wouldn't have know what to do!
:guitar:
Thank you, thank you, thank you, all!!!

---

### Post by n0dix on 2010-02-24
> **clicker4721 said:**
> **WOOOOOOOHOOOOOO!!!!!!!!!**
I honestly didn't think it would ever work again!
:D:D:D:D:D:D:D
Works like a charm! Thank you all so much, I obviously wouldn't have know what to do!
Thank you, thank you, thank you, all!!!

No problem, 
Enjoy!!! ;)

---

