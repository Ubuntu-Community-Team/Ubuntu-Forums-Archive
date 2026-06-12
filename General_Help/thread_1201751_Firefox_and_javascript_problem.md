---
title: "Firefox and javascript problem"
date: 2009-07-01
forum: General Help
---

### Post by LakesideLoafer on 2009-07-01
I am running Ubuntu Netbook Remix 9.04 on an Acer Aspire One. Suddenly, I am experiencing problems with Firefox. I haven't made any changes to it and cannot think what might have caused the problem.
I get an error message
> Exception..."Component returned failure code 0x80570016
I suspect that this is because Speed Dial is my home page. If I change the home page I no longer get the message but the other problems persist. I have no bookmarks, no history, cannot navigate backwards and forwards.
Tried reinstalling Sun Java - no change. How do I reinstall OpenJDK? Any other ideas?

---

### Post by LakesideLoafer on 2009-07-02
Solved! Had a look around some other forums and it is a Firefox issue across all operating systems. In case anyone else has the same problem, locate the go to Home/.Mozilla/Firefox and delete the profiles.ini file and restart Firefox. Lost all my bookmarks and history but all working now. :p

---

