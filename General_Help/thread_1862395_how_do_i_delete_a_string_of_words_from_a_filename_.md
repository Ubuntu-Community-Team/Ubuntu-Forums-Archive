---
title: "how do i delete a string of words from a filename (in batches too)"
date: 2011-10-16
forum: General Help
---

### Post by bigdee973 on 2011-10-16
i got a bunch of files that have YOU_POOP in them. (e.g. cool_song_YOU_POOP.mp3 etc) i wanna batch delete that string.... how can i do that via terminal?  Also since im at it...how do i add, iterate (e.g. (cool_song(1).mp3), (cool_song(2).mp3) etc) strings etc.

---

### Post by gsmanners on 2011-10-16
In a terminal, you would use rename, so:

```
rename 's/YOU_POOP//' *
```

Should do the trick. Not sure how to iterate, though.

---

