---
title: "unable to play embed wav files in 10.04"
date: 2010-05-10
forum: General Help
---

### Post by sir_nasty on 2010-05-10
so here's what I"m trying to use.  I click on the play button and nothing happens

```

<embed src="done/VM161650.WAV" width="200" height="20" autoplay="false" controller="true"></embed> 

```

Any Ideas?  It just switches to the pause option and nothing happens.  Sound Manager doesn't even show a sound device active.  I can download and play the file without issue.  It occurs in both Chrome and Firefox.

---

### Post by sir_nasty on 2010-05-12
This issue didn't occur in Ubuntu 9.10.  Anyone seen a bug on this or a related issue?  Also, my sound volume is incredibly low even when it does play and I haven't been able to resolve that either... any ideas?

---

### Post by sir_nasty on 2010-05-12
If anyone stumbles across this and can't seem to get multimedia files like wav, mp4 etc to play in firefox or chrome I got it fixed by installing mozilla-plugin-vlc and gecko-mediaplayer packages.  YOu can get them from package manager or go to terminal and 

```

sudo apt-get install mozilla-plugin-vlc
sudo apt-get install gecko-mediaplayer

```

---

