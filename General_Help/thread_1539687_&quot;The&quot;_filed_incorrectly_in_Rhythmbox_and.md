---
title: "&quot;The&quot; filed incorrectly in Rhythmbox and Banshee"
date: 2010-07-26
forum: General Help
---

### Post by lalilulelo on 2010-07-26
This is kind of a minor complaint, but nonetheless a problem that I'd like to see resolved. In Rhythmbox and Banshee, artist names that begin with the word "the" are filed under "T" instead of whatever letter comes after that. I'm used to using iTunes, which simply ignores the word "the" and files an artist name according to whatever letters come after "the". For example, songs by the artist named "The Beatles" are filed under "T" in both Rhythmbox and Banshee, whereas in iTunes they're filed under "B". Is there any way to change this?

---

### Post by flick on 2010-07-26
Looks like a bug has been filed, and a fix may be on the way :

[https://bugs.launchpad.net/rhythmbox/+bug/27664](https://bugs.launchpad.net/rhythmbox/+bug/27664)

---

### Post by lalilulelo on 2010-07-27
That problem is listed as a bug, though I think its really more of just a complaint. Regardless of whether they're going to fix this for Rhythmbox or not, I'd really like it to be fixed in Banshee as I think this is the main program I'll be using (because of its iPod syncing ability). Any ideas? Perhaps there's a workaround of some type?

---

### Post by AlphaLexman on 2010-07-27
I think the real problem is an 'id3' issue. Artist="The Beatles" should be saved as; Artist="Beatles, The"
But in linux, filenames with a comma are problematic. Catch_22.

---

