---
title: "HD partition trouble"
date: 2009-07-28
forum: General Help
---

### Post by Flexico on 2009-07-28
OK, I just re-partitioned my hard drive, and it said there was an error. Thankfully, my Ubuntu still boots up fine, but:

[color=orange]Ubuntu, used[/color]
[color=brown]Ubuntu, unused[/color]
[color=blue]Other[/color]

Before:
[color=blue][-----------][/color][color=orange][--------[/color][color=brown]--------][/color]
After:
[color=orange][--------------------[/color][color=brown]--------][/color]
what it should be:
[color=orange][--------[/color][color=brown]--------------------][/color]

Now it's like part of my hard drive doesn't exist. Through the filesystem, I'm still only registering 35.3 GB (which is what it should be) but the hard drive itself (through gparted) is registering as having 98 GB used! How do I fix it?

---

