---
title: "How to backup Firefox history?"
date: 2012-03-10
forum: General Help
---

### Post by ubuntu27 on 2012-03-10
Hello all. The release day for Ubuntu 12.04 is almost near us. And for those of us who likes to do a Fresh Install are very likely to make a backup of their personal files.


Could you guys guide us in how to backup Firefox history? Specifically the visited sites that appear in the address bar.
I don't want to copy the whole Firefox folder since it might ruin the user experience in the next version or carry bad configurations.


Thank you all! :KS

---

### Post by plucky on 2012-03-10
> **ubuntu27 said:**
> Hello all. The release day for Ubuntu 12.04 is almost near us. And for those of us who likes to do a Fresh Install are very likely to make a backup of their personal files.


Could you guys guide us in how to backup Firefox history? Specifically the visited sites that appear in the address bar.
I don't want to copy the whole Firefox folder since it might ruin the user experience in the next version or carry bad configurations.


Thank you all! :KS

Just Backup your **Bookmarks** which will create a .json file which you can then import into the next version of Firefox.

Good Luck

---

### Post by Megaptera on 2012-03-10
... or take a look at Xmarks: (Quote) "Install Xmarks on each computer you use, and it seamlessly integrates with your web browser and keeps your bookmarks safely backed up and in sync. Xmarks will sync across browsers too. Today we support Firefox, Chrome, Internet Explorer, and Safari (Mac OS)." [http://www.xmarks.com/about/features](http://www.xmarks.com/about/features)

---

### Post by Dave_L on 2012-03-10
> **plucky said:**
> Just Backup your **Bookmarks** which will create a .json file which you can then import into the next version of Firefox.

In Firefox 10.0.2, "History >> Show All History >> Backup..." and "Bookmarks >> Show All Bookmarks >> Backup..." produce the same file, with the default name "bookmarks-2012-03-10.json".

Does that same .json file contain both History and Bookmarks, or is that a bug?

---

### Post by ubuntu27 on 2012-03-10
Thank you guys for your answers.

So, is the .json file also contains visited site (URL) that shows up in the address bar?

In another words I will like to know what Dave said:

> **Dave_L said:**
> In Firefox 10.0.2, "History >> Show All History >> Backup..." and "Bookmarks >> Show All Bookmarks >> Backup..." produce the same file, with the default name "bookmarks-2012-03-10.json".

Does that same .json file contain both History and Bookmarks, or is that a bug?

---

### Post by plucky on 2012-03-11
> **Dave_L said:**
> In Firefox 10.0.2, "History >> Show All History >> Backup..." and "Bookmarks >> Show All Bookmarks >> Backup..." produce the same file, with the default name "bookmarks-2012-03-10.json".

Does that same .json file contain both History and Bookmarks, or is that a bug?

It looks like the History file doesn't get preserved when you use History > Backup.The file size is the same as Bookmarks > Backup.

You have to save the whole hidden .mozilla file in your /home directory to preserve the history.

If you rename the .mozilla file,when you start Firefox it creates a new .mozilla file with all the Bookmarks and History removed.You can then Restore the .json file, but it only contains the Bookmarks,not the History.

Good Luck

---

### Post by Dave_L on 2012-03-11
> **plucky said:**
> It looks like the History file doesn't get preserved when you use History > Backup.The file size is the same as Bookmarks > Backup.

Not only is the file size the same, but the files are identical, as determined by a (binary) comparison.

I tried searching to see if this is a known/reported bug. But there seem to be so many open bugs in this area, I gave up.

---

