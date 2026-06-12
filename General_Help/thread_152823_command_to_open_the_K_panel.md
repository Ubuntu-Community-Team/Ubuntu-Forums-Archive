---
title: "command to open the K panel?"
date: 2006-03-30
forum: General Help
---

### Post by munchies on 2006-03-30
I am trying to bind my windows key to open the K panel and I am trying to use xbindkeys but in order for it to work I need to know the command that you would type in a terminal to open the K panel.

---

### Post by localzuk on 2006-03-30
I went through the same process. Take a look at: [http://ubuntuforums.org/showthread.php?t=102509](http://ubuntuforums.org/showthread.php?t=102509)

It describes briefly what I did, and provides a link to: 
[http://www.kde-forum.org/thread.php?threadid=11451](http://www.kde-forum.org/thread.php?threadid=11451)
which provides information on the specifics.

I should really create a howto for it...

---

### Post by binarysleeper on 2006-04-01
[quote=munchies]I am trying to bind my windows key to open the K panel and I am trying to use xbindkeys but in order for it to work I need to know the command that you would type in a terminal to open the K panel.[/quote]
Use:
```

dcop kicker kicker showKMenu
```

The only caveat being that if you try other key mapping combos with the Win key it will trigger the Kmenu as well. Will post again if I find a workaround.

---

