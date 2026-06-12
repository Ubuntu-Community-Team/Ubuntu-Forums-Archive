---
title: "Can't stop &quot;.xsesseion-errors&quot; file from getting huge.(1gb &amp;+)"
date: 2011-01-30
forum: General Help
---

### Post by Grizzil on 2011-01-30
Can't stop ".xsesseion-errors" file from getting huge.(1gb &+)
My .xsession.errors keep getting huge.
I try for a few hours to get rid of the ".xsession-errors" file in my home directory for good but without success, He keeps coming back so I roam the Internet in search for a cure for this plague but my limited linux skills kept me from acheiving my goal, so now this little beast rest in peace in my /home directory growing slowly but surely.

I already try to edit the "/etc/X11/Xsession" file replacing "$HOME/.xsession-errors" line with "/dev/null"

I also try adding
```
#!/bin/bash 
ln -sf /dev/null $HOME/.xsession-errors
rm /home/prodigy/.xsession-errors
rm /home/prodigy/.recently-used.xbel
```

in the boot.local file

Tanks in advance for your help

ubuntu 10.10 amd64
gnome + compiz

---

