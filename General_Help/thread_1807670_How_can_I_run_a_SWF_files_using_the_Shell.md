---
title: "How can I run a SWF files using the Shell ?"
date: 2011-07-19
forum: General Help
---

### Post by feinfadiges on 2011-07-19
People I have some SWF files in my Ubuntu and I want to run them using the Shell. I tried ./flashplayer myfile.swf (where flashplayer is the name of the player i have downloaded and myfile is the name of the swf movie) but i didn't work. Previously i tried the same shell command in Mandriva and it worked fine.

Since I am developing a PHP application i need to run those files by the Shell. So, how can I make it work (run the SWF files) in Ubuntu via Shell? Any solution is welcome

---

### Post by dino99 on 2011-07-19
gnash (gnome) & klash (kde) are swf readers, so your script might call one of them (search "swf" into synaptic)

---

### Post by mikejonesey on 2011-07-19
not sure about the link between php and shell... why do you need them to open using shell? (ie how will that help a php app).. ne ways...

try opening with firefox... (will load flash ext when file opended)
```
/usr/bin/firefox /home/foo/bar/myswf.swf
```

---

