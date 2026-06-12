---
title: "Add File Extensions script help"
date: 2012-04-03
forum: General Help
---

### Post by Thrashrokz33 on 2012-04-03
Hello, I've run into a problem transferring my music over from a external drive. It seems like all the .mp3 extensions on my music files have decided to disappear. After a few searches, I found a command that worked for re-adding the .mp3 extension to all files inside a single folder:

rename 's/$/.mp3/' *

This works when I'm actually inside the folder with a series of music files. I want to apply this command to all folders in my music directory, though. What would I have to add to this command to do that?

Something like: (I don't know the syntax)

for folder in /music
    rename 's/$/.mp3/' *
done

(add extension to all files in that folder, move to the next folder)

---

### Post by papibe on 2012-04-03
Hi Thrashrokz33.

You can use the command 'find' so that every time it finds a file it would change its name:
```
find -type f -exec rename 's/$/.mp3/' '{}' \;
```
where
[INDENT]'-type f' will only match files.
'-exec ...' execute the following command every time 'find' finds a file.
'{}' makes reference to file just found.
[/INDENT]
I hope that helps, and tell us how it goes.
Regards.

---

### Post by Thrashrokz33 on 2012-04-03
Thanks! That worked flawlessly. It all imported into Banshee perfectly.

You're the man.

---

### Post by papibe on 2012-04-03
:D great! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

