---
title: "Recover document from persistent Live USB that no longer boots"
date: 2011-03-08
forum: General Help
---

### Post by StevenSheridan on 2011-03-08
Edit:How do I extract a document from the casper-rw file?
I think the casper-rw file is the problem. I made a fresh Live USB--which booted properly--then replaced the casper-rw file with the one from the problematic flash drive. The new drive now behaves like the old: startup freezes on the Ubuntu splash screen (the dots keep moving, it just never stops).


Original post: My friend wrote a paper on a netbook booted from a Live USB running a recent version of the Netbook Remix, on a persistent installation (I think). He does not know where in the filesystem he saved the file.

When he was writing the paper, the OS was booted in Russian. While the OS was still running, the drive was unplugged. When it was plugged back in, the computer froze. Upon rebooting in English, the document could not be found in a search. After this, the drive will no longer boot; it stays stuck on the splash screen with the dots trickling by.

The flash drive is visible to other OSs. The casper folder has 6 files, including a 667 MB filesystem.squashfs file. Is there a way to settle whether it really was a persistent installation?

So, questions:
1) Could booting it into Russian again give us access to a file that isn't accessible when booted in English? Or are they stored in the same place?
2) If they're stored separately, is there a way to make the thing boot successfully again?
3) Else: where are the persistent files stored? How can I access them?

Thanks for your help; this was an all-nighter paper he lost, which won't be fun to start all over.

---

### Post by dandnsmith on 2011-03-08
Looking at a persistent install of Mint 6, I see a file in the root directory of the usb device named 'casper-rw' which was a file created by the installer for the persistent data.

I'm not sure what the characteristics of this filesystem is (whether compressed etc) so how to mount it.
The same name file is present in other persistent-data installs I have created - including one using a different installer (Ub 10.10 netbook).

I do not think that the language will have any effect - I've switched to and from Spanish with no change on places (just the words describing them).

---

### Post by StevenSheridan on 2011-03-09
Is it possible to deconstruct the casper-rw file?

---

### Post by C.S.Cameron on 2011-03-09
You can mount casper-rw and get at the files inside:

[http://ubuntuforums.org/showpost.php?p=7055983&postcount=2](http://ubuntuforums.org/showpost.php?p=7055983&postcount=2)

---

### Post by StevenSheridan on 2011-03-18
That worked. Thanks.

---

