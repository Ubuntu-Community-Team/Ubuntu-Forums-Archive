---
title: "alt+left arrow is not working"
date: 2010-04-05
forum: General Help
---

### Post by ryanfx on 2010-04-05
Hello all,

I was hoping you could give me some troubleshooting steps as to why my right alt+left arrow is not working as a "back" in firefox, however my left alt+left arrow works perfectly.

If you need code outputs, please let me know!

---

### Post by ryanfx on 2010-04-05
bump?

---

### Post by Iowan on 2010-04-05
Out of curiosity - does left alt+right arrow work for forward?

---

### Post by ryanfx on 2010-04-07
Yes, left alt + right array goes forward perfectly.  So I basically need to figure out how to map right alt to the same key ID as left alt? 

Not really sure how to go about this.

---

### Post by linden940 on 2010-04-07
do u have something in compiz that is using the left alt left arrow key? something to check

---

### Post by ryanfx on 2010-04-08
I'm not even running Compiz =/

How can I check key-mappings or change them?

---

### Post by lovinglinux on 2010-04-08
> **ryanfx said:**
> I'm not even running Compiz =/

How can I check key-mappings or change them?

It should be working. At least it works here with Firefox 3.6.3 on Lucid Linx.

Take a look at [this thread](http://forums.mozillazine.org/viewtopic.php?t=72994). I never used that tool, don't know if can be trusted, but the thread is on MozillaZine forums for a long time.

---

### Post by ryanfx on 2010-06-05
I just wanted to report I got this working using xev + xmodmap.

I found out the key was mapped to some goofy key so I changed it back to match what it should be with a simple script added to my user startup 

```

#!/bin/bash
xmodmap -e "keycode 108=Alt_R"
exit 0

```

---

