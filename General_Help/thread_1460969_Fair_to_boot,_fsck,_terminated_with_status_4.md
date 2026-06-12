---
title: "Fair to boot, fsck, terminated with status 4"
date: 2010-04-23
forum: General Help
---

### Post by Kdar on 2010-04-23
> fsck /home [803] terminated with status 4

This is what I am getting when I am trying to boot. Does anyone know how can I fix it?

Before that, the Transmission BitTorrent client froze, and froze all other windows in Gnome, so I had to reboot manually.

---

### Post by Penguin Guy on 2010-04-23
Perhaps [this]("http://ubuntuforums.org/showthread.php?t=1333270") post may be helpful.

Basically:
[LIST=1]
[*]Boot into liveCD
[*]Find the partition you want to fix (e.g. [FONT="Courier New"]/dev/sda5[/FONT])
[*]Run [FONT="Courier New"]sudo fsck -p *<partition>*[/FONT]
[/LIST]

Once you've figured it out, please [mark your post as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

