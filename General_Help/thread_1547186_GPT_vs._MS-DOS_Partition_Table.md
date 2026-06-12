---
title: "GPT vs. MS-DOS Partition Table"
date: 2010-08-06
forum: General Help
---

### Post by Ginsu543 on 2010-08-06
Is there a difference between using GPT partition table when formating hard drives and MS-DOS partition table? What are the advantages/disadvantages of using either?

---

### Post by dandnsmith on 2010-08-06
Try reading [this wiki article](http://en.wikipedia.org/wiki/GUID_Partition_Table) which has a good explanation of what is involved.
Note that not all hardware or OS support the GPT system

---

### Post by Ginsu543 on 2010-08-06
Thank you, that article was very helpful. I wonder if others with experience can chime in, but what I would like to know is whether there is a performance boost/advantage of using GPT as opposed to MS-DOS (besides the obvious ability of GPT to have partitions > 2.2 TB).

I had previously always used MS-DOS, but with my install of Lucid, I used GPT. I'm wondering if using GPT (and not MS-DOS) is affecting in any way my ability to use BURG over GRUB2. When I tried BURG, it said that it was installed properly, but when I rebooted it would not "kick in." When I tried removing it, it deleted my GRUB2. When I booted into my backup Karmic partition and tried to restore GRUB2, I got an error message saying that GPT didn't support writing to the MBR and recommended I use the --force flag for grub-install. I did ultimately get my GRUB2 back, but was wondering if this is a concern at all under MS-DOS partition table.

---

