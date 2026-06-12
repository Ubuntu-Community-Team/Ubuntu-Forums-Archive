---
title: "How to Recursively Check par2s"
date: 2010-08-22
forum: General Help
---

### Post by Stvnx7 on 2010-08-22
Hi all. 

I have been having trouble recursively checking par2s when there is more than 1 set of par2s in a given directory. At the moment, using cfv's recursive feature (r), it will only check for one set of par2 files in a given directory. How can I "tell" cfv to check for multiple par2 sets in a given directory? 

Thanks, 

Steven

P.S. This situation occurs when (1) I download a full season of a show into one directory due to it being one big NZB file, and also (2) when each episode has its own directory, but there is a separate set of par2 files for the sample .avi file.

---

### Post by hwttdz on 2010-08-22
I assume you mean parity volume archive?  

It sounds like you should be able to do something of the sort of
find . -name "*.par2"|xargs -n 1 -I{} bash -c "cfv {} {}.checksum"

which will execute the command
cfv filename filename.checksum for each par2 file in . or any subfolder.

---

### Post by Stvnx7 on 2010-08-23
> **hwttdz said:**
> I assume you mean parity volume archive?  

It sounds like you should be able to do something of the sort of
find . -name "*.par2"|xargs -n 1 -I{} bash -c "cfv {} {}.checksum"

which will execute the command
cfv filename filename.checksum for each par2 file in . or any subfolder.

Thank you very much for your response. Yes, by par2 I mean a parity archive set. 

While the solution you posted does indeed work, and has already saved me a lot of time, I was wondering if it is the most efficient solution. The reason I ask is because it seems to check every single par2 file. Multiple par2 files belong to the same par2 set, so that if the first file in that par2 set tells me that the checksums don't match, I don't need to check the second par2 file in that same set, since the results will be the same. Would cfv be able to test / check each set only once?

---

### Post by Stvnx7 on 2010-08-24
Maybe it would be easier to use the par2repair command line program in this process? Instead of having the par2s checked, I'd have them all checked and repaired.

---

