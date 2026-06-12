---
title: "anyone using jungledisk? problems?"
date: 2010-10-13
forum: General Help
---

### Post by undecidable on 2010-10-13
Am testing the Network Drive feature of Jungledisk.
Whenever I browse to a Jungledisk directory with konqueror, dolphin or krusader,
or the file open dialog of programs like kpdf
jungledisk downloads all the files in that directory to the local cache
(which really makes it unusable)
However an ls -lpa does not cause this.

Jungledisk support say the kde programs
whenever they browse to a directory
are issuing open()'s on the files in that directory to the fuse filesystem
so it is not their problem.

Anyone have any experience with Jungledisk?
Are you seeing the same problem?
does the gnome desktop have the same problem?



Using Kubuntu 8.04
kde 3.5.9

---

### Post by undecidable on 2010-10-16
Well I have the answer
and it is as surprising as it is unhelpful.
(cf Ringworld - location of Nessus' homeworld)

Konqueror, Dolphin and Krusader to display the file type or icon
have to "open" the file to read the "magic no." showing file type.
But to open a file, must download it first.

And these browsers have no view mode that doesn't require knowing the filetype.
I am guessing it is the same for Nautilus.

This is a serious gotcha for using cloud services.

Of course you can use the backup/restore features of Jungledisk (et al) 
but this is not as flexible as the network disk feature.

The workaround is to use Midnight Commander in a command window,
which doesn't force a file download.  

fwiw I am currently using Dropbox, using and & paying for SpiderOak and testing Jungledisk.  
Why not Ubuntu One?  No KDE support!
The above 3 all have gui clients that work perfectly in Kubuntu,
and SpiderOak even has a v functional cli interface.

---

