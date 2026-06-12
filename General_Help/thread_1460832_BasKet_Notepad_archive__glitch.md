---
title: "BasKet Notepad archive  glitch"
date: 2010-04-23
forum: General Help
---

### Post by SlayBeau on 2010-04-23
I've been using BasKet Notepad for about two years now on a Dellbuntu Mini-9.  I just installed Mint8 Xfce and finished installing all my preferred apps this morning, including Basket.

Unfortunately, when I tried to import my archive from the old system (saved on a thumb), it fails to recognize it as an archive file.  At first I thought it might be linked ot its apparent inability to recognize the thumb drive, so I transferred the file to the SSD, extracted it, etc.  All the files are there, it seems, but the individual baskets are all saved as .html files.  There doesn't seem to be any "archive" as such that I can import.

Now the weird thing is that I've imported the archive before, back into Basket on  the dellbuntu version of 8.04, without any problem.  What gives?

This is my research.  For my dissertation.  While I'm heartened that it still exists, I am more than a little annoyed at the notion that I might have to cut and paste every damn basket into the system (which I've already done once when I tried to put the notes on my home desktop XP system.  I am returning to the field in five weeks and really want these things accessible.  Is there any help for this?

---

### Post by SlayBeau on 2010-04-25
Worth and update, folks, for anybody else who get stuck:

When the archive gets unpacked from the .tar, there will be a folder called "baskets."  This folder needs to be put into the  subdirectory ".kde/share/apps/basket" in the home directory.  It is hidden, so once in  ~/, mouse up to "view" and check "show hidden files.  Once the .kde directory is revealed, simply navigate to the subdirectory and drag-and-drop.

Easy peasy.

---

