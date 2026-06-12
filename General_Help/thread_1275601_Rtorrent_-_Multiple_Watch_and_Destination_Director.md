---
title: "Rtorrent - Multiple Watch and Destination Directories"
date: 2009-09-26
forum: General Help
---

### Post by jseiser on 2009-09-26
I am using rtorrent 8.5 and I want to have multiple watch and destination directories.

When I launch rtorrent, It loads but I receive this error.

```

(11:32:48) Deprecated on_* commands, use 'system.method.set_key = event.download.{inserted, erased, ...}, <key>, <command>' instead.

```

The relevant portion of my config is here.

```

###########CUSTOM
###### MOVE DIRECTORY

schedule = watch_directory_1,10,10,"load_start=/home/justin/media/torrents/music/*.torrent,d.set_custom1=/home/justin/media/music/"
schedule = watch_directory_2,10,10,"load_start=/home/justin/media/torrents/movie/*.torrent,d.set_custom1=/home/justin/media/movie/"
schedule = watch_directory_3,10,10,"load_start=/home/justin/media/torrents/misc/*.torrent,d.set_custom1=/home/justin/media/misc/"

# On completion, move the torrent to the directory from custom1.

on_finished = move_complete,"d.set_directory=$d.get_custom1= ;execute=mv,-u,$d.get_base_path=,$d.get_custom1="

####END CUSTOM
#######

```

The directories I am referencing exist as well.

```

[justin@beast ~]$ cd media/
[justin@beast media]$ ls
misc  movie  music  torrents
[justin@beast media]$ cd torrents/
[justin@beast torrents]$ ls
misc  movie  music
[justin@beast torrents]$

```

The watch directories all work.  The first directory works as intended ( The music one), the other two do not get moved to the folder, they download and sit in my home folder.  Any ideas would be great. Thanks.

---

### Post by jseiser on 2009-09-26
If anyone had any sort of ideas on this it would be great.

---

### Post by Quentusrex on 2011-01-10
Just so you know, the problem is the setting is not 'set_d_directory' it should be 'd.set_directory'. If you were to make that one change it should work for you.

---

