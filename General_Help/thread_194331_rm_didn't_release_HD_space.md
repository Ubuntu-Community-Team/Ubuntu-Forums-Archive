---
title: "rm didn't release HD space"
date: 2006-06-11
forum: General Help
---

### Post by Kimppa on 2006-06-11
Hi.

I had two dvd-images on my computer, they were called filename.iso and filename.nrg
I wanted to remove these two files, so I ran the following command "rm filename*"
The files were removed in the sence that they didn't show up anylonger with "ls -al", however, any hard disk space wasn't released!?
So I just removed 9 GB worth of data, but still have only 300 MBs free space left on the same HD. How is this possible, more important, how can I fix it (release the space)?

There weren't any other operations running and the HD is only for file storage, so it couldn't have been filled with some other data - not that it would have even been possible in just a few seconds.

Thanks in advance

- Kimppa

---

### Post by konradsa on 2006-06-11
[QUOTE=Kimppa]Hi.

I had two dvd-images on my computer, they were called filename.iso and filename.nrg
I wanted to remove these two files, so I ran the following command "rm filename*"
The files were removed in the sence that they didn't show up anylonger with "ls -al", however, any hard disk space wasn't released!?
So I just removed 9 GB worth of data, but still have only 300 MBs free space left on the same HD. How is this possible, more important, how can I fix it (release the space)?

There weren't any other operations running and the HD is only for file storage, so it couldn't have been filled with some other data - not that it would have even been possible in just a few seconds.

Thanks in advance

- Kimppa[/QUOTE]

Check your recylce bin (GNOME desktop) and ./Trash, empty both.

---

### Post by Kimppa on 2006-06-11
Yup, both are empty. Actually, I was in KDE when this happened, but I was using terminal so will it make any difference?

When I logged out from KDE and into GNOME, some space was released (4,5 GB = one image). But I'm still missing another 4,5 GB

---

### Post by ayoli on 2006-06-11
maybe you can have a look to du's (console tool to display disk usage) output with a line like this:

du --max-depth=4 -b | sort -r -n | more

---

