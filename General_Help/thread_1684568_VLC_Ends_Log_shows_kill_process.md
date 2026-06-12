---
title: "VLC Ends Log shows kill process"
date: 2011-02-09
forum: General Help
---

### Post by gmgj on 2011-02-09
My swag is that my VLC has a memory leak and that is why it keeps dying on my system while playing audio .m3u Playlists of flac files

VLC 1.1.4 Jan 25 2011, ubuntu 10.10, Dell Lattitude laptop D600


This is what I see in the syslog

Feb  9 09:24:12 ubugj-DellD600 kernel: [ 4995.881387] Out of memory: kill process 2353 (vlc) score 239282 or a child
Feb  9 09:24:12 ubugj-DellD600 kernel: [ 4995.881401] Killed process 2353 (vlc) vsz:1914260kB, anon-rss:385568kB, file-rss:0kB
Feb  9 09:56:10 ubugj-DellD600 init: tty1 main process (1189) killed by INT signal

Or might it be some other process?


I recently enabled open office quickstarter and I use Firefox and gedit; however, my observations are, the other applications do not die and VLC can die when that is the only "active" application.   

BTW My life is easier after reassigning Ctrl - Alt - Del from logout/shutdown to gnome-system-monitor.

---

### Post by gmgj on 2011-02-09
Sent to 
[https://bugtrack.alsa-project.org/alsa-bug/](https://bugtrack.alsa-project.org/alsa-bug/)


maybe, just maybe, this has some bearing on my problem

Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 353060 bytes (2001 ms).
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: snd_pcm_dump():
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: Hardware PCM card 0 'Intel 82801DB-ICH4' device 0 subdevice 0


VLC running along fine at around 50% of memory.  Start Firefox, still running fine, start GEDIT, opps geting flaky, starting "Places" - computer
hang, disk light goes on and stays on

More of the log for context
Feb  9 11:23:33 ubugj-DellD600 wpa_supplicant[1014]: WPA: Key negotiation completed with 00:1a:70:52:54:7a [PTK=CCMP GTK=CCMP]
Feb  9 11:23:33 ubugj-DellD600 NetworkManager[767]: <info> (eth1): supplicant connection state:  group handshake -> completed
Feb  9 11:23:33 ubugj-DellD600 wpa_supplicant[1014]: CTRL-EVENT-CONNECTED - Connection to 00:1a:70:52:54:7a completed (reauth) [id=0 id_str=]
Feb  9 11:23:42 ubugj-DellD600 wpa_supplicant[1014]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Feb  9 11:23:42 ubugj-DellD600 NetworkManager[767]: <info> (eth1): supplicant connection state:  completed -> disconnected
Feb  9 11:23:42 ubugj-DellD600 NetworkManager[767]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Feb  9 11:23:42 ubugj-DellD600 wpa_supplicant[1014]: Trying to associate with 00:1a:70:52:54:7a (SSID='Bullwinkle' freq=2437 MHz)
Feb  9 11:23:42 ubugj-DellD600 NetworkManager[767]: <info> (eth1): supplicant connection state:  scanning -> associating
Feb  9 11:23:42 ubugj-DellD600 wpa_supplicant[1014]: Associated with 00:1a:70:52:54:7a
Feb  9 11:23:42 ubugj-DellD600 NetworkManager[767]: <info> (eth1): supplicant connection state:  associating -> associated
Feb  9 11:23:42 ubugj-DellD600 NetworkManager[767]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Feb  9 11:23:42 ubugj-DellD600 wpa_supplicant[1014]: WPA: Key negotiation completed with 00:1a:70:52:54:7a [PTK=CCMP GTK=CCMP]
Feb  9 11:23:42 ubugj-DellD600 wpa_supplicant[1014]: CTRL-EVENT-CONNECTED - Connection to 00:1a:70:52:54:7a completed (reauth) [id=0 id_str=]
Feb  9 11:23:42 ubugj-DellD600 NetworkManager[767]: <info> (eth1): supplicant connection state:  4-way handshake -> group handshake
Feb  9 11:23:42 ubugj-DellD600 NetworkManager[767]: <info> (eth1): supplicant connection state:  group handshake -> completed
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 353060 bytes (2001 ms).
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: snd_pcm_dump():
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: Hardware PCM card 0 'Intel 82801DB-ICH4' device 0 subdevice 0
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c: Its setup is:
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   stream       : PLAYBACK
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   format       : S16_LE
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   subformat    : STD
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   channels     : 2
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   rate         : 44100
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   msbits       : 16
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   buffer_size  : 16384
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   period_size  : 16384
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   period_time  : 371519
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   tstamp_mode  : ENABLE
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   period_step  : 1
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   avail_min    : 16384
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   period_event : 0
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   start_threshold  : -1
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   stop_threshold   : 1073741824
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   silence_threshold: 0
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   silence_size : 0
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   boundary     : 1073741824
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   appl_ptr     : 232289594
Feb  9 11:37:21 ubugj-DellD600 pulseaudio[1461]: alsa-util.c:   hw_ptr       : 232361475
Feb  9 11:49:13 ubugj-DellD600 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb  9 11:49:13 ubugj-DellD600 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="807" x-info="http://www.rsyslog.com"] (re)start
Feb  9 11:49:13 ubugj-DellD600 rsyslogd: rsyslogd's groupid changed to 102
Feb  9 11:49:13 ubugj-DellD600 rsyslogd: rsyslogd's userid changed to 101
Feb  9 11:49:13 ubugj-DellD600 rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Feb  9 11:49:13 ubugj-DellD600 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  9 11:49:13 ubugj-DellD600 kernel: [    0.000000] Initializing cgroup subsys cpu

---

### Post by gmgj on 2011-02-12
I am unable to reproduce this problem with either the Gnome Mplayer or rhythmbox.

---

### Post by gmgj on 2011-02-12
Opps , wrong, its just harder in rhythmbox


Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: -765352 bytes (-4338 ms).
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c: snd_pcm_dump():
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c: Hardware PCM card 0 'Intel 82801DB-ICH4' device 0 subdevice 0
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c: Its setup is:
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   stream       : PLAYBACK
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   format       : S16_LE
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   subformat    : STD
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   channels     : 2
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   rate         : 44100
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   msbits       : 16
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   buffer_size  : 16384
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   period_size  : 16384
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   period_time  : 371519
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   tstamp_mode  : ENABLE
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   period_step  : 1
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   avail_min    : 16384
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   period_event : 0
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   start_threshold  : -1
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   stop_threshold   : 1073741824
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   silence_threshold: 0
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   silence_size : 0
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   boundary     : 1073741824
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   appl_ptr     : 19815701
Feb 12 10:26:27 ubugj-DellD600 pulseaudio[1507]: alsa-util.c:   hw_ptr       : 20023423

---

