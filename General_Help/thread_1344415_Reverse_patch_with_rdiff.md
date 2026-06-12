---
title: "Reverse patch with rdiff"
date: 2009-12-02
forum: General Help
---

### Post by silentrebel on 2009-12-02
I've been trying to make use of rdiff for backing up...

If I have origFile and modFile and if want to obtain a delta (patch to go from the former to the latter, the following lines do the trick:
```
rdiff signature origFile.txt signature.sig
rdiff delta signature.sig modFile delta.rdiff
rm -f signature.sig #not needed, but let's be tidy

```
So now, if I do:
```
rdiff patch origFile delta.rdiff modFile2

```
modFile and modFile2 should be identical.

Is there a rdiff command that, when run on modFile, will result in another file that is identical to origFile (reverse-patch)?

For those of you who know diff and patch, I'm looking for the equivalent of "patch -R."

---

### Post by silentrebel on 2009-12-03
Hasn't anyone ever used rdiff before?

[http://librsync.sourcefrog.net/doc/rdiff.html]("http://librsync.sourcefrog.net/doc/rdiff.html")
_____________________
I sent an email to the developers of rdiff concerning this question and they quite quickly replied:
They said that rdiff aims to create compact and optimal deltas--which implies that it will only include information in the second file that is not in the first file (not the other way around (diff does this because it stores exactly what has been removed as well (this way, when you want to reverse-patch, it adds what was removed and removes what was added))).
They suggested that if anyone wants rdiff's ability to create deltas between files that are too large to fit in memory (diff: memory exhausted) and the ability to patch and reverse-patch, one should just use rdiff to create deltas in both directions.  According to the developers, the combined size of these two rdiff deltas should be approximately the same as the size of diff's bidirectional patch.  
I hope this clears everything up.
silentrebel

---

