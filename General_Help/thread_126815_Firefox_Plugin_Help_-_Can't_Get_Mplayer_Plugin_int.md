---
title: "Firefox Plugin Help - Can't Get Mplayer Plugin into Firefox"
date: 2006-02-07
forum: General Help
---

### Post by Ingla on 2006-02-07
Hello.

I've been having no end of trouble with streams.

I went to about: plugins in Firefox and saw that gxine was the main plugin. However, it can't play almost anything...messages such as "no demuxer..", etc. So I renamed the file. Now Firefox shows no plugins except the following:

===================================================
Shockwave Flash
Default Plugin
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
Adobe Reader 7.0
Java(TM) Plug-in 1.5.0_05-b05
====================================================
All are enabled except the Default Plugin.

I used Automatix to install Mplayer "with the plugins". I later noticed in Synaptic that mplayer plugins showed as not installed. So, I installed them "again". (Synaptic currently lists no mplayer plugins...installed or otherwise).

Searching the filesystem, I found that mplayerplug-in.so exists in:

====================================================
/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins
/usr/lib/firefox/plugins
/usr/lib/netscape/plugins
====================================================

mplayerplug-in.xpt is found in:

====================================================

usr/lib/mozilla/plugins
usr/lib/mozilla-firefox/plugins
usr/lib/firefox/plugins

It is also in:

/usr/lib/mozilla-firefox/components

where I copied it because some plugin how-to said it should be in components.
For some reason, this last location is not found by Search for Files...but it's there and it appears in File Browser (I wonder what else Search is failing to report). Maybe Firefox can't see it for the same reason (whatever that is). I did the copying as root because of the directory permissions.

===================================================
/usr/lib/mozilla does not contain a directory called "components".
Neither does /usr/lib/firefox or /usr/lib/netscape.

I have closed and re-opened Firefox and even shut down the computer. No Mplayer plugins appear in Firefox (about: plugins).

I've been trying hard to get the multimedia situation fixed in Ubuntu, but this is really getting baffling. I checked out a Realplayer clip and that plugin worked fine. But I can't see or hear any other kinds of streams. 

Maybe I'm wrong, but I figured Mplayer would be a logical first attempt. 

Can anyone help get the plugin working?

Many thanks.

---

### Post by dcstar on 2006-02-08
[QUOTE=Ingla]Hello.

I've been having no end of trouble with streams.
........
Can anyone help get the plugin working?

Many thanks.[/QUOTE]
You may want to install mozplugger and see how that works.

---

### Post by Ingla on 2006-02-08
Hi.

Guess what! I have pretty good streaming on all kinds of formats. Here's the story, in the hope that anyone with difficulties in this area can benefit.

First of all, I did get the mplayer plugins into Firefox. I did a search for some plugin files that appeared in about: plugins, and found out that Firefox 1.5 was reading from /opt/... not /usr/. So, I put mplayerplug-in.so into "plugins" and mplayerplug-in.xpt into "components"...re-opened Firefox and voila.

Unfortunately, I still couldn't see or hear many streams. IMO, mplayer just isn't any good. It just hangs on everything until you xkill it. I had had this problem in my previous installation and had manually entered mrl's in other media programs.

Also, Firefox tried opening video streams in gxine, which could play only the audio part.

Still searching, I found quite a good solution. The problem seems to lie with Firefox. I installed the MediaPlayerConnectivity Extension, available at: [https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446) .

It runs a configuration wizard on Firefox startup after it's installed. I let it do its thing without changing defaults. Still had problems. It wanted to use mplayer for Windows Media Player files...but we've already mentioned mplayer's behavior. Also, it replaced realplay as the default for Real Player files.

So, one goes (in Firefox) to Tools>Extensions>MediaPlayerConnectivity. At the bottom of the window, hit Preferences. This brings up the extension's config. There you select which player it should use for various file types. Browse to /usr/bin/ and they're all there (if you have them installed). Try opening various streams until you've found the player that works and bingo. This works so, if you're having problems, keep playing with the extension preferences...it's not hard.

Warning: It opens things kind of slowly and you have to click its little icon to make it play the stream. Then it brings up your player...if nothing seems to be happening, wait a minute.

I have it set for "Smart Play" which looks for alternative addresses for the stream and lets you pick one. They don't all work. You might get an error notice like "Missing Component". Just try another address.

That's it. I think the extension is great. Streaming is not as quick and straightforward as it is under Windows but, for me, it's good enough not to send me back there. It's a great step forward for Firefox.

All's well that ends well. Thanks, everyone, for all the help.

---

### Post by nix4me on 2006-02-08
mplayer and mplayerplug-in works fine.  If you install the w32 codecs it will play almost everything.

You must either have something misconfigured, or you haven't installed the w32 codecs.

nix4me

---

### Post by Ingla on 2006-02-08
Don't know. I did install the codecs...I don't think that's causing the hanging. It hangs not only when accessed by Firefox, but also when opening manually and giving it an location to play. None of the other players does this. It doesn't try to play anything...no errors notices...nothing. Just freezes when you hit "OK". I've tried uninstalling, re-installing (in the past)...nothing helped.

At least the new setup is getting me almost everything I want....first time that's been the case since I started trying to use Linux.:D

---

