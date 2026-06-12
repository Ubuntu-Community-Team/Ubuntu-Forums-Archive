---
title: "Looking for a Gmail notifier that does not work by diffing the Atom feed"
date: 2009-08-07
forum: General Help
---

### Post by clanmackay on 2009-08-07
Hello friends,

I tend to keep more than 10-20 unread messages in my Gmail account.  The Linux new message notifiers I have tried appear to just run a diff against the last-retrieved Atom feed.  The problem with this is that if you have more unread messages than are in the XML file the notifier checks, when you read a message it notifies you of a message, because (?) a "new" (in reality, older) message appears at the bottom of the list.

Google's native checker for Windows uses another technique and handles this properly, but they may be using an undocumented API.

I think I've tried CheckGmail and KCheckGmail so far.

Ideas?

Thank you.

---

### Post by lvleph on 2009-08-07
gm-notify doesn't diff the atom feed. I didn't like it though.

---

