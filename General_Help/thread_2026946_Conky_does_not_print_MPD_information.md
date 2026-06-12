---
title: "Conky does not print MPD information"
date: 2012-07-16
forum: General Help
---

### Post by jenic on 2012-07-16
*[SIZE=1]I wasn't sure if this was "Audio & Multimedia" enough to post there so I am asking here instead. Apologies if this is incorrect.[/SIZE]*

My problem is that conky will not display the information it receives from Music Player Daemon. I know the server is functioning as ncmpcpp, mpc, telnet, and netcat can all reach it and run commands against it without issue. I know conky is at least attempting communication with MPD as I can see them talking on lo interface via tcpdump. Here are the basic facts of my issue and environment:


[LIST]
[*]I am running MPD locally. (not via service/init.d) It is executed by slim via my .xinitrc
[*]I am running conky-cli package, version 1.8.0 on Ubuntu 10.04.4 (conky-std refuses to print to stdout despite repeated attempts; but that's another story)
[*]MPD is definitely running and responding fine to a multitude of other applications
[*]I have tried both with and without setting MPD_* env variables
[*]I can see two-way traffic between conky and MPD over port 6600 and I have attached the packet capture to this post.
[/LIST]
Here is a lsb_release -a:
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

```Here is the output I receive from conky:
```

jenic@Dracarys ~ %conky -DDDc .conkt
DEBUG(1) [../../src/core.c:1217]: no templates to replace
(null) [0%]  UTC 2012-07-16 06:17:45

```Here is the .conkt config file:

```

out_to_console yes
background no
total_run_times 1
no_buffers yes
uppercase no
mpd_host localhost
mpd_port 6600

TEXT
$mpd_status$mpd_smart [${mpd_percent}%]  UTC $utime

```I have also tried this:
```
$mpd_artist [${mpd_percent}%]  UTC $utime
```Here is a conky -v and mpd --version:
```

Conky 1.8.0 compiled Fri Apr 23 10:41:59 UTC 2010 for Linux 2.6.24-27-server (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky


 Music detection:
  * MPD
  * MOC

 General:
  * math
  * config-output
  * apcupsd
  * iostats
  * ncurses

``````

mpd (MPD: Music Player Daemon) 0.15.4

```And here is MPD config (with comments removed):
```

music_directory        "/home/jenic/Music"
playlist_directory        "/home/jenic/.mpd/playlists"
db_file            "/home/jenic/.mpd/mpd.db"
log_file            "/home/jenic/.mpd/mpd.log"
pid_file            "/home/jenic/.mpd/mpd.pid"
state_file            "/home/jenic/.mpd/mpdstate"
bind_to_address        "localhost"
metadata_to_use    "artist,album,title,track,name,genre,date,composer,performer,disc,comment"
input {
        plugin "curl"
}
audio_output {
    type        "pulse"
    name        "MPD"
}
max_connections        "5"
filesystem_charset        "UTF-8"
id3v1_encoding            "UTF-8"

```Has anyone else had this problem? Were you able to fix it? I'm trying to avoid anything major like recompiling conky. Right now I am using conky's exec tag to call mpc. This workaround works but I'd rather use pure conky mainly for the "mpd_smart" tag but also so I can remove mpc. (I additionally don't like seeing my netstat full of time_wait connections between mpc and mpd but that is just a pet peeve of mine)

Please let me know if I've forgotten to include any information.

---

