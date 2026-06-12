---
title: "Amarok 2.1.1 Issues"
date: 2009-10-11
forum: General Help
---

### Post by kooldino on 2009-10-11
I have a few issues with Amarok on my kubuntu 9.04 box.  I've tried reinstalling it several times to no avail.  Issues are as follows.

1-Incorrect album art. I'm not sure how or when it went wrong, but it frequently displays the wrong cover art.  It usually displays the art for the wrong band completely, and when I go to Fetch new art, no results are found.  

2-My collection.  It scans and gets to 93% each time I open it, and then it refuses to make it past that point.  What gives?

3-When I have a song paused, I will still get the overlay every few minutes in the upper left corner of the screen which is apparently reminding me of the track info on the song that I'm choosing not to listen to.

4-Whenever I remove the program and uninstall it every way I know how, it always comes back with the same settings and playlist when I reinstall it.

Help!

---

### Post by ad_267 on 2009-10-11
Number 1 and 2 I had problems with too, but they have supposedly been fixed with Amarok 2.2. I haven't tried it myself yet though.

Number 3 I've got no idea.

For number 4 you need to remove all of your personal settings which are stored in ~/.kde/share/apps/amarok

---

### Post by kooldino on 2009-10-11
> **ad_267 said:**
> Number 1 and 2 I had problems with too, but they have supposedly been fixed with Amarok 2.2. I haven't tried it myself yet though.

How can I get Amarok 2.2?  I don't see it in my repository.

> For number 4 you need to remove all of your personal settings which are stored in ~/.kde/share/apps/amarok

Ah, I didn't look that deep, i just looked under .kde

I deleted it, but it's now re-stuck at 93% again.  Bah.

---

### Post by ad_267 on 2009-10-11
Usually I can shut down Amarok and try rescanning again and it will be able to finish.

You can install 2.2 on Ubuntu 9.04 with these instructions: [http://webupd8.blogspot.com/2009/09/install-amarok-22-rc1-in-ubuntu-jaunty.html](http://webupd8.blogspot.com/2009/09/install-amarok-22-rc1-in-ubuntu-jaunty.html)

---

