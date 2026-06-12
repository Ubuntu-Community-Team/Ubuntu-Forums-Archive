---
title: "rTorrent putting %2F instead of /"
date: 2012-03-15
forum: General Help
---

### Post by Sab3r on 2012-03-15
I know this isn't a rTorrent support forum, but since that forum doesn't exist and alot of people here are probably using rTorrent anyway...

I use a headless uTorrent/file server running 64-bit Ubuntu Server, with rTorrent 0.9.0, libTorrent 0.13.0 and ruTorrent 3.3. I've got it set so that it watches certain directories for .torrent files, downloads the torrents to a temporary directory and when it finishes, moves the downloaded files to a directory set by which watch directory the .torrent file was put in originally (hope that makes sense). This is achieved by using 'schedule' and 'system.method.set_key' rules in .rtorrent.rc. It stores the final location for the files in a 'custom1' tag, see this _[example]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrentstodifferentdirectorydependingonwatchdirectory")_.

Recently however, only sometimes it puts '%2F' in the 'custom1' tags instead the regular forward slash '/'. This causes the files to be moved to a directory named after the whole tag, including the %2F's, in the users home directory, which is even on a different drive. :eek: It also causes rTorrent to report an error when it finishes the torrent. 

This has probably something to do with Linux and Windows differences in character sets and encodings, but does anyone know how I could prevent this from happening? 
("Stop using Windows" is not a useful solution) 

Thanks.

---

### Post by pyroscope on 2012-03-19
ruTorrent uses the NUMBERED custom fields for its own purposes, so use a NAMED custom for anything you do in rT proper, to avoid clashes. Also the numbered fields are legacy and should be avoided anyway.

---

