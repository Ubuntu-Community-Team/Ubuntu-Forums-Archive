---
title: "Stopping e2fsck mid-run"
date: 2010-01-11
forum: General Help
---

### Post by jektal2 on 2010-01-11
I have a very large (6.x TB, Drobo), and very effed, ext3 partition which I'm attempting to run e2fsck on, after running mke2fs, in an attempt to fix the journal.

The problem is I didn't specify the automatic/passive argument when I ran e2fsck, so I'm stuck with a seemingly endless set of confirmation prompts.

Can I CTRL+C e2fsck and then run it again, or will this cause further damage?

Thanks greatly for any help, I think I'm going to break my "y" key if I can't restart this.

---

### Post by dcstar on 2010-01-12
> **jektal2 said:**
> I have a very large (6.x TB, Drobo), and very effed, ext3 partition which I'm attempting to run e2fsck on, after running mke2fs, in an attempt to fix the journal.

The problem is I didn't specify the automatic/passive argument when I ran e2fsck, so I'm stuck with a seemingly endless set of confirmation prompts.

Can I CTRL+C e2fsck and then run it again, or will this cause further damage?

Thanks greatly for any help, I think I'm going to break my "y" key if I can't restart this.

AFAIK it should just restart from where you interrupted it on the next run.

---

