---
title: "compiling conky w/ audacious support"
date: 2010-08-29
forum: General Help
---

### Post by crownedzero on 2010-08-29
Not really sure where this should be posted so I'll try kicking around here. I'm trying to compile conky 1.8 with audacious 2.3 support. I've come across the following error
```
conky-audacious.o: In function `audacious_thread_func':
audacious.c:(.text+0x354): undefined reference to `audacious_remote_is_running'
audacious.c:(.text+0x3a2): undefined reference to `audacious_remote_is_paused'
audacious.c:(.text+0x3d1): undefined reference to `audacious_remote_is_playing'
audacious.c:(.text+0x41e): undefined reference to `audacious_remote_get_playlist_pos'
audacious.c:(.text+0x433): undefined reference to `audacious_remote_get_playlist_title'
audacious.c:(.text+0x47c): undefined reference to `audacious_remote_get_playlist_time'
audacious.c:(.text+0x540): undefined reference to `audacious_remote_get_output_time'
audacious.c:(.text+0x619): undefined reference to `audacious_remote_get_info'
audacious.c:(.text+0x69a): undefined reference to `audacious_remote_get_playlist_file'
audacious.c:(.text+0x6dc): undefined reference to `audacious_remote_get_playlist_length'
audacious.c:(.text+0x737): undefined reference to `audacious_remote_get_main_volume'
collect2: ld returned 1 exit status
make[2]: *** [conky] Error 1
make[2]: Leaving directory `/home/crownedzero/Downloads/conky-1.8.0/src'
make[1]: *** [all] Error 2

```
I've tried to do some research and I'm coming up with very little information. Here are the sites I have found pertaining to this issue:
[http://bugs.gentoo.org/313161](http://bugs.gentoo.org/313161)
[http://forums.freebsd.org/showthread.php?t=14795](http://forums.freebsd.org/showthread.php?t=14795)
and possibly [http://sourceforge.net/tracker/?func=detail&aid=2933738&group_id=143975&atid=757308](http://sourceforge.net/tracker/?func=detail&aid=2933738&group_id=143975&atid=757308)

Can anyone help me get this thing figured out?

---

