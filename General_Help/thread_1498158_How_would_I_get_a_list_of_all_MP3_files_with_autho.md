---
title: "How would I get a list of all MP3 files with authors?"
date: 2010-05-31
forum: General Help
---

### Post by anthony62490 on 2010-05-31
I have scoured the 'ls' man page, but I don't think it has the capability to do this. Specifically, I would like a command/program that will output a list of all of the files in "/home/anthony/Music/" in the following format:

> artist1 - file1.mp3
artist2 - file2.mp3
artist3 - file3.ogg
artist4 - file4.flac

Any ideas? To be honest, I really only need the artist and the song title. If it can't be formatted exactly like that, then it's not the end of the world.

---

### Post by StuartN on 2010-05-31
> **anthony62490 said:**
> a command/program that will output a list of all of the files in "/home/anthony/Music/"

From the command line you could try eyed3, id3v2, id3tool or similar and pipe the output through sed to tidy it up. None of them seem to produce clean, consistent output though, and none seem to have a good printf type switch that works across v1 / v2 / v3 tagged files.

Applications like EasyTag, Picard or Musicbraiz might suit. Perhaps one can dump the database to text for you.

---

