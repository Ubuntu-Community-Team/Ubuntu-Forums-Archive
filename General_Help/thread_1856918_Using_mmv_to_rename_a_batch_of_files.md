---
title: "Using mmv to rename a batch of files"
date: 2011-10-09
forum: General Help
---

### Post by jackn on 2011-10-09
I've scoured the forums in search of an easy way of renaming a batch of files.

I'm trying to change the names of a bunch of files such that they have new numbers. Thus, to give an example, say I now have a series 12gym-98gym, I'd like to change those to 24back-110back. A change in the numbers would do (keeping the 'gym' bit), but I'd like to change the names altogether, yet keeping a series of numbers. The numbers would make up a new series, shifted upwards.
I'd like to avoid getting into regular expressions (required to use *rename*), and I didn't understand *pyRename*.

*mmv* seemed handy, as I feel comfortable with *mv*.

When I tried to rename a batch of files using *mmv*, it seemed like the 'to' range (as the *mmv* manual entry calls it) in my command, which to me was a range of files, meant the name of a single file only to *mmv*. 
As a result, mmv wouldn't rename, reporting a collision:
```
~$ mmv Desktop/delete/'0*.mp3' Desktop/delete/'1[345]audio_impact.mp3'
Desktop/delete/02-AudioTrack 02.mp31[3-5]audio_impact_cd.mp3 , Desktop/delete/03-AudioTrack 03.mp31[3-5]audio_impact_cd.mp3 , Desktop/delete/04-AudioTrack 04.mp31[3-5]audio_impact_cd.mp3 -> Desktop/delete/1[345]audio_impact.mp3 : collision.
Nothing done.

```

*mmv* doesn't seem to consider [345] as a range, but to take it literally. 
The result is the same whether the 'to' range is stated as [345], [3,5] or as [3-5]. 
Likewise, it makes no difference whether I surround the 'to' range with single quotes or not.

Can someone please help me coax *mmv* into doing my bidding?

Thank you.
jackn

---

### Post by jackn on 2011-10-15
Bump...

---

