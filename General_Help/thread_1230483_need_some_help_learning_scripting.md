---
title: "need some help learning scripting"
date: 2009-08-03
forum: General Help
---

### Post by BufordPants on 2009-08-03
I want to develop a bash procedure called createTestMP3Files() that creates a subdirectory named TESTMP3 in the current working directory, and populates it with about a 100 dummy MP3 files.

This creates one dummy mp3 file.

createOneDummyMP3File()
{
  echo > $1.mp3
  id3tool $1.mp3 -a $2 -r $3 -y $4
}

Any help would be greatly appreciated!

---

### Post by credobyte on 2009-08-03
Might be a little bit offtopic, but all programming/scripting questions should be asked in [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") section.

---

