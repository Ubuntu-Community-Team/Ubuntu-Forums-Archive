---
title: "Little newbie questions"
date: 2006-02-22
forum: General Help
---

### Post by Qwertie on 2006-02-22
I have some experience with Linux, but could someone clarify a few things?

System settings shows my webcam under "Digital Camera": a D-Link DSC 350+.  How can I get a webcam window to see if it is working?  Are there any Linux IM programs I can use with the webcam?

I started the "Adept Updater", curious what it was.  After clicking "Fetch Updates" in the otherwise blank window, it showed a list of packages and (without my having done anything) the action was set to "upgrade" or "install" for every single package (IIRC, less than ten of the packages weren't already installed.)  So I accepted its choices and, well, it spent quite some time updating.

My question is, what's the difference between the adept "updater" and regular Adept (I notice that it lists fewer packages) and why does it automatically update or install everything on the list?

I'm having some minor problems with the default video player, Kaffeine (although it is working, after I installed the 'restricted' codecs.)  What other video players are available?  Recommendations?

Is there a keyboard shortcut to Copy to clipboard in Konsole?

As it happens, I have two bootable hard drives and plan to install Linux on the other one, RSN.  What's the deal with permissions across installations, I mean, when running distro "A", can I expect problems accessing the ext2/3 partition that was created by a distro "B"?

Where can I learn more about how these "magic" software installations work in Adept?  How do the icons for the programs I install end up in the K menu?

Why does my computer beep when I hold Shift for 5 seconds?  It's as though it's scolding me :)

TIA!

---

### Post by thomasando on 2006-02-22
I'll answer the few questions I know the answer to off the top of my head. I've only been using Ubuntu for a few days, but have been using Linux for many, many years.

I think Adept Updater will automatically update all packages that have updates available, and install any dependent packages. That will by why all packages are marked as 'update' - it's only show the ones that there's updates for! The ones marked upgrade will be upgraded, the ones marked install will be installed because they're dependencies from some other package that is being upgraded. The adept application can be used to do a system-wide update (like Adept Updater), but it is much more useful to search for packages that aren't installed that you are able to install - for instance if you wanted to install a program such as KPilot, you would use Adept. Does that clarify it somewhat?

Check out xine for a media player, though it will probably have a long dependency chain as it's a GTK application... another alternative that I have used in the past is mplayer/kmplayer.

You wont have any problems accessing partitions created by your other distro. For instance, I have 2 installations of Linux presently (Gentoo and Kubuntu). I can access all the filesystems from my Gentoo systems, and the permissions on my Home Directories that were created in Gentoo don't need to be edited. I think as long as the username is the same on both distro's, then you'll be right.

---

### Post by Qwertie on 2006-02-22
Hmm, well I heard somewhere that permissions were based on user numbers rather than names... if so, I have no idea how to modify user numbers.

Thanks for the info. Does Adept Updater deal with the same list of packages that Adept does? I'd guess yes. Does it download any new version of anything, and does it stick to stable versions or does it also grab e.g. alpha versions? I might ask the same question of Adept proper.

I see many xines in Adept, 3 of which are "video players": totem-xine, xine-ui and gxine. Funny, there's no plain xine...

Adept didn't find a "mplayer", but after I added the "backports" repository, there's now a "MPlayer-Plugin for Mozilla". My favorite Windows media player is Media Player Classic (mplayerc)... I don't suppose mplayer is related?

---

### Post by thomasando on 2006-02-22
Re user numbers: that's possibly correct. Perhaps the UID's just happened to be the same between Gentoo and Kubuntu on my system. Either way, they can be changed. KUser ought to do it (or the user area in kcontrol). I know for a fact that webmin can do it, but it's not installed by default. You can edit UID's through a console, too.

I believe Adept Updater and Adept use the same package info. They will both use the repositories that you have setup (in Adept). It will stick to stable packages, unless you have added repositories to allow it to get unstable packages.

xine-ui is the one you want. Check which dependencies it's going to install (use the check boxes to show only packages that are flagged for install that aren't already installed) first to get an idea of what else it's going to put on your system. May be hardly anything, may be a lot - I don't know as I haven't done it yet myself.

mplayer is totally unrelated to mplayerc on Windows. One is a Microsoft product, the other is open source. That said, there may not be an official build of mplayer for ubuntu. You can probably do a search in adept for video or media and get a good list of media players. To see ones that are specifically for kde, have a look at [http://www.kde-apps.org]("http://www.kde-apps.org")

---

### Post by ltmon on 2006-02-22
You may not be aware of possibly the single greatest thing about Linux (at least I think so).  When you want to copy something from Konsole, simply select it - there's no more key pressing required.

Then you can paste it at any time using middle click.

This is true for any application... select to copy, middle-click to paste.

Also have a look at "klipper" (it should be installed by default).  It will start in your system tray, and keep a history of you clipboard.

L.

---

### Post by Qwertie on 2006-02-22
That clipboard behavior is pretty interesting.

New question!  How do I find out how much disk space I have left?  I want to download a 2.5gig file on my 5gig linux partition and I dunno if it'll work...

Regarding Media Player Classic, it's not a Microsoft product; it's just designed to look like the older, leaner Microsoft Media Player 6.4.  But it's packed with useful features so if there were something like it on Linux, I'd be very pleased.

---

### Post by thomasando on 2006-02-23
The command 'df' (at a console - hit alt+f2 to get the run command, then type 'konsole' and hit enter to start it) will show you the disk usage. If all you've done is installed kubuntu then you should have enough space left for a 2.5GB file easily. df by default will show you in bytes how much space is used/available.

Fair enough about mediaplayer - cant say what it's like as I only use Windows at work, and havent used windows at home for years. There are plenty of good media players around for Linux, it's just a matter of finding them.

---

### Post by xtacocorex on 2006-02-23
Shift+Insert will paste into Konsole. 

If you're running Klipper, you need to watch what you paste as any selected text is saved by Klipper, so you might have to select what you want to paste into Konsole if it doesn't paste the right text.

This is the main reason why I don't use Klipper, but that's me. Other people may swear by it. That's just my experience with it.

---

