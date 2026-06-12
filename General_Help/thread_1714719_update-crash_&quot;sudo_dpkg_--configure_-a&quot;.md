---
title: "update-crash &quot;sudo dpkg --configure -a&quot;"
date: 2011-03-25
forum: General Help
---

### Post by aldyguy on 2011-03-25
I was doing an update and it froze, so I rebooted and I tried opening the manager again and I got 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." 

So I ran that in terminal and got this
dpkg: parse error, in file '/var/lib/dpkg/updates/0230' near line 0:
 newline in field name `#padding'


I need help with this :p


so I went into the file itself and it's just a bunch of #padding lines, the files above 0230 are transparent. Is there a terminal code I can do to just remove 0230 and the ones that follow it? I tried just deleting it but it wouldn't allow me.

---

