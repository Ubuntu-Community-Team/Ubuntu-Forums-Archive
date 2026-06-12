---
title: "Wrong Disk Usage report"
date: 2012-02-07
forum: General Help
---

### Post by Kmels on 2012-02-07
Hello, and thanks in advance for the help. What could be the reason of the following, and how can one fix it?

> kmels@kmels-stelle:~$ du -sh ~/
48G	/home/kmels/


> kmels@kmels-stelle:~$ du -sh ~/*
97M	/home/kmels/bin
807M	/home/kmels/code
196K	/home/kmels/Desktop
4.0K	/home/kmels/Documents
42M	/home/kmels/Downloads
1.5G	/home/kmels/Dropbox
12K	/home/kmels/#.emacs.adf#
4.0K	/home/kmels/examples.desktop
268K	/home/kmels/IMG_06022012_155647.png
408K	/home/kmels/IMG_06022012_155909.png
256K	/home/kmels/IMG_06022012_160133.png
4.0K	/home/kmels/Music
60K	/home/kmels/package.cache
772K	/home/kmels/Pictures
4.0K	/home/kmels/Public
4.0K	/home/kmels/Templates
192M	/home/kmels/tmp
8.0K	/home/kmels/Videos

Yes, you might think: what about hidden files?

I ran 

> find ~/ -type d -exec du -ks '{}' \; | sort -rn > ~/report


and checked there were no *big* files.

Also, I'm attaching a screenshot from Ubuntu's Disk Usage, where the sub directories of ~/ are sorted by size.

Thanks again.

---

