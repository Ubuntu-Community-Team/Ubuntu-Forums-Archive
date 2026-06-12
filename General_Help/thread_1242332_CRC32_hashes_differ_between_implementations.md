---
title: "CRC32 hashes differ between implementations"
date: 2009-08-17
forum: General Help
---

### Post by thomasyen on 2009-08-17
I've recently decided to do a CRC32 hash check on some of my downloaded anime. To my surprise, files that checked out (i.e. the CRC32 hash matches the one in the filename) on my Windows box (using RapidCRC) gave a different hash on my Ubuntu box (using GtkHash, which uses the libmhash2 library). This intrigued me, so I created a text file containing only the string "Test string" (without quotes), ran it through RapidCRC, GtkHash, and GNU cksum (I converted the cksum result from decimal into hex), and got entirely different results. I checked around Wikipedia and the Web, but I don't think the CRC32 hash is dependent on the filesystem or operating system...or am I missing something? Can anyone give me a few hints?

---

### Post by mikechant on 2009-08-17
You've probably checked this but:
Some of these utilities support a number of hashes. Are you sure they're not defaulting to using different (i.e. non-CRC32) hashes in some cases?

Update: I've also noticed that libmhash2 supports two different CRC32 hashes.

---

### Post by thomasyen on 2009-08-18
> **mikechant said:**
> You've probably checked this but:
Some of these utilities support a number of hashes. Are you sure they're not defaulting to using different (i.e. non-CRC32) hashes in some cases?

Update: I've also noticed that libmhash2 supports two different CRC32 hashes.

Yes, I've checked. RapidCRC produces only a CRC32 hash and an MD5 hash (both implemented in assembly). I've set GtkHash to produce a CRC32 hash and (just now) a CRC32B hash (which is yet another hash, different from the other three hashes). The manpage of GNU cksum says that it "prints CRC checksum and bytecounts of each FILE". Although the manpage doesn't specify the *type* of CRC, cksum returns a decimal value that, when converted to hex, has a length of eight hex values. Because of this, I assume this to be CRC32. The new results have been inserted into the "results.txt" file in my initial post. (As a side note, I have no idea what the difference between CRC32 and CRC32B is. Both seem to be 32 bits long.)

Update: I searched through the repos for a CRC32 application,and found a utility called jacksum (which uses the Java API). The jacksum implementation of CRC32 matches that of RapidCRC. However, I still don't understand why these implementations differ.

---

### Post by lisati on 2009-08-18
According to [Wikipedia]("http://en.wikipedia.org/wiki/Cyclic_redundancy_check") there are four different variations for CRC-32. Perhaps this would account for at least part of the differing results.

CRC calculation is something that I haven't realling looked into in great depth (how do you simply explain a CRC to someone who knows next to nothing about the subject?), but suspect that perhaps the different programs are using different quotients.

---

### Post by Windows Nerd on 2009-08-18
In all honesty I dont think this belongs in *Absalute Beginner  Talk*. It is way above what an average user knows.

---

### Post by thomasyen on 2009-08-18
> **lisati said:**
> According to [Wikipedia]("http://en.wikipedia.org/wiki/Cyclic_redundancy_check") there are four different variations for CRC-32. Perhaps this would account for at least part of the differing results.

Thanks for the hint. I'm beginning to think that this is another one of those cases where a lot of people just skip the suffix or prefix of a name out of laziness or (in their minds) brevity. In the end, those who implement "CRC32" don't even specify the subtype (CRC-32-IEEE 802.3, CRC-32C, CRC-32K, CRC-32Q). This can get really confusing.

> **Windows Nerd said:**
> In all honesty I dont think this belongs in *Absalute Beginner  Talk*. It is way above what an average user knows.

You're right, but the reason I chose this panel is because the other ones are too specific with regard to subjects. If you find a more suitable panel though, feel free to move this thread.

As an update, I found another utility: cfv. It matches the RapidCRC implementation. See my first post for update.

Update: I think this thread should be moved to General Help. Can an admin move this, please?

---

