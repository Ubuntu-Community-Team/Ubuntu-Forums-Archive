---
title: "ac3 sound problems"
date: 2006-01-23
forum: General Help
---

### Post by t0bb3 on 2006-01-23
I'm trying to watch an xvid encoded movie with ac3 sound.
mplayer/gmplayer gives me this error: MPlayer interrupted by signal 11 in module: decode_audio
More details here: [https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/508](https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/508) I have the exact same errors as that guy. Maybe that bug should be reopened?

I also tried xine-ui but with no luck. The movie started playing, but with no sound. Couldn't see any error messages though.

I then found an old post here on the forums that suggested trying this:> gmplayer -ao alsa1x -ac hwac3 -af-adv force=3
That line worked great for this ac3 movie, but when I started gmplayer with those options and tried to watch a movie without ac3 sound I got an error "Cannot find codec for audio format 0x55". The movie then plays, but with no sound.

I would prefer using xine, since mplayer doesn't support DVD menus.

And I need something that allways works without changing command line parameters because I'll be launching the movie from within MythTV.

Ideal would be a script or something that first tried the "gmplayer -ao alsa1x -ac hwac3 -af-adv force=3" equivalent for xine, and then if that gives an error falls back on normal sound. Is that possible? Or is there some other, easier, way?

Thanks
//t0bb3

---

### Post by t0bb3 on 2006-01-24
Setting the audio.output.speaker_arrangement:Pass Through option in .xine/config seems to work both for ac3 and non ac3 audio :)

---

