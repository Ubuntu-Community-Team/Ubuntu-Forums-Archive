---
title: "where can i find the default Firefox Icon launch command?"
date: 2009-07-13
forum: General Help
---

### Post by eival on 2009-07-13
i recently installed 3.5 manually an i switched the command location for the icon to the new 3.5, but after noticing a few bugs with flash i want to switch it back so the icon loads the default firefox 3.11 again.
only problem is when i search my computer all the firefox and mozilla folders open 3.5 even the folder that says Firefox 3.11.


where would the launch/run file for the system managed version of Firefox be located?

im using Ubuntu 8.04

---

### Post by lovinglinux on 2009-07-13
To revert a launcher command, set it to:

```
firefox %u
```

This the path used by Firefox launcher by default. It should load Firefox 3.0.11. If it doesn't, then we might need to restore some symlinks. How did you install  Firefox 3.5? It would be better If you could provide the method you used to install Firefox 3.5, because they have differences.

---

### Post by eival on 2009-07-14
> **lovinglinux said:**
> To revert a launcher command, set it to:

```
firefox %u
```

This the path used by Firefox launcher by default. It should load Firefox 3.0.11. If it doesn't, then we might need to restore some symlinks. How did you install  Firefox 3.5? It would be better If you could provide the method you used to install Firefox 3.5, because they have differences.

that starts up 3.5 too.

i installed 3.5 using the tar package from mozilla.com then double clicked on the diamond(firefox) file an clicked Run.

that code you gave looks familiar but i think the original had something like ```
-f
``` in there somewhere


i know the original firefox is still on my OS an working cause i was using it along side 3.5, the only thing i changed was the command line for the Firefox Icon in my toolbar, so i shouldnt have to install anything again

---

### Post by ptn107 on 2009-07-14
On a 9.04 installation /usr/bin/firefox is a link to /usr/bin/firefox-3.0 which in turn is linked to /usr/lib/firefox-3.0.11/firefox.sh.

You can try:
```
sudo rm /usr/bin/firefox && sudo ln -s /usr/bin/firefox-3.0 /usr/bin/firefox
```

---

### Post by eival on 2009-07-14
> **ptn107 said:**
> 
You can try:
```
sudo rm /usr/bin/firefox && sudo ln -s /usr/bin/firefox-3.0 /usr/bin/firefox
```

THAT WORKED!!!

thanks:guitar::popcorn:

now i use Youtube again an the myspace java picture uploader wont lock up the browser.

---

