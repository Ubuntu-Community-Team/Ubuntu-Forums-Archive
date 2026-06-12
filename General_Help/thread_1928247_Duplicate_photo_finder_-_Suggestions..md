---
title: "Duplicate photo finder - Suggestions?."
date: 2012-02-19
forum: General Help
---

### Post by Rafterman414 on 2012-02-19
I have about 90 GB worth of photos that my wife has taken over the years, and there are a great deal of duplicates. I am looking for a Linux or Windows program to find duplicate files. 

The catch is I have tried several such programs however many of the files that I have that are detected as duplicates are in fact not dupes, this is because the file name is the same and so is the filesize. Is there such a program that can look at the actual image and not just file name and file size and make the determination if a file is a dupe or not based on the image content? I have Googled a few that claim to do such a task, but does anyone have any first hand experience?

If anyone has any suggestions I appreciate it. Thanks.

---

### Post by Ms. Daisy on 2012-02-19
I don't have any experience with it, but FSlint looks promising.  According to the [FAQ ]("http://fslint.googlecode.com/svn/trunk/doc/FAQ")it looks at more than just the name & file size. 

Here's a guy who wrote a script to hash the files & list all the duplicates.
[http://www.forensickb.com/2008/05/find-duplicate-files.html](http://www.forensickb.com/2008/05/find-duplicate-files.html)

---

### Post by duke.tim on 2012-02-19
I would just like to note that even if it uses hashes, if the duplicates are of different file types it will not report pic.jpg and pic.gif as the same. (assuming they both are the same)

---

