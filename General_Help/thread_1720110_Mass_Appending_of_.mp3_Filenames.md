---
title: "Mass Appending of .mp3 Filenames"
date: 2011-04-02
forum: General Help
---

### Post by BagelKing on 2011-04-02
In my music library, there are mysteriously many files that Ubuntu recognizes as .mp3's but are not actually named as such; they are just files with no extensions. Hitherto, this has been absolutely fine, because Rhythmbox has been intuitive enough to recognize them and import them. I've recently been annoyed by Rhythmbox for other reasons, however, and, upon hearing that Banshee is going to be the default media player in Ubuntu 11, decided to switch. The trouble is that Banshee is *not* so intuitive as to import the extensionless files, which are numerous in quantity. It could take quite a long while to rename each individual track. I have a hunch that Ubuntu provides some method whereby to add ".mp3" to the ends of these files' names in bulk. Could someone apprise me of this method?

Love and thanks.

Ubuntu Version: 10.10

---

### Post by doorknob60 on 2011-04-02
If all the files are in the same directory, you could do something like this:
```
for i in *;do mv $i $i.mp3;done
```

Not sure how to make it do it recursively throughtout multiple directories though...

---

### Post by BagelKing on 2011-04-02
I'm happy to go directory-by-directory, I think. I'm going to go ahead with that approach, but if anyone finds a way to accomplish a multi-directory approach, it could be useful for readers of the future.

Thank you, friend

---

### Post by BagelKing on 2011-04-02
That almost worked, except that it seems to only rename directories, which I would rather like to remain the same.

"mv: example is not a directory."

---

### Post by Vaphell on 2011-04-03
that **for ...** fails with names with spaces, $something needs to be put in " " to prevent incorrect parsing

for recursive solution try
```
find . ! -iname '*.mp3' -type f -exec **echo** "{}" "{}.mp3"  \;
```
in current form command merely prints out old_name new_name
if you are happy replace echo with mv to rename

test it first on some small set of dummy data, recursive commands are a pain to clean up if something goes wrong :) also this command looks only for .mp3 so if you have some .txt or .jpg files there, they will get caught by the command too.

in such case something like this should do:
```
find . ! \( -iname '*.mp3' -o -iname '*.txt' \) -type f -exec echo "{}" "{}.mp3"  \;
```

parentheses hold extensions to exclude
! = not, -o = OR
so command means find stuff that is NOT( .mp3 OR .txt )

---

