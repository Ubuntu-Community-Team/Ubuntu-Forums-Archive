---
title: "some mplayer questions"
date: 2006-06-10
forum: General Help
---

### Post by circ on 2006-06-10
i've played around with the mplayer config file a bit, but can't figure out how to make it repeat a playlist. is there an option for this?

and also speaking of playlists, how do you save one in mplayer? or do i make a textfile and save it with a certain extension with links to the playlist items inside?

---

### Post by hopstah on 2006-06-20
i haven't been able to find out how to do this either, and i would love to.  i see this as a staple of a media player, and it's a pretty significant shortcoming of mplayer considering how mature the project is as a whole.

---

### Post by bforbes on 2006-06-20
Make a file with one playlist item per line. You can give it any name you want. Then:
```

mplayer -playlist filename

```

If you aren't a command-line person, you could create a file association for an extension of your choosing, eg .pls. The command would be "mplayer -playlist "

I don't know how to make it repeat, I too think that would be a good feature.

EDIT: You can pass "-loop N " as a command-line argument to make the playlist/file repeat N times. Just set N quite high, that should work fine.

---

### Post by starkes on 2006-06-20
-loop 0 will repeat forever

---

