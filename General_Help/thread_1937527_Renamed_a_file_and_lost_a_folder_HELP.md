---
title: "Renamed a file and lost a folder HELP"
date: 2012-03-08
forum: General Help
---

### Post by anticommander on 2012-03-08
I was in the process of moving a movie from one directory to another, I messed up the mv command and ended up moving the file to the directory above my intended directory and renamed the movie to the name of my target directory.

Basically I the movie is now named "Movies" and my "Movies" folder is now gone.

I'm hoping that it did not overwrite the directory and that I am still able to recover it.

Any suggestions?

Thanks!

---

### Post by jerome1232 on 2012-03-08
When you make a folder the target of a mv command, the file should be copied into the folder, it won't overwrite said folder.
what does this command yield?
```

ls -ld ~/Movies
```

---

### Post by anticommander on 2012-03-08
I ended up using locate to find my Movies directory. Somehow it got moved into another directory with my mv command, i have no idea how


Thanks for you help!

---

