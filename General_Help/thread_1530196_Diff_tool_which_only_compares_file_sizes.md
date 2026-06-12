---
title: "Diff tool which only compares file sizes"
date: 2010-07-13
forum: General Help
---

### Post by Mr. Matt on 2010-07-13
I have recently copied my large MP3 collection from one computer to another.  I had to interrupt the transfer a couple times so I want to check if any files were not copied fully?

Is there a diff or compare tool that will recursively compare directories but only based on the file names and file sizes?  'diff' seems to compare the contents which takes way too long.  I don't need to compare the contents - just the filesize.

I didn't realise this would be so hard to find.  I thought it would be a common tool.

Thanks

---

### Post by surfer on 2010-07-13
you could copy the rest with

```

$ rsync -rvz --size-only src_dir dst_dir

```

would that help?

---

### Post by Mr. Matt on 2010-07-17
I found the 'du' command and then ran the output through Meld but rsync would probably work as well.  I will try that next time.  Thanks.

---

