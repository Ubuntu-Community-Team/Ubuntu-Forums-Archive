---
title: "Sound stops, suddenly"
date: 2006-02-12
forum: General Help
---

### Post by Minilek on 2006-02-12
I've been using Ubuntu without any problems for some time now, but my sound suddenly completely stopped working today.  I was listening to a song using mplayer.  Halfway through the song, I quit playing it then rm'd the file.  I immediately then tried playing another song using mplayer but noticed that there was no sound.  Ever since then, I haven't been able to get sound out my sound card at all, using any application.  Rebooting has not helped.

Is there perhaps a lock file or something somewhere that needs to be removed?  My sound card is still intact, as things play fine in Windows.  I imagine it's not a driver problem either since the sound was working just fine up until this incident.  Help would be appreciated.

minilek@MINILEK:~$ lspci
...
0000:05:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
...

---

### Post by Minilek on 2006-02-12
Apparently "PCM2" got turned down all the way somehow, which doesn't show in alsamixer.  I had to get aumix and change it that way, in case anyone else runs into this.

---

