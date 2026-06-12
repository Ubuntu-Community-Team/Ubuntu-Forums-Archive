---
title: "View mailbox size in Evolution"
date: 2010-03-05
forum: General Help
---

### Post by 98cwitr on 2010-03-05
Outlook has their PST file, where can I see how large the mailbox is for the evolution mail client?

---

### Post by Barriehie on 2010-03-05
~/.evolution/mail/local is where the mailbox files are stored.

---

### Post by gordintoronto on 2010-03-05
And the folder is hidden. You can Edit the Preferences in Nautilus to display hidden folders.

---

### Post by Barriehie on 2010-03-05
> **gordintoronto said:**
> And the folder is hidden. You can Edit the Preferences in Nautilus to display hidden folders.

My bad!  or you can use CTRL-H to toggle the display of hidden folders.

---

### Post by 98cwitr on 2010-03-06
so my evolution folder size is roughly 18Mb then?

[email]brett@brett-desktop:~/.evolut[/email]ion/mail/local$ ls
Drafts                  Outbox                  Sent.cmeta
Drafts.cmeta            Outbox.cmeta            Sent.ibex.index
Drafts.ibex.index       Outbox.ibex.index       Sent.ibex.index.data
Drafts.ibex.index.data  Outbox.ibex.index.data  Templates
folders.db              saved                   Templates.cmeta
Inbox                   saved.cmeta             Templates.ibex.index
Inbox.cmeta             saved.ibex.index        Templates.ibex.index.data
Inbox.ibex.index        saved.ibex.index.data
Inbox.ibex.index.data   Sent
[email]brett@brett-desktop:~/.evolut[/email]ion/mail/local$ du
12	./.#evolution.sbd
18456	.
[email]brett@brett-desktop:~/.evolut[/email]ion/mail/local$

---

### Post by darolu on 2010-03-06
Try with:
```
ls -lah ~/.evolution/mail/local
```

---

