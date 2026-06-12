---
title: "Dell Studio 1535 no speaker support?"
date: 2012-07-13
forum: General Help
---

### Post by shamusl on 2012-07-13
I just came onto an old Dell Studio 1535 and installed Ubuntu 12.04 and I can't get sound through the speakers. The sound works through (one of the) headphone jacks (theirs two), and I'm thinking Ubuntu has some kind of problem with this, since it lists two soundcards installed in the laptop by default. 

I checked around the Internet and other people don't seem to be having this problem. Could it be a hardware problem?

Any ideas?

---

### Post by Rexilion on 2012-07-14
Maybe they are muted?

```
alsamixer
```

(also press F6 to switch card)

If the the cards are incorrectly switched, then I would suggest using grub and the index option for each sound driver to arrange them correctly. That is like a system-wide setting that works.

---

