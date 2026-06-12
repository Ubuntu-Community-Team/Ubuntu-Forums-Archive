---
title: "Clearing Evolution's mailbox search index"
date: 2010-06-23
forum: General Help
---

### Post by Midahed on 2010-06-23
Hello,

On my system running 10.04 and Evolution 2.28.3, searching for ANYTHING in Evolution's inbox returns no results, while a search of the 'sent' folder works fine.

I'm guessing that this is because the index for my inbox folder has become corrupted.

Based on advice I've read elsewhere, after completely shutting down Evolution with the command 'evolution --force-shutdown' I've tried deleting the following files....

~/.evolution/mail/local/Inbox.ibex.index

~/.evolution/mail/local/Inbox.ibex.index.data

~/.evolution/mail/local/folders.db

...but it hasn't made any difference.  Evolution recreates the files on start-up, but the symptoms remain the same.

What's the best way to clear Evolution's index and force it to be rebuilt?

Mike

---

### Post by dcstar on 2010-06-24
> **Midahed said:**
> Hello,

On my system running 10.04 and Evolution 2.28.3, searching for ANYTHING in Evolution's inbox returns no results, while a search of the 'sent' folder works fine.

I'm guessing that this is because the index for my inbox folder has become corrupted.

Based on advice I've read elsewhere, after completely shutting down Evolution with the command 'evolution --force-shutdown' I've tried deleting the following files....

~/.evolution/mail/local/Inbox.ibex.index

~/.evolution/mail/local/Inbox.ibex.index.data

~/.evolution/mail/local/folders.db

...but it hasn't made any difference.  Evolution recreates the files on start-up, but the symptoms remain the same.

What's the best way to clear Evolution's index and force it to be rebuilt?

Mike

Post a screenshot of the non-working search.

---

### Post by Midahed on 2010-06-24
Mmmmmmmmm....  Maybe this was a bit of finger trouble on my part....

I've found that if I change the 'search in' option from 'All Accounts' to 'Current Folder' the search returns the correct results.

That will do as a solution for the moment - it may be that I've always previously had that setting on 'Current Folder', and it only changed after a recent upgrade.  I'm not sure, but either way it works well enough now.

Maybe it's my understanding of Evolution's search feature that's broken!  I'll see what the user manual says, but I'd expected a search across the 'Current Account' or 'All Accounts' to at least produce the matching results that appear when searching 'Current Folder'.

Thanks for your help - it was your request for a screenshot that got me looking beyond the search box.

Mike

---

