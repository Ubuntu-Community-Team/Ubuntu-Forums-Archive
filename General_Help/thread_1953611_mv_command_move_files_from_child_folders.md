---
title: "mv command: move files from child folders"
date: 2012-04-06
forum: General Help
---

### Post by Shannondorf on 2012-04-06
Hi everyone,

      So I have many mp3 files sorted this way:

/Folder1/song1.mp3
/Folder1/Folder2/song2.mp3
/Folder1/Folder2/Folder3/song3.mp3

etc.

I want to move them in one folder, but to do so I have to type many commands like this:

```
mv */*.mp3 .
mv */*/*.mp3 .
mv */*/*/*.mp3 .

etc.
```

Being an engineer, I am naturally lazy ( ;) ) and I want to do everything in one command. Is that possible?

---

### Post by brainwash on 2012-04-06
Something along these lines should work:
```
find . -name "*.mp3" -type f -exec mv {} . \;
```

---

### Post by codemaniac on 2012-04-06
locate with xargs , some unorthodox finding
```
locate *.mp3 | xargs -I {} mv {} ~/OneFolder
```

---

### Post by Shannondorf on 2012-04-06
Thanks to both of you for your replies, I completely forgot about the "find" command. I used brainwash's command and it worked like a charm.

---

