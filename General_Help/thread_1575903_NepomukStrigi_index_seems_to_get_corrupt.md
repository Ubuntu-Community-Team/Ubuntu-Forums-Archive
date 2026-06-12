---
title: "Nepomuk/Strigi index seems to get corrupt"
date: 2010-09-16
forum: General Help
---

### Post by StiltonSandwich on 2010-09-16
I am just posting this in case anyone else has had the same problem or knows a better solution, or whether this is worth digging deeper into as a bug.

I have Nepomuk/Strigi enabled on my Kubuntu 10.04 system (KDE 4.4.2), and it sometimes works. However, every now and again, it seems to stop working and Strigi gets automatically disabled. It is possible to coax it back into action by repeatedly turning it off and on again. But, when I do this, the information window perpetually shows "Calculating..." for the number of files indexed, the Nepomuk store size remains static at a large value, and Strigi has started indexing from the beginning rather than where it left off previously. Nothing can be retrieved from the index in the form of search results or to display metadata for files in Dolphin or Konqueror.

When I log out and back in again, it's back to square one, Strigi has been automatically disabled, and it just goes on like this perpetually.

However, if I disable Nepomuk and Strigi, delete my Nepomuk store at ~/.kde/share/apps/nepomuk/repository/ and then re-enable Nepomuk and Strigi, Strigi begins indexing from the beginning, "Files indexed" shows "0" (correctly; since I just deleted the index) and counts upwards, and the store size shows "10 MiB", counting slowly upwards. Furthermore, metadata starts to become available in Dolphin and Konqueror, for files that have been indexed. What's more, the index survives when Strigi is stopped and restarted. This is what you would expect to happen when you run Strigi.

Clearly my index has been getting corrupted in some way or another, but I have no idea how. It has done it about three times so far, lasting several months each time before failing again. Once, the index swelled to over 4 GiB to no avail, but normally it stabilises at a few hundred MiB, works for a while and then silently stops working one day.

If you are having similar problems, you may find that deleting your Nepomuk store, as I have, and letting Strigi rebuild its index, will act as a workaround.

I am led to believe that Strigi has been improved for KDE SC 4.5, and a new system is being put in place for displaying file metadata when the file is not in the Strigi index (or Strigi is disabled), so hopefully this is a temporary situation.

---

