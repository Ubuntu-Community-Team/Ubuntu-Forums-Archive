---
title: "Transmission BitTorrent --&gt; stopped at 97% and only seeding"
date: 2009-08-31
forum: General Help
---

### Post by Ezipan on 2009-08-31
I've been downloading torrent file using Transmission BitTorrent Client, and after a while the progress stopped suddenly at 97% (21 MegBytes to go).

I'm not pulling any bit any more while the only thing i'm doing is seeding to peers !

is it related to "Ratio" values because it happened to be 0.1 only.


many thanks

---

### Post by stefangr1 on 2009-08-31
This is a problem that is quite common with bittorent. When you start downloading, every peer can upload to you. For the last part, however, there are only a few seeders that have the data you need available. These long term seeders usually share a lot of different files, which diminishes overall speed.

---

### Post by Vaphell on 2009-08-31
also check what is the availability of the torrent in question. If it's < 1 and there are no seeds then it means that people can't finish downloading because some parts of it are missing - no peer has them (in your case it would be 3%, availability of 0.97).
availability indicates if you can form full torrent from the chunks from all people you are connected to.

---

### Post by Ezipan on 2009-08-31
hey
I figured out the principal cause behind it. 

When I started downloading the file, I excluded some French subtitle (guess what? it's 21 MegByte) among the files and chunks to be downloaded. 

All files were downloaded fully including the video file itself. However, the excluded subtitle was taken into account in terms of the overall percentage of progression. In other words, it was not downloaded as per the selection of files I made but was included in terms of completion percentage though! 


on the same line I want to ask Vaphell what do you mean by checking/verifying the availability and how do I do it?

---

