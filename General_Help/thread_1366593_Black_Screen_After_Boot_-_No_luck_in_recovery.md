---
title: "Black Screen After Boot - No luck in recovery"
date: 2009-12-28
forum: General Help
---

### Post by Aeroice on 2009-12-28
So, this morning my mom (whose laptop has Xubuntu installed on it) informed me of a problem: her computer no longer functioned. There are a few interesting things that I think may help in diagnosing the problem:

1. GRUB appears. It did not do this before today; it simply booted directly into Xubuntu 9.10. The interesting thing is, it lists 3 separate systems (I guess?) - Linux 2.....14, 2.....15, and 2....16. I don't remember the numbers in between, but it lists all three of those *and* their recovery modes. 

2. If you're booting in the regular mode (i.e. non-recovery) then the mouse will come up, but it doesn't seem to fade in and out like it normally does. A minute or two after the mouse appears, the screen goes completely black.

3. If you're booting in recovery mode, it says that it "gave up on waiting on the root filesystem" (or something to that effect.) It lists a few "common issues" but I've never encountered these problems before today. I found a post on the internet talking about using *dpkg*, but that isn't a command in recovery mode apparently (it says it can't find dpkg in /bin/sh).

I've got no idea what the problem is, so I was wondering if anyone here had either experienced this problem or diagnosed it in the past or had any interesting ideas. I'm thinking it could be a HD problem, but I'm not exactly an expert with Linux so I'm not entirely sure.

---

