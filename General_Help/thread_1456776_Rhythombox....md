---
title: "Rhythombox..."
date: 2010-04-17
forum: General Help
---

### Post by Cubhicbu on 2010-04-17
I love Rhythombox. I wouldn't trade it for any other music player. But it keeps putting the songs under the wrong artist because one letter in the songs properties is different. Such as Starrstruk by 3Oh!3. I have all my other 3Oh!3's songs under the artist "3Oh!3" (set by Windows 7) and Starrstruk is set as "3OH!3". So now, there's two artists of 3Oh!3 (3Oh!3 and 3OH!3.)

In Windows, I right click the file, click "Properties", switch to "Details", and I can change the artist's name. How can I do this in Ubuntu?

---

### Post by Odd-rationale on 2010-04-17
You need a music tag editor. My personal favorite is called EasyTag.

You can find several others in the Software Center.

---

### Post by Eraemaajaervi on 2010-04-17
right click the entries in rhythmbox, click "Properties", change the artist's name and click ok.

use ctrl or shift to select multiple entries

---

### Post by Cubhicbu on 2010-04-17
When I change them in Rhythombox, they just change back when I reopen Rhythombox.

---

### Post by Eraemaajaervi on 2010-04-17
can't reproduce.
do you have writing permission to the files?
do the files even support ID-tags?

if you don't wanna mess around with Rhythmbox, try this
```

sudo apt-get install mp3info
cd /path/to/files/3Oh!3
mp3info -a "3OH!3" *.mp3

```

this should change the artist name of all mp3's to "3OH!3"
this can't be undone!

---

