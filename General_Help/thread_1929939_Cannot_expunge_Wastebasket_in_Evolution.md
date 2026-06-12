---
title: "Cannot expunge Wastebasket in Evolution"
date: 2012-02-22
forum: General Help
---

### Post by SteveHillier on 2012-02-22
Ok guys, I know this subject has been raised before, however none of the solutions given seemed to work for me.  I have now fixed my problem so maybe this might help someone else.
Ubuntu 11.10, Evolution 3.2.2
As described elsewhere I could not empty the Wastebasket - or more precisely the main wastebasket.  The waste basket associated with imported emails was fine.
Following the advice from elsewhere I deleted the .cmeta and .index files whereever I found them.
My location was .local/share/evolution/mail/local as well as some other folders under the ../mail folder.
After doing this when I tried to empty the wastebasket it failed but it did give me a message 'Cannot contact mail.<domainname>.  Connection timed out'.
Now this domain is one that I have only just set up and for whatever reason the dns was not resolving (I checked with ping!).  I added the appropriate entry in my /etc/hosts file and re-ran the expunge function and behold - all mail expunged.
I have no idea why this should give problems or why evolution would want to be connecting to the mail server during the expunge function or indeed why I should get a timeout on this when I didn't get a timeout during  send/receive function.
However, if this helps others then all is good.

Steve

A propos absolutely nothing my wireless keyboard gave up while I was writing this post.

---

