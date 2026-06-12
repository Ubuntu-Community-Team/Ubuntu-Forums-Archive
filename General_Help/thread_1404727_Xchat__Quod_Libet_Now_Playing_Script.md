---
title: "Xchat / Quod Libet Now Playing Script"
date: 2010-02-11
forum: General Help
---

### Post by WhiteRabbit101 on 2010-02-11
Firstly, hello, this is my first post on the forums. I've used Ubuntu alot, (right now i use mint) and I've used the forums alot in the past for finding solutions to problems.

If your anything like me you use IRC ALOT! 

But if your also like me you prefer using the QuodLibet music player, now I searched about for a now playing script for xchat for this player and couldn't find one so I decided to code my own. Just stick this into your /home/<name>/.xchat2/ directory under now_playing.py or something like that and when your in chatting just type "/np" and it will tell your friends what your listening to.

```

#!/usr/bin/python

import os
import xchat

__module_name__ = 'NowPlaying'
__module_description__ = '/me the Now Playing Track'

#WR101's Now Playing Script for Quod Libet

def play(word, word_eol, userdata):
    np = os.popen('quodlibet --print-playing')
    song = np.readline()
    song1 = song.rstrip('\n')
    xchat.command('ME is listening to >> '+song1)
    return xchat.EAT_ALL

xchat.hook_command('NP', play)

```Criticism / feedback is welcome.

---

### Post by abdusamed on 2010-08-23
nice..doesn't seem to work with rhythm box

---

