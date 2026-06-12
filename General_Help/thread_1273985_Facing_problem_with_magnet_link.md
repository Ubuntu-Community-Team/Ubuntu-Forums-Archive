---
title: "Facing problem with magnet link"
date: 2009-09-24
forum: General Help
---

### Post by Tapas Bose, India on 2009-09-24
Good morning everybody.
I am facing a problem associated magnet link. I am trying to download from seedpeer using magnet link. But firefox show me the following message 
> 
Firefox doesn't know how to open this address, because the protocol (magnet) isn't associated with any program.

Then I googled and find a solution of the error from the link
[http://ubuntuforums.org/showthread.php?t=308130](http://ubuntuforums.org/showthread.php?t=308130)
and the solution is
> 
Type about:config into the address bar and press Enter.
    * Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true 
    * Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /opt/azureus/azureus 
    * Ensure network.protocol-handler.expose-all is set to true. 

I have vuze 4.2.0.2.1~getdeb1 (according to synaptic; also in synaptic this is in the "Installed (local or obsolete)" section).
By using the command 
> 
which vuze

I found the path of vuze is /usr/bin/vuze.
But after doing everything firefox again show me the previous error.
Please help me.

---

### Post by erpel on 2009-11-17
This thread might be a bit old already but the problem is still there.

I found [this]("http://ubuntuforums.org/showthread.php?t=229924") older thread and after repeating these steps vuze at least tries to download a magnet link.


```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/vuze %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true
```It still fails, however, saying "no sources found for torrent". The reason seems to be that Vuze modifies the magnet link in an illegal way. If I try [this link]("magnet:?xt=urn:btih:98c5c361d0be5f2a07ea8fa5052e5aa48097e7f6&dn=ubuntu-9.10-desktop-i386.iso&tr=http%3A%2F%2Fdenis.stalker.h3q.com%3A6969%2Fannounce"), e.g. which should point to a karmic iso, vuze outputs

```
Downloading From :magnet:?xt=urn:btih:98c5c361d0be5f2a07ea8fa5052e5aa48097e7f6&&&&
```The same problem seems to be described [here]("http://forum.vuze.com/thread.jspa;forum01?messageID=182203") in the Vuze forums a year ago and it is still "not answered".

---

### Post by ko_ko_now on 2009-11-17
exactly same experience as Tapas Bose,
...

---

### Post by lovinglinux on 2009-11-17
I'm running Firefox 3.5.5 on KDE and I'm facing the same problem, when trying to associate the magnet link with Ktorrent.

---

### Post by =JoNaZ= on 2009-11-17
i keep getting:

```
Error :  no sources found for torrent
```

if i try to use magnet link in vuze...

---

### Post by greylander on 2009-11-17
I also have the same problem.  I use Deluge.  I'm on Jaunty, 64-bit.

I tried the settings in the original post (subsituting path to deluge), with same result.

Looks like suddenly many people are having this problem... perhaps because piratebay has just started providing magnet links, , with big magnet-logo announcement on the main screen, so, like me, you decided to try them out for the first time?  :)

---

### Post by Prometheus28 on 2009-11-17
I am running ubuntu 9.04. Using ktorrent from synaptic gives me this error when i try to open magenet link (open url)

KTorrent
Version 3.2.1
Using KDE 4.2.2 (KDE 4.2.2)

> Could not start process Unable to create io-slave:
klauncher said: Unknown protocol 'magnet'.
.

I am unable to use azureus to open magnet links because claims is not found.

> 
Downloading From :magnet:?xt=urn:btih:98c5c361d0be5f2a07ea8fa5052e5aa48097e7f6&&&&...
Searching...
Error :  no sources found for torrent

---

### Post by greylander on 2009-11-17
The instructions in post #2 from erpel work to get Firefox directing the magnet link to the desired application... except I must not have the form of the command right.  Deluge starts up, but does not start a torrent for the magnet link.  If I try the same command from the command line, I get:

```
greylander@Tesseract:~$ deluge magnet:?xt=urn:btih:0c43bbd12170a1bf3be3287544e190fa7d04f9cf&dn=Enigma+all+albums&tr=http%3A%2F%2Ftracker.prq.to%2Fannounce
[1] 12051
[2] 12052
[2]+  Done                    dn=Enigma+all+albums
greylander@Tesseract:~$ 1.1.6
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))
Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/deluge/ui/gtkui/gtkui.py", line 260, in _on_new_core
    component.start()
  File "/var/lib/python-support/python2.6/deluge/component.py", line 198, in start
    _ComponentRegistry.start()
  File "/var/lib/python-support/python2.6/deluge/component.py", line 118, in start
    self.start_component(component)
  File "/var/lib/python-support/python2.6/deluge/component.py", line 130, in start_component
    self.components[name].start()
  File "/var/lib/python-support/python2.6/deluge/ui/gtkui/queuedtorrents.py", line 90, in start
    self.on_button_add_clicked(None)
  File "/var/lib/python-support/python2.6/deluge/ui/gtkui/queuedtorrents.py", line 195, in on_button_add_clicked
    self.liststore.foreach(add_torrent, None)
  File "/var/lib/python-support/python2.6/deluge/ui/gtkui/queuedtorrents.py", line 184, in add_torrent
    component.get("AddTorrentDialog").add_from_magnets([torrent_path])
  File "/var/lib/python-support/python2.6/deluge/ui/gtkui/addtorrentdialog.py", line 221, in add_from_magnets
    info_hash = base64.b32decode(uri.split("&")[0][20:]).encode("hex")
  File "/usr/lib/python2.6/base64.py", line 222, in b32decode
    raise TypeError('Non-base32 digit found')
TypeError: Non-base32 digit found
/var/lib/python-support/python2.6/deluge/ui/tracker_icons.py:70: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  log.debug("%s %s %s" % (url, e, e.message))


```

---

### Post by maxxer on 2009-11-17
i guess %s should be enclosed in double quotes, so:
```
"%s"
```

---

### Post by lunatic1234 on 2009-11-17
Hi!

Here is a solution to this problem for Vuze:
[http://forum.vuze.com/thread.jspa?threadID=86970&tstart=0](http://forum.vuze.com/thread.jspa?threadID=86970&tstart=0)

"According to [http://www.bittorrent.org/beps/bep_0009.html#magnet-uri-format](http://www.bittorrent.org/beps/bep_0009.html#magnet-uri-format) , info-hash in a magnet URI should be in HEX. For compatibility a client **should also** support info-hashes in base32 encoding.

However, Azureus recognizes **only** magnet URIs with info-hashes in base32. For magnet URIs with info-hashes in HEX it just sits there a while, trying to find the torrent, and then fails to do so (apparently it interprets the hash as base32-encoded when it is really just HEX-encoded).

This feature has been fixed in version 4.3.0.1_b04
You can download it from here:
[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

---

### Post by size_XXM on 2009-11-17
@Prometheus, lovinglinux: Ktorrent [does NOT support magnet links](http://ktorrent.org/wiki/index.php/FAQ#Does_KTorrent_support_magnet_links.3F) yet.

---

### Post by karlmp on 2009-11-17
use rtorrent

---

### Post by Prometheus28 on 2009-11-17
> **lunatic1234 said:**
> Hi!

Here is a solution to this problem for Vuze:
[http://forum.vuze.com/thread.jspa?threadID=86970&tstart=0](http://forum.vuze.com/thread.jspa?threadID=86970&tstart=0)

"According to [http://www.bittorrent.org/beps/bep_0009.html#magnet-uri-format](http://www.bittorrent.org/beps/bep_0009.html#magnet-uri-format) , info-hash in a magnet URI should be in HEX. For compatibility a client **should also** support info-hashes in base32 encoding.

However, Azureus recognizes **only** magnet URIs with info-hashes in base32. For magnet URIs with info-hashes in HEX it just sits there a while, trying to find the torrent, and then fails to do so (apparently it interprets the hash as base32-encoded when it is really just HEX-encoded).

This feature has been fixed in version 4.3.0.1_b04
You can download it from here:
[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

I can confirm that luna 's solution works using vuze azereus version 4.3.0.1_b04. I have it running as local install.

> [QUOTE]magnet:?xt=urn:btih:98c5c361d0be5f2a07ea8fa5052e5aa48097e7f6&&&&[/QUOTE]

and other magnet links from the pirate bay tpb.

---

### Post by size_XXM on 2009-11-17
So what's the verdict? Which of the GUI-driven, repository-supplied clients (also repository-supplied versions) have working support for TPB (hex) magnet links in Karmic?

---

### Post by utkjamie on 2009-11-17
> **size_XXM said:**
> @Prometheus, lovinglinux: Ktorrent [does NOT support magnet links]("http://ktorrent.org/wiki/index.php/FAQ#Does_KTorrent_support_magnet_links.3F") yet.

That's *so* frustrating. The bug report referenced in the link even states that the magnet technology has been stable since *2002*. Wonder why this is still only a TODO item for the Ktorrent developers.

---

### Post by lovinglinux on 2009-11-17
> **size_XXM said:**
> @Prometheus, lovinglinux: Ktorrent [does NOT support magnet links](http://ktorrent.org/wiki/index.php/FAQ#Does_KTorrent_support_magnet_links.3F) yet.

Thanks for the info.

---

### Post by lunatic1234 on 2009-11-17
> **size_XXM said:**
> So what's the verdict? Which of the GUI-driven, repository-supplied clients (also repository-supplied versions) have working support for TPB (hex) magnet links in Karmic?

I think none of them? So far, only torrent client I have found for linux with the magnetic link support that TPB uses, is Vuze. And only that 4.3.0.1_B04 version, so you have to get it directly from their website. But its _very_ easy to install.

---

### Post by grege on 2009-11-18
As well as above you need to follow this thread (even if you use Kubuntu) to make magnet links work in Firefox. Substitute /usr/bin/deluge for azureus

[http://ubuntuforums.org/showthread.php?t=229924](http://ubuntuforums.org/showthread.php?t=229924)

---

### Post by Falc7 on 2009-11-18
> **grege said:**
> As well as above you need to follow this thread (even if you use Kubuntu) to make magnet links work in Firefox. Substitute /usr/bin/deluge for azureus

[http://ubuntuforums.org/showthread.php?t=229924](http://ubuntuforums.org/showthread.php?t=229924)

I've tried those 3 commands, still dosen't work with deluge

---

### Post by anders_c_ on 2009-11-18
> I think none of them? So far, only torrent client I have found for linux with the magnetic link support that TPB uses, is Vuze. And only that 4.3.0.1_B04 version, so you have to get it directly from their website. But its _very_ easy to install.

From the info on TPB:

> These are "magnet links", a link that lets you download a torrent directly in your BitTorrent client, instead of your browser. Most clients supports this (uTorrent, Vuze, rtorrent, whatever) and will get the relevant torrent data over the DHT network.

Is the info on TPB incorrect or is it only the windows version of rtorrent that works...because I compiled latest rtorrent from source and still haven't managed to open a magnet link with it.

Edit:
The magnet link to Karmic ISO on TPB is:
```
magnet:?xt=urn:btih:b65333c904f35428c09811a01032666f98abff67&dn=ubuntu-9.10-desktop-i386.iso&tr=http%3A%2F%2Fdenis.stalker.h3q.com%3A6969%2Fannounce
```

am I supposed to be able to start downloading by running:
```
rtorrent magnet:?xt=urn:btih:b65333c904f35428c09811a01032666f98abff67&dn=ubuntu-9.10-desktop-i386.iso&tr=http%3A%2F%2Fdenis.stalker.h3q.com%3A6969%2Fannounce
```
Or do i have to change something in that magnet link?? I have tried to start rtorrent and loading it afterwards to but nothing seems to work.

---

### Post by KIAaze on 2009-11-18
In Vuze/Azureus, it's not necessary to change the magnet link, so I suppose it would be the same for rtorrent.

However, I have also not been able to use the magnet links with rtorrent (tried repository package).

---

### Post by anders_c_ on 2009-11-18
It works with uTorrent 1.8.5 through wine...

---

### Post by poisonkiller on 2009-11-18
Does anyone know, how to make magnet links work with KDE+Firefox+Deluge? I've tried adding those two settings in about:config with Deluges path (/usr/bin/deluge), but it doesn't work.

---

### Post by karlmp on 2009-11-18
the only client I care about is rtorrent
[http://libtorrent.rakshasa.no/ticket/955](http://libtorrent.rakshasa.no/ticket/955)

---

### Post by grege on 2009-11-18
> **poisonkiller said:**
> Does anyone know, how to make magnet links work with KDE+Firefox+Deluge? I've tried adding those two settings in about:config with Deluges path (/usr/bin/deluge), but it doesn't work.

Mine works with karmic Kubuntu AMD64

The about:config above has an error in the syntax

network.protocol-handler.app.magnet   /usr/bin/deluge
network.protocol-handler.external.magnet  true

plus run these gconf commands amending to deluge rather than azureus

[http://ubuntuforums.org/showthread.php?t=229924](http://ubuntuforums.org/showthread.php?t=229924)

The first time it runs it will ask if you want to make deluge the default magnet handler, thereafter it just fires up deluge and starts. Magnets look a bit different and take a bit longer to start than torrents so don't panic if it looks different for the first 30 seconds.

---

### Post by grege on 2009-11-18
ps

It is not easy to fix stuffed about:config entries. You will need to open ~/.mozilla/firefox/xxxxxxxx/prefs.js with kate and fix the entry that is wrong, where xxxxxxxx is a bunch of letters and numbers that is different for each install.

---

### Post by trytenn on 2009-11-19
Hi! I think I have a similar problem to anders_c.
I can't open the magnet links on TPB, but on mininova isn't it a problem. I run ubuntu karmic, firefox 3.5.5 and vuze v4. The magnet link URI looks diffrent. Example with a US Now torrent (legal):
```
TPB:
magnet:?xt=urn:btih:24ec1f97b8288b15943096278dcf11c4487416e0&dn=US_NOW-720.mp4&tr=http://tracker.openbittorrent.com/announce

Mininova:
magnet:?xt=urn:btih:ETWB7F5YFCFRLFBQSYTY3TYRYREHIFXA
```Do anyone know anything about this? Anders, does the links work on mininova for you?

EDIT:
I saw this help after i posted.
[lunatic1234]("http://ubuntuforums.org/member.php?u=958243") wrote: 
> However, Azureus recognizes **only** magnet URIs with info-hashes in base32. For magnet URIs with info-hashes in HEX it just sits there a while, trying to find the torrent, and then fails to do so (apparently it interprets the hash as base32-encoded when it is really just HEX-encoded).

This feature has been fixed in version 4.3.0.1_b04

---

### Post by KIAaze on 2009-11-19
Here's your answer:
> **lunatic1234 said:**
> Hi!

Here is a solution to this problem for Vuze:
[http://forum.vuze.com/thread.jspa?threadID=86970&tstart=0](http://forum.vuze.com/thread.jspa?threadID=86970&tstart=0)

"According to [http://www.bittorrent.org/beps/bep_0009.html#magnet-uri-format](http://www.bittorrent.org/beps/bep_0009.html#magnet-uri-format) , info-hash in a magnet URI should be in HEX. For compatibility a client **should also** support info-hashes in base32 encoding.

However, Azureus recognizes **only** magnet URIs with info-hashes in base32. For magnet URIs with info-hashes in HEX it just sits there a while, trying to find the torrent, and then fails to do so (apparently it interprets the hash as base32-encoded when it is really just HEX-encoded).

This feature has been fixed in version 4.3.0.1_b04
You can download it from here:
[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

The pirate bay uses magnet links in hex instead of base 32 like mininova.
The latest stable Vuze version (4.3.0.0) supports magnet links in base 32, but not in hex.
You will have to use the beta version 4.3.0.1_b04.

Other clients seem to support base 32 magnet links, but from my experience the Vuze beta is the only one currently supporting hex links.

---

### Post by KIAaze on 2009-11-19
I wrote a little script to convert magnet links from hex into base 32. :)

It simply takes the hex link as input and outputs the base32 link, so you should be able to use it with any torrent client supporting CLI input of base32 magnet links like this:
```
CLIENT_COMMAND $(PATH_OF_SCRIPT/magnet_converter.py "HEX_MAGNET_LINK")

```

Don't forget to put "" around the magnet link!

Usage examples:
```
$ magnet_converter.py "magnet:?xt=urn:btih:ea53d1923abf55ae93276988275e29bc92a02be7&dn=Debian+GNU-Linux+Bible&tr=http%3A%2F%2Ftracker.openbittorrent.com%2Fannounce"
magnet:?xt=urn:btih:5JJ5DER2X5K25EZHNGECOXRJXSJKAK7H&dn=Debian+GNU-Linux+Bible&tr=http%3A%2F%2Ftracker.openbittorrent.com%2Fannounce

$ ./azureus $(magnet_converter.py "magnet:?xt=urn:btih:ea53d1923abf55ae93276988275e29bc92a02be7&dn=Debian+GNU-Linux+Bible&tr=http%3A%2F%2Ftracker.openbittorrent.com%2Fannounce")
Starting Azureus...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Java exec found in PATH. Verifying...
...

```

Edit: It seems to work best when there are a lot of seeders. I had a few failures with less popular torrents. But the conversion itself seems to work correctly.

---

### Post by gilgongo on 2009-11-19
Excellent! Works great! Thanks!

---

### Post by spazzm on 2009-11-19
I'm also having trouble with Deluge.
The configuration for Firefox works fine, Deluge opens but the torrent is not added to the queue. The buttons for adding new torrents are also disabled - only solution seems to be restarting Deluge.

The only BT client I've found so far with working magnet link support available in the repositories is **qbittorrent**:

[FONT=Courier New]sudo apt-get install qbittorrent[/FONT]

Then configure Firefox as above with /usr/bin/qbittorrent instead of /usr/bin/deluge or /usr/bin/vuze

---

### Post by KIAaze on 2009-11-19
Thanks for the tip.
Just tested it and drag and drop of the magnet links into qbittorrent works too. :D
I wonder why they haven't added the possibility to open magnet links through file->open URL.

---

### Post by Sav on 2009-11-20
> **anders_c_ said:**
> It works with uTorrent 1.8.5 through wine...

wich string do you use in firefox?
I have to always copy the magnet link and paste it in utorrent.

---

### Post by Falc7 on 2009-11-20
> **grege said:**
> Mine works with karmic Kubuntu AMD64

The about:config above has an error in the syntax

network.protocol-handler.app.magnet   /usr/bin/deluge
network.protocol-handler.external.magnet  true

plus run these gconf commands amending to deluge rather than azureus

[http://ubuntuforums.org/showthread.php?t=229924](http://ubuntuforums.org/showthread.php?t=229924)

The first time it runs it will ask if you want to make deluge the default magnet handler, thereafter it just fires up deluge and starts. Magnets look a bit different and take a bit longer to start than torrents so don't panic if it looks different for the first 30 seconds.

Okay: So is this right? If so i could post it as a HowTo

Okay so i put these into terminal:
```
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/deluge %s"
```
```
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
```
```
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true
```

> *Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.app.magnet /usr/bin/deluge -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.external.magnet true -> Value -> /usr/bin/deluge
* Ensure network.protocol-handler.expose-all is set to true. (mine was already)


---

### Post by AntoineL on 2009-11-20
I used the Python script of KIAaze and made a quick GTK+ GUI for it.

Here it is!

---

### Post by KIAaze on 2009-11-20
Woohoo! The joys of open-source. :) (well, I didn't put any license in, but let's say it's public domain + I reused code from [here]("http://code.activestate.com/recipes/111286/"))

I was thinking about making it return a base32 magnet link if it's already base32. This would allow it to be used with any torrent site by using the Firefox magnet protocol configuration and some client who wants base 32 magnet links.
But I still haven't tried configuring Firefox for that. :oops:

---

### Post by grege on 2009-11-20
> **Falc7 said:**
> Okay: So is this right? If so i could post it as a HowTo

That is what worked for me with Kubuntu AMD64 karmic, KDE 4.3.2, Firefox 3.5.5 and Deluge 1.1.9

about:conf should read

network.protocol-handler.app.magnet  Value  /usr/bin/deluge
network.protocol-handler.external.magnet   Value true

These are from my Bash history

gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/deluge %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true

Note: Firefox is compiled as a Gtk program and thus the Gnome commands are what controls it. The gconf commands will need some of the Gnome libs installed, but most KDE installs still have some gnome libraries installed as well. I cannot help with that minimum as I have a full Gnome installed in parallel and can not tell what is needed. I guess if the gconf commands work then you have enough, and with Firefox installed there should be enough.

ps try eztv.it for a test to avoid the other issue being discussed in this thread

---

### Post by AntoineL on 2009-11-20
Another quickfix would be to go edit the code of Deluge directly.

In the file /usr/share/pyshare/deluge/ui/gtkui.py, in the function add_from_magnet (line 219), replace:
```
info_hash = base64.b32decode(uri.split("&")[0][20:]).encode("hex")
```
with:
```
try:
    info_hash = base64.b32decode(uri.split("&")[0][20:]).encode("hex")
except TypeError:
    info_hash = uri.split("&")[0][20:]
```

---

### Post by Nekow42 on 2009-11-20
I used the Python script made by KIAaze and hacked together a tkinter interface. I know there is already a GTK+ interface, but since tkinter ships standard with python for other operating systems, this might be helpful to someone out there. Also, more choices is good :) 

As with the parent script, this is public domain.

---

### Post by anders_c_ on 2009-11-21
> **Sav said:**
> wich string do you use in firefox?
I have to always copy the magnet link and paste it in utorrent.

I can't start them from firefox either, I just meant that they work if i copy paste. I don't even use firefox :P

---

### Post by kobbi on 2009-11-21
> **KIAaze said:**
> I wrote a little script to convert magnet links from hex into base 32. :)

You sure did KIAaze and it works awesome for me. Thank you and good job dude!

---

### Post by KIAaze on 2009-11-22
Don't miss the GUIs for it: :)
[http://ubuntuforums.org/showpost.php?p=8357695&postcount=35](http://ubuntuforums.org/showpost.php?p=8357695&postcount=35)
[http://ubuntuforums.org/showpost.php?p=8358428&postcount=39](http://ubuntuforums.org/showpost.php?p=8358428&postcount=39)

And what's even better IMO, the [deluge]("http://deluge-torrent.info/") "patch":
[http://ubuntuforums.org/showpost.php?p=8358327&postcount=38](http://ubuntuforums.org/showpost.php?p=8358327&postcount=38)
(Which could simplify my script a lot too. Maybe I'll work on it again.)
Note: For me the changes were in /usr/share/pyshared/deluge/ui/gtkui/addtorrentdialog.py at line 219.
For deluge-1.2.0_rc3, it's in deluge/ui/gtkui/addtorrentdialog.py at line 229.

Deluge developers already know about it apparently:
[http://forum.deluge-torrent.info/viewtopic.php?f=7&t=548&p=111005&hilit=magnet+links&sid=91e6d43238e42424bf848cfe29f75476#p111005](http://forum.deluge-torrent.info/viewtopic.php?f=7&t=548&p=111005&hilit=magnet+links&sid=91e6d43238e42424bf848cfe29f75476#p111005)
[http://forum.deluge-torrent.info/viewtopic.php?f=7&t=25875&p=110995&hilit=magnet+links&sid=91e6d43238e42424bf848cfe29f75476#p110995](http://forum.deluge-torrent.info/viewtopic.php?f=7&t=25875&p=110995&hilit=magnet+links&sid=91e6d43238e42424bf848cfe29f75476#p110995)

---

### Post by Sav on 2009-11-22
For me, the following solution worked:

Distro: Ubuntu karmic 64 bit

1) Installed azureus from synaptic

2) downloaded the last beta from: [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

3) sudo cp "the_file_just_downloaded".jar /usr/share/java/Azureus2.jar

4) started azureus

5) started firefox

6) clicked on a magnet link

7) when firefox asked wich application should manage the magnet link, chosed /usr/bin/azureus

8) the linked was passed to azureus

Tested on my favorite bay.

---

### Post by huanix on 2009-11-22
I got a different result: Firefox doesn't know how to open this address, because the protocol (magnet) isn't associated with any program.

This could be because i've tried 11 other half-baked schemes to get it to work... firefox recognizes magnet as a communication protocol, not as a file that requires an external application to open it..

---

### Post by grege on 2009-11-22
> **huanix said:**
> I got a different result: Firefox doesn't know how to open this address, because the protocol (magnet) isn't associated with any program.

This could be because i've tried 11 other half-baked schemes to get it to work... firefox recognizes magnet as a communication protocol, not as a file that requires an external application to open it..

Just rename your ~/.mozilla to .mozilla.old and restart a clean Firefox.

Warning all your extensions and favourites will be gone.

---

### Post by cstr on 2009-11-27
> **KIAaze said:**
> Don't miss the GUIs for it: :)
[http://ubuntuforums.org/showpost.php?p=8357695&postcount=35](http://ubuntuforums.org/showpost.php?p=8357695&postcount=35)
[http://ubuntuforums.org/showpost.php?p=8358428&postcount=39](http://ubuntuforums.org/showpost.php?p=8358428&postcount=39)

And what's even better IMO, the [deluge]("http://deluge-torrent.info/") "patch":
[http://ubuntuforums.org/showpost.php?p=8358327&postcount=38](http://ubuntuforums.org/showpost.php?p=8358327&postcount=38)
(Which could simplify my script a lot too. Maybe I'll work on it again.)
Note: For me the changes were in /usr/share/pyshared/deluge/ui/gtkui/addtorrentdialog.py at line 219.
For deluge-1.2.0_rc3, it's in deluge/ui/gtkui/addtorrentdialog.py at line 229.

Deluge developers already know about it apparently:
[http://forum.deluge-torrent.info/viewtopic.php?f=7&t=548&p=111005&hilit=magnet+links&sid=91e6d43238e42424bf848cfe29f75476#p111005](http://forum.deluge-torrent.info/viewtopic.php?f=7&t=548&p=111005&hilit=magnet+links&sid=91e6d43238e42424bf848cfe29f75476#p111005)
[http://forum.deluge-torrent.info/viewtopic.php?f=7&t=25875&p=110995&hilit=magnet+links&sid=91e6d43238e42424bf848cfe29f75476#p110995](http://forum.deluge-torrent.info/viewtopic.php?f=7&t=25875&p=110995&hilit=magnet+links&sid=91e6d43238e42424bf848cfe29f75476#p110995)

And for deluge-1.1.6 (jaunty):

/usr/share/python-support/deluge/deluge/ui/gtkui/addtorrentdialog.py @ line 221

---

### Post by Utopic on 2009-12-02
Does anyone has a solution for rtorrent ? :-)

---

### Post by Sefianix on 2009-12-04
Just wanted to mention that qBittorrent (in the repos) worked for me.  Just dragged the magnet link from FF to the qBittorrent window and away it went.  not as nice as simply clicking on the magnet link in FF but it'll do. :popcorn:

---

### Post by NFblaze on 2009-12-04
To let other people know that the current nightly in Transmission has support for magnet links now via both the command line and the torrent gui and supports drag and drop magnet-linking. Nothing yet about firefox enabling a clickable magnet uri. Though, I've used them before and they are designed to be copiable text anyway.

---

### Post by admasb on 2012-09-21
Still not solved

---

### Post by oldos2er on 2012-09-21
Please don't bump old threads, start a new thread instead. From the posting guidelines:

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

