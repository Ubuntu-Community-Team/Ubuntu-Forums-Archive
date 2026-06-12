---
title: "Search"
date: 2012-07-30
forum: General Help
---

### Post by mayagrafix on 2012-07-30
How do u search for a document or folder in Ubuntu 12.04?:confused:

I tried using Dash, and although it seems to have a lot of potential, no results are forthcoming.

Particularly I want to search for a doc (a PDF file) that is in a separate (and mounted) partition which I use as a shared storage area (formatted in NTFS). Dash does not have a way (so far as I can tell) to specify a particular area to search, nor does it search all mounted partitions automatically. Or does it?

I opened the aforementioned target folder in Nautilus File Manager (or what ever it is now called under Unity) and used it's find file function and after some waiting, it found the specified file, so I guess I'm not up the river without an oar.

Find command from a terminal seems to be real fast but requires patience to learn. I tried the following:
**find device /sda7 /documents -name theory.PDF**
and no joy.

Is there a better, faster, easier way?

Windows search also sucks (so far Apple Mac is best) but there is a free utility program called "Everything" (for windows OS) that does a complete search STAT. Anything of the sort available for Ubuntu?

Thanks for any help and sorry for the long rant.

---

### Post by andrew.46 on 2012-07-31
If you are truly interested in using *find *perhaps have a look at this Ubuntu Community Doc:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

---

### Post by Dawnbandit on 2012-07-31
> **mayagrafix said:**
> How do u search for a document or folder in Ubuntu 12.04?:confused:

I tried using Dash, and although it seems to have a lot of potential, no results are forthcoming.

Particularly I want to search for a doc (a PDF file) that is in a separate (and mounted) partition which I use as a shared storage area (formatted in NTFS). Dash does not have a way (so far as I can tell) to specify a particular area to search, nor does it search all mounted partitions automatically. Or does it?

I opened the aforementioned target folder in Nautilus File Manager (or what ever it is now called under Unity) and used it's find file function and after some waiting, it found the specified file, so I guess I'm not up the river without an oar.

Find command from a terminal seems to be real fast but requires patience to learn. I tried the following:
**find device /sda7 /documents -name theory.PDF**
and no joy.

Is there a better, faster, easier way?

Windows search also sucks (so far Apple Mac is best) but there is a free utility program called "Everything" (for windows OS) that does a complete search STAT. Anything of the sort available for Ubuntu?

Thanks for any help and sorry for the long rant.
Ctrl+F its that easy!

---

### Post by LewisTM on 2012-07-31
You can install Synapse which provides similar functions as the Dash but finds documents with the locate command. Locate is a system-wide file indexer (fast). Once you get a list of matches, press the down arrow to scroll through them and Tab to reveal actions for each item.

If you want a full-text search utility you should take a look at Recoll. A Recoll [PPA]("http://www.webupd8.org/2012/03/recoll-lens-full-text-search-unity-lens.html") offers a more recent version of Recoll as well as a Unity search lens.

Cheers!

---

### Post by mayagrafix on 2012-07-31
Thanks for the answers, so far so good with Synapse which does a real bang up job of finding/searching for stuff. Only problem is installing (not friendly to Unity) but after some reboots, works great, less filling! :KS

---

