---
title: "cmus and streaming - how?"
date: 2012-01-10
forum: General Help
---

### Post by casbahdk on 2012-01-10
How do I get [cmus]("http://cmus.sourceforge.net/#features") to play icecast/shoutcast streams? The documentation states that it is possible, but does not explain how. I have tried creating a "radio.pls" file as in [this thread]("http://boards.openpandora.org/index.php?/topic/6548-cli-love-what-can-you-do-with-it-examples/"), and navigating from within cmus to the file, but nothing happens. Anyone have any ideas?

---

### Post by casbahdk on 2012-01-27
The way to do this, according to the maintainer of the cmus-devel mailing list, is as follows:> Just do```
:add http://your_stream_url
```the stream will show up with <Stream> pseudo-artist in the tree view.

---

