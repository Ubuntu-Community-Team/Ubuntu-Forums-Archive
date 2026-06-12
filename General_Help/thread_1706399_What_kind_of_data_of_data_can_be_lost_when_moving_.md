---
title: "What kind of data of data can be lost when moving files from ntfs to ext4?"
date: 2011-03-13
forum: General Help
---

### Post by nnn= on 2011-03-13
I'm running out of space on an ntfs partition on win pc and would like to move files from it to ext4 partition. I understand ntfs and ext4 metadata aren't exactly the same, so what kinds of things can I expect to lose?

If I alternatively created an ntfs partition for a hard drive on the ubuntu pc, would its ntfs driver be even able to read all the metadata and copy it over the network?

---

### Post by lithopsian on 2011-03-13
You shouldn't lose anything.  There have been issues with writing certain metadata to NTFS drives from Linux, primarily permissions, but if you use the ntfs_3g drivers then you should be fine.  Obviously Windows and Linux permission structures are somewhat different so you'll have to bear that in mind with any files that you copy across.  You can also maintain an NTFS partition to share data between Windows and Linux, or even create new ones.

Most issues you are likely to come across can be solved through correct configuration.  You may need to map Linux to Windows users or your permissions will be bogus.  Obviously you need to enable permissions in the ntfs mount in the first place or every file will I think be owned by root and world readable.  Be careful about the characters used in filenames and make sure they are valid for your locale.  Be doubly careful about case sensitive filenames.

---

