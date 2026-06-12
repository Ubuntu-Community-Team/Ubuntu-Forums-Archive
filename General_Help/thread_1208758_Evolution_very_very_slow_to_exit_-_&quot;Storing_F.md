---
title: "Evolution very very slow to exit - &quot;Storing Folders&quot;"
date: 2009-07-09
forum: General Help
---

### Post by 61811 on 2009-07-09
Hi:

Evolution mail was working fine till a few days ago. Now, while exiting the application, it will take several minutes with the message "Storing Folders" starting to slow down at around 50% and completely coming to a crawl at 70%. 5-10 minutes later it will finally exit.

Please help with what needs to be checked/modified.

Thank you.

---

### Post by 61811 on 2009-07-09
Problem solved.

Trash folder was filling up and not expunging itself on exiting Evolution. Manually trying to "Empty Trash" would not work either, and the same slow counting would start whereby it would almost get stuck at 70%.

Found this somewhere else:
-----------------------------------------------------------------
In Terminal type:
*find ~/.evolution/ -name "*.ev-summary" -print0 | xargs -0 rm -rf*

Restart Evolution
-----------------------------------------------------------------

This time around the Trash folder lets itself be cleaned by "Empty Trash". Everything starts working as a charm.

---

### Post by 61811 on 2009-07-09
Just realized that all my messages in the Inbox from the past few months also got deleted along with the ones in Trash. Wonder if they were somehow linked.

Please help!!

Where could they be residing? Any way of retrieving them?

---

