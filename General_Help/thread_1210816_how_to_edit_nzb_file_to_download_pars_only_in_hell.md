---
title: "how to edit nzb file to download pars only in hellanzb"
date: 2009-07-11
forum: General Help
---

### Post by gahligahli on 2009-07-11
Edit:  Problem solved

i have been using hellaNZB for many months to fetch binaries from usenet, and I have encountered a problem. 

a download has been moved to my "done" folder, but failed to extract from RAR form.  When I try to extract it, it says that rar part .36 is corrupt.  Fair enough.  ordinarily i would run the par2verify command, but no PARs were downloaded for this NZB due to it not being recognised as corrupt.    

How do I download all the pars from this NZB, on account of them being skipped?  Without re-downloading the rest of the actual data file the NZB points to as well?  

My solution was to edit the NZB file so it only references the par files,  edit hellanzb.conf to skip smart par, and then let it download them all.  But I cannot find any linux tools that let you edit a par file, and I can not make any sense of opening it in a text editor, i am unable to differentiate between the fields in it.

if someone has experienced this then that would be good.
____________________

edit:
solved!

---

### Post by wiplash on 2011-07-08
could you share how you solved this?

---

