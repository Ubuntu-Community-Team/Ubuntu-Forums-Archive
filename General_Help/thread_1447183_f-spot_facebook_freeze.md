---
title: "f-spot facebook freeze"
date: 2010-04-05
forum: General Help
---

### Post by DexterLB on 2010-04-05
I installed Lucid beta-1 because I broke karmic with a fork bomb and didn't want to clean-install karmic again. And it's wonderful - boots sooooooo fast, has new versions of lots of packages in main. I saw that the facebook plugin for f-spot was also in main (included in f-spot actually) and I enabled it.

So it connects, authorizes, and freezes on the "Session established, fetching photo albums" stage. It has no CPU usage and isn't sending packets.

Has anyone else tried this and had the same problem?

---

### Post by DexterLB on 2010-04-07
bump

---

### Post by digitaleagle on 2010-04-24
I am in the same boat.  I have searched a while back, and didn't find anything helpful.  I am curious if any one has it working or has had it working for a long time.

Here is an old thread that looks like it never got answered:
[http://ubuntuforums.org/showthread.php?t=635385](http://ubuntuforums.org/showthread.php?t=635385)

Here is the last time I messed with it:
[http://linuxsagas.wordpress.com/2010/01/08/more-f-spotfacebook-troubleshooting/](http://linuxsagas.wordpress.com/2010/01/08/more-f-spotfacebook-troubleshooting/)

Here is my workaround:
[http://linuxsagas.wordpress.com/2010/01/15/workaround-for-posting-pictures-to-facebook/](http://linuxsagas.wordpress.com/2010/01/15/workaround-for-posting-pictures-to-facebook/)

---

### Post by DexterLB on 2010-04-25
The workaround isn't satisfying as I need to manually copy all captions, the java applet is buggy and the basic applet malfunctions too often :(

---

### Post by danopia on 2010-04-28
I've been playing with the git HEAD of F-Spot trying to see where this bug is coming from and it appears to be a bug in Mono.Facebook. The GetAlbums call is erroring with "Input string was not in the correct format: Did not parse entire string. pos = 15 s.Length = 18"

The fun part now is that to get any further I'd have to debug part of mono itself. I think I'm going to "neuter" the album listing so that F-Spot can only add new albums. At least that functionality would work.

[ EDIT ]
Haha. Mono.Facebook/ is right in the FacebookExport dir. Looks like Facebook changed something so it can't add pics either, so I'm going to have some fun with this tonight.

[ EDIT ]
Looks like I got it. Albums and Photos now have non-numeric IDs... mostly underscores but I saw a dash. I patched Mono.Facebook to use "string" instead of "long" and it seems like album listing and creation and photo uploading is fully operational. If I find no further issues, I plan to post a patch. (is there a bugtracker I should post this on? ubuntu, fspot, mono.facebook? I'm not sure which)

[ EDIT ]
I got it working with the git version of F-Spot, but when I try packaging up a version of the addin and putting it on a reop so others can just install it, it can't by default because the broken version is in /usr/lib, and then once that's sorted out the addin just doesn't want to work. It's probably due to me building it against the git F-Spot and using it against the apt-get one (ubuntu 9.10). I couldn't `make` the `apt-get source` version, which is why I couldn't build the fixed version against it.

(copied from another topic; I replied to the wrong one)

---

