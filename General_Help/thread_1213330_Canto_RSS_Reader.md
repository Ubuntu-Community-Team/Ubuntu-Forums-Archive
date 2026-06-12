---
title: "Canto RSS Reader"
date: 2009-07-14
forum: General Help
---

### Post by kandieyman on 2009-07-14
I would like to filter the entries shown in canto. I know how to limit the entries to a fixed number, but I would like the feed to show all *unread* entries. Is that possible?

---

### Post by TheMoken on 2009-07-25
Yes, it's possible. First of all, if you're using the 0.5.7 package in Jaunty, you might want to consider an upgrade to 0.6.x in Karmic or the newly released 0.7.0, if you're comfortable with installing outside of apt.

Anyway.

First, make sure you have

```
from canto.extra import *
```At the top of your config. Then it should be as simple as

```

filterlist=[show_unread, None] # 0.5.7
filters=[show_unread, None]    # >= 0.6.0 

```If you have trouble with either (particularly if you're using 0.5.7 because I could be forgetting something), it might be better to ask in #canto on irc.freenode.net or email me (I'm the creator) directly (jack at codezen dot org). It's really by chance I discovered your post.

EDIT: I forgot, with this it will filter your items by default and you can use [/] to switch between the filtered and unfiltered views.

---

