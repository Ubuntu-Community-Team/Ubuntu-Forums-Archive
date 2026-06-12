---
title: "Tape Restore Problems"
date: 2011-03-31
forum: General Help
---

### Post by john_corry on 2011-03-31
Hi,
 
I have a dlt1 tape which has a backup created on a win2000 server using brightstor arcserve version 9.
 
I want to restore the data on my ubuntu server which has a dlt4 sata drive.
 
I run the following:-
 
tar -b 256 -tf /dev/st0
 
and I get:-
 
tar: Record size = 128 blocks
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure
 
Is it possible to restore the data that is created by windows onto linux? If so, what do I need to do?
 
Thanks in advance,
 
John.

---

