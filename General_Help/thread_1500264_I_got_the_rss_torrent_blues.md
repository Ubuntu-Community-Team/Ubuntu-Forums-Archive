---
title: "I got the rss torrent blues"
date: 2010-06-02
forum: General Help
---

### Post by nbv4 on 2010-06-02
This is something that *should* be easy. This is what I want to do:

1. I give an RSS url, a reges, and a download location to a torrent client.
2. The client then automatically refreshes that feed url every X minutes, and once a item shows up in the feed that matches my regex, it downloads it to a folder I specified.

Yet every few months, going back to at least 2007, I attempt to get this working in ubuntu, but I can never do it. Well, it's that time of the year again, I'm trying to get this working, and am having no luck. This is what I've tried so far:

1. Deluged - apprently older versions had a flexget plugin, but the latest version of deluged (the version that comes with lucid) does it completely different. Apparently you have to use this thing called "FlexGet", which is about the polar opposite of easy to use. I can't tell if you're supposed to install a deluged plugin for flexget, or a flexget plugin for deluged. Or no plug in at all. Flexget has a yaml config system which is way more complicated than it needs to be. All I have an RSS url, a regex, and a download location. What else do you want?

I also tried a tutorial on how to do get flexget working with deluged, but it was about 20 steps and it wanted me to do all sorts of crap like adding daemons to /etc/ini.d which is way way way way more involved that I want it to be. An RSS url, a regex and a download location, people.

2. qtorrent - This doesn't work at all. I added the url for my feed but qtorrent doesn't do anything. It just shows nothing. I know my RSS url is correct because wget gets it fine.

3. utorrent under wine - Does not work. I get all sorts of UI errors. It will list the torrents, but all of them 404 when trying to download. I tried grabbing a few of the torrent urls via wget and they all download fine.

4. I also tried out a older version of utorent - Does not work either. When I run the program, it wants to install to program files. I let it install, but when I navigate to my program files folder and run the program  the installer runs again Great. Must be a wine problem.

I haven't tried vuze yet, but unless someone can tell me that they have it 100% working, I'm not going to waste any more time with it until the next cycle of me trying to get automatic RSS torrent download working...

---

### Post by theshrike on 2010-06-04
> **nbv4 said:**
> This is something that *should* be easy. This is what I want to do:

1. I give an RSS url, a reges, and a download location to a torrent client.
2. The client then automatically refreshes that feed url every X minutes, and once a item shows up in the feed that matches my regex, it downloads it to a folder I specified.

1. Deluged - apprently older versions had a flexget plugin, but the latest version of deluged (the version that comes with lucid) does it completely different. Apparently you have to use this thing called "FlexGet", which is about the polar opposite of easy to use. 

Deluge's old ["FlexRSS" plugin]("http://dev.deluge-torrent.org/wiki/Plugins/FlexRSS") and [FlexGet]("http://flexget.com/") don't have anything to do with each other. FlexGet is a standalone program that downloads anything you tell it to.

> **nbv4 said:**
> I can't tell if you're supposed to install a deluged plugin for flexget, or a flexget plugin for deluged. Or no plug in at all.

You're supposed to use FlexGet's Deluge plugin, or if you don't want to, you can just have it download files to a directory.

> **nbv4 said:**
> Flexget has a yaml config system which is way more complicated than it needs to be. All I have an RSS url, a regex, and a download location. What else do you want?

```
feeds:
  myfeed:
    rss: http://example.com/feed.rss:
    regexp:
      accept:
        - hello.rss.world
    download: /home/user/downloads/

OR

    deluge: yes
```
   
The *feeds *section defines the sources, *myfeed *is the name you want to give the feed. The feed has 3 plugins: *rss*, which is the source, *regexp*, which handles filtering and *download*, which handles downloading. Or you can use the deluge plugin and feed torrents directly to deluged without watch directories.

Not that complex really.

> **nbv4 said:**
> I also tried a tutorial on how to do get flexget working with deluged, but it was about 20 steps and it wanted me to do all sorts of crap like adding daemons to /etc/ini.d which is way way way way more involved that I want it to be. An RSS url, a regex and a download location, people.

[This tutorial on the Deluge forums]("http://forum.deluge-torrent.org/viewtopic.php?f=9&t=18865&start=0") has 3 steps. (4 if you don't have deluge installed.)

1) install Deluge 2) install FlexGet 3) write config for FlexGet 4) put FlexGet in crontab.

#deluge@Freenode and #FlexGet@Freenode are good sources if you want real time support.

---

### Post by rampageoberon on 2010-11-01
Hello, you could try use rtorrent with [http://rampage.homelinux.com/scripts/rss-tor-dl.html](http://rampage.homelinux.com/scripts/rss-tor-dl.html)

Have rtorrent watching a folder for new torrents which works well for me.

---

