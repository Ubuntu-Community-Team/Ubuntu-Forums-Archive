---
title: "Openoffice.org recovery"
date: 2009-12-01
forum: General Help
---

### Post by s3a on 2009-12-01
If you randomly shut down your computer or there is a power outage or something openoffice.org "rescues" your file and asks you to reload the next time it is launched. It usually successfully rescues it and I haven't ever had any problems. My current "problem" is that I had shut down my computer when an openoffice.org window was open (and thus saved in /tmp as a temporary file). I was hoping somebody could tell me how to remove the screen that wants to recover the files but ends up failing with red x marks (This happened more than one time with different files).

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by jmszr on 2009-12-01
s3a,

Here is a link to a OOo forum post about this issue (I've had it also): [http://www.oooforum.org/forum/viewtopic.phtml?p=156335#156335](http://www.oooforum.org/forum/viewtopic.phtml?p=156335#156335) . You just need to change the path to reflect Ubuntu rather than Windows.

e.g. The first one will now read: /home/yourusername/.openoffice.org2/user/registry/data/org/openoffice/Office/Recovery.xcu 

Hope that helps.

You will need to Ctrl+H so as to see hidden files,of course.

---

### Post by s3a on 2009-12-05
Thanks! It worked!

---

