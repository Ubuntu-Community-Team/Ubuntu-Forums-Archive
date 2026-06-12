---
title: "Update Manager Errors?"
date: 2010-01-07
forum: General Help
---

### Post by DynastyX on 2010-01-07
Hey everyone, for the past four or so days there have been a few updates for my system (32bit Karmic). I tried ignoring it at first to see if it would go away, but this is the third time I've seen these error messages.

> Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".
I click the "Run this action now" button and I get a second error,

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/karmic/Release](http://repository.cairo-dock.org/ubuntu/dists/karmic/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
I think I understand what it's telling me, but I don't really know how to fix this. All help is appreciated, thanks.

---

### Post by michy99 on 2010-01-07
The server at repository.cairo-dock.org seems to be down. If you disable that repository, everything else should work fine.

---

### Post by howefield on 2010-01-07
> **michy99 said:**
> The server at repository.cairo-dock.org seems to be down. If you disable that repository, everything else should work fine.

Answers to the cairo-dock repository in this thread.

[http://ubuntuforums.org/showthread.php?t=1373828](http://ubuntuforums.org/showthread.php?t=1373828)

---

### Post by DynastyX on 2010-01-07
[Solved] Thanks guys :)

---

