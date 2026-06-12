---
title: "gosfeedback.xml missing"
date: 2011-08-26
forum: General Help
---

### Post by ricnow on 2011-08-26
On Ubuntu 10.04 have put up without parts of help for long time.  Some investigation as to why the message:-
 "The file ‘///usr/share/gnome/help/user-guide/en_GB/user-guide.xml’ could not be parsed because one or more of its included files is not a well-formed XML document."    lead to finding that <gosfeedback.xml> is missing from </usr/share/gnome/help-langpack/user-guide/en_GB> 

Have tried reinstalling various language packages with Synaptic but no change.
 
Failure of help in similar ways seems to have been in bug reports over the years, but I never found any reference to <gosfeedback.xml">

:)

---

### Post by ricnow on 2011-08-27
I seem to have solved this Help problem.

So: Ignoring the error reports about badly formed xml file or if via Forefox, missing style information.

I have replaced all the files missing from </usr/share/gnome/help-langpack/user-guide/en_GB/ with ones found in </usr/share/gnome/help-langpack/user-guide/en_AU/>  i.e gosfeedback.xml and several others.

Help now works fine.

Cheers

---

