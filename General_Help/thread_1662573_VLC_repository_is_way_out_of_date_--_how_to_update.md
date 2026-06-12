---
title: "VLC repository is way out of date -- how to update repository?"
date: 2011-01-08
forum: General Help
---

### Post by nrundy on 2011-01-08
I've noticed that Synaptic shows VLC 1.0.6 as the latest version of VLC. Except this is not true and 1.0.6 is way out of date. Version 1.0.6 does not even have a REPEAT icon button for the control panel. But newer versions do. Running Windows I can download VLC version 1.1.5 and make use of a REPEAT icon.  Is there a way to update the repository? Or a way to tell Ubuntu developers that the VLC repository is way out of date and needs updating? I'm running 10.04 LTS--I thought this was supposed to deliver longterm updates?

---

### Post by Verbeck on 2011-01-08
[s]you could follow the instructions on the videolan website
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
[/s]
> [s]Command line way[FONT=monospace]:
[/FONT]sudo add-apt-repository ppa:lucid-bleed/ppa
sudo apt-get update
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc[/s]

edit: see the next post by [mc4man]("http://ubuntuforums.org/member.php?u=320715")

---

### Post by mc4man on 2011-01-08
You did leave out this one line
"At your OWN risks, install VLC from PPA:"

Most of the ppa's offering an updated vlc for lucid are now backporting from maverick and as such are replacing your ffmpeg shared libs.
This will break some apps/plugins which may or may not matter on an individual basis.

The ppa's do offer some replacements, but not all for affected apps.

The lucidbleed has alot of packages which you may or may not appreciate.

Alt. means thru ppa's

Add this ppa for updated vlc, enable and update
[https://launchpad.net/~n-muench/+archive/vlc?field.series_filter=lucid](https://launchpad.net/~n-muench/+archive/vlc?field.series_filter=lucid)

 Then add this ppa and update for new gstreamer ffmpeg plugin (uses it's own internal ffmpeg) and other updated gstreamer packages
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

If you use mplayer then you'll need a new build - this provides current svn builds
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

---

### Post by QLee on 2011-01-08
[QUOTE=nrundy]... I'm running 10.04 LTS--I thought this was supposed to deliver longterm updates?[/QUOTE]

After release you get security upgrades, not feature upgrades, Long Term Support is a measure of stability, not newness of  program version. You get a system that continues to work and is secure very useful in enterprise applications . New features to software often bring new bugs, new features are tested in newest release or in release candidates. LTS releases are meant to be stable.

---

### Post by nrundy on 2011-01-08
So once an LTS finalizes, none of the programs are updated unless it is security/stability related?

To get a newer version of VLC with a repeat icon, I would have to:
1.) wait 2 years for the next LTS
2.) use a PPA at my own risk
3.) use one of the non-LTS releases (e.g., 10.10)

Do I understand all this accurately?   Thanks for the help guys :)

---

### Post by mc4man on 2011-01-08
> Do I understand all this accurately? 
you do

the other option is to build your own version of vlc or anything else where newer versions are desired.

(the last 2 ppa's I mentioned, gstreamer and mplayer, are what I'd term 'highly trusted', no risk at all.

---

### Post by nrundy on 2011-01-08
> **mc4man said:**
> you do

the other option is to build your own version of vlc or anything else where newer versions are desired.

(the last 2 ppa's I mentioned, gstreamer and mplayer, are what I'd term 'highly trusted', no risk at all.

I'm assuming to build my own version I need to compile from source or something. I have no idea how to do this--way over my head.

I like VLC, so since there is no "highly trusted" ppa of that I guess I'll wait for next LTS or have to use 10.10. 

Thanks for the clarification and pointing out the highly trusted ones though :)

---

### Post by mc4man on 2011-01-08
I believe, from looking thru what the muench ppa has, that it would serve you well.
I cannot however 100% vouch for it because I've never tested it, don't use lucid.

If the time arises you wish to build vlc, either a release (1.1.X) or the dev version (1.2+) there is an excellent howto in the Tips.. sub forum that will not let you down.
(designed for the dev version , easily adapted to a release if desired

---

### Post by bumder on 2011-01-08
I'm currently on 10.04, and use the muench ppa.

Currently on vlc 1.1.4 'the luggage', and have had no problems with it.

---

### Post by QLee on 2011-01-08
[QUOTE=nrundy]...
I like VLC, so since there is no "highly trusted" ppa of that I guess I'll wait for next LTS or have to use 10.10. 
...[/QUOTE]

And keep everything in perspective, it's likely that a ppa on launchpad has a significant number of users in the community and any problems would likely be discussed at length in the forums. It may be a risk you are willing to take, especially if you don't have to do "support" for a bunch of users on your system.

---

### Post by craig.o on 2011-01-24
> **mc4man said:**
> You did leave out this one line
"At your OWN risks, install VLC from PPA:"

...Add this ppa for updated vlc, enable and update
[https://launchpad.net/~n-muench/+archive/vlc?field.series_filter=lucid](https://launchpad.net/~n-muench/+archive/vlc?field.series_filter=lucid)...[/url]

[Update] Make note that the correct ppa name for the Lucid (10.04) distribution is posted at the top of the page (ppa:n-muench/vlc2). 

Thanks for the info!

-Craig

---

