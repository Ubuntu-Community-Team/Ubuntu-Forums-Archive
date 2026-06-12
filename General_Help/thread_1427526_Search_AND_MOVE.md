---
title: "Search AND MOVE"
date: 2010-03-11
forum: General Help
---

### Post by djbushido on 2010-03-11
So i've found that I can easily search for mp3 files in a given directory. What I would like to do next is to move all of those files in to another directory. Is there a way to do that?

---

### Post by djbushido on 2010-03-11
#nevermind, drag and drop seems to work fine.

EDIT: Just kidding, that doesn't work so well. Any ideas? I looked into the "find" command, put I'm not sure how to move a file after I know what its location is....

---

### Post by kaibob on 2010-03-11
> **djbushido said:**
> So i've found that I can easily search for mp3 files in a given directory. What I would like to do next is to move all of those files in to another directory. Is there a way to do that?


If all of the files are in one directory, you can just use the move command:

```
mv /source/directory/*.mp3 /target/directory
```

If you want to move files recursively, then the find command is best:

```
find /source/directory -name '*.mp3' -type f -exec mv '{}' /target/directory ';'
```

---

### Post by djbushido on 2010-03-11
Yeah, I actually discovered how to REALLY use find while you were posting. I actually did it with cp, but same difference. I appreciate the help.

---

### Post by audiomick on 2010-03-11
You might find a pipe useful. Should let you find and move in one go, I think.
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)
there is a mention of it right down the bottom of that.

---

### Post by djbushido on 2010-03-11
Yeah, a pipe will work too, but sometimes it's just nice to do it all in one command.
No really "better" way though, as far as I know. Unless someone wants to time it.

---

