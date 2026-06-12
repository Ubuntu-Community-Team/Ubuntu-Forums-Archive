---
title: "Auto transfer of files upon external media plugin"
date: 2010-07-18
forum: General Help
---

### Post by davavanstone on 2010-07-18
Hey peeps,

Im after some help on some scripting in bash or maybe programming in c if u think it needs it?

I have a server in the attic that does loads of downloading, nzbs and torrents, ive set it up as a web server so my sister down the road can access it and add files to be downloaded from her place.  The reason for this is that she uses a revo with boxee to play the media but hasnt really got a manly enough connection to handle all the downloads.

Im after a script that uses the uuid of her external usb hard disk to recognize its hers and to copy all her files (already sorted into her own folder)from the server straight onto it.  
She can come to mine whenever, plug it in, it auto copies the files over (i dont want to have to ssh into the server and tell them to copy, i need her to be able to plug and go, she not too computer savvy bless her)

Any ideas on doing this?

The drives on the server that hold the said folder are mounted in fstab as its own drives on my revo downstairs all on gigabit, she can use this revos usb port as the "transfer" port.

---

### Post by davavanstone on 2010-07-19
bump

---

### Post by davavanstone on 2010-07-19
Got looking around, maybe rsync will work for this? i need it to be fully auto though and to play a sound on completion,

---

### Post by davavanstone on 2010-07-20
ok got rsync sorted, and to play an mp3 upon completion, ive put the script on the external drive as an autorun file, but why wont ubuntu load it? ive been through the nautilus settings and messed about with gconf-editor.  Googled everywhere but ubuntu doesnt want to load the autorun.  I know it can be seen as a security risk but not in this case.

---

