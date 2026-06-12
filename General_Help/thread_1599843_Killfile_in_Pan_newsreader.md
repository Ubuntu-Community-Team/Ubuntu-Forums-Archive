---
title: "Killfile in Pan newsreader?"
date: 2010-10-18
forum: General Help
---

### Post by Peter McVries on 2010-10-18
Can anyone help with this?  I try to killfile a poster on usenet by ignoring author and setting article score to -9999 forever.  This only flags up the score for the poster when viewing a usenet group.

What I'd really like is to not download or see posts from ignored users or ignored subjects /at all/.

I can't figure out a way to do this in Pan (or Knews or Tbird for that matter).

---

### Post by cor2y on 2010-10-18
usually when adding a scoring rule to pan i set the article criteria to either subject contains or author contains.
With the article score -9999 and the duration to forever then click add and rescore and that works.
Now i have no idea if pan downloads the headers and then deletes them when i get new headers or if the filters doesnt download them but they never turn up again.
Also if this doesnt work you might try downloading the most recent build of pan2 from K. Haley's git repo which has added fixes that the main ubuntu one may not have, you will have to compile it yourself but here are some instructions

[http://www.scottkuma.net/pan-newsreader-and-multi-part-images-in-ubuntu-9-10-karmic-koala](http://www.scottkuma.net/pan-newsreader-and-multi-part-images-in-ubuntu-9-10-karmic-koala)

---

