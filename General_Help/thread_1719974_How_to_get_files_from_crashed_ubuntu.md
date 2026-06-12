---
title: "How to get files from crashed ubuntu?"
date: 2011-04-02
forum: General Help
---

### Post by Waidas on 2011-04-02
My ubuntu not booting up. How can I get files from home directory?

---

### Post by oldfred on 2011-04-02
Is this an install to a partition or wubi inside windows. Can it be repaired?

Post this so we can see, if it is just a boot issue.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Waidas on 2011-04-02
I have big problem. It's installed to a partition. While booting shows an error: ```
An error occurred while mounting /media/6092-594B
```. There are two options : ```
Press S to skip mounting or M for manual recovery
```. I have tried press S, but nothing happens.

Showing that code:
```
fsck from util-linux-ng 2.17.2
/dev/sda7: clean, 366872/2943360 files, 9301096/11765248 blocks
init: unreadahead-other main process (843) terminated with status 4
init: unreadahead-other main process (848 ) terminated with status 4
mount: /media//6092-594B not mounted already, or bad option
mountall: Filesystem could not be mounted: /media/6092-594B
Skipping /media/6092-594B at user request
```


And nothing happening further.
That problem made mountmanager application. It changed configuration file

---

### Post by oldfred on 2011-04-02
Is this an external drive or why are you mounting in /media? Is it NTFS not Linux format? What is the partition. 

UUID looks more like a NTFS, if so run chkdsk from a windows repair CD.

---

