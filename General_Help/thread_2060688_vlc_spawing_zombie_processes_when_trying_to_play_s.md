---
title: "vlc spawing zombie processes when trying to play some FLAC files from DLNA server"
date: 2012-09-20
forum: General Help
---

### Post by zloster12 on 2012-09-20
Hi,
I'm using Ubuntu 12.04 64-bit on a desktop machine and VLC 2.0.3. On my home network I have a minidlna server running on another machine. I've noticed that several particular flac files don't want to play and after each attempt to play them the VLC player finish with two (2) or three (3) zombie processes and skips them. Other flac files are played just fine.
[ATTACH]224430[/ATTACH]
Here is also the debug log from the vlc itself.
[ATTACH]224431[/ATTACH]
The only clue in the log is this:
```
main debug: `http://192.168.27.2:8200/MediaItems/38.flac' successfully opened
main debug: EOF reached
dbus debug: the main loop has been woken up
```But when I open the address of the file in a browser it is opened without a problem, saves completely  and plays nicely locally.
And now the strange thing: I also use a laptop with Ubuntu 12.04 64-bit and VLC 2.0.3. The same flac files from the same minidlna server are played without any problems.

Can anyone suggest what to do to be able to investigate this? Reinstall of the VLC does not help. I think that it could be some configuration settings somewhere.

Any suggestions will be helpful.

---

