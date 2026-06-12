---
title: "Ext3 or Reiserfs"
date: 2006-05-23
forum: General Help
---

### Post by wizzkid on 2006-05-23
Guys, I would to know youe input with regards to filesystem. Ext3 or Reiserfs?

Last year, I used ext3, it works fine and does force fsck on every 30 reboots, and even i can manually force fsck by type sudo touch /forcefsck. However, i manage to mess up the system, well, you know a beginner linux user. When I re-install the whole system, I found out that I can use reiserfs instead of ext3, so I took the opportunity of trying it, so far its good, but i havent notice any difference, since Im using this only for my desktop and I dont really transfer lots of files. Unfotunately, I cannot figure out how to fsck my drives/ partition. its been 5 months and I havent really scan the drive for error, so far this is what bugs me now, othewise its a good OS. There are some issues on my kubuntu now, but its not in my concern as of yet. 

If somebody knows how to fsck on reiserfs, please do teach me how. 

Thanks for reading guys.

---

### Post by deanjm1963 on 2006-05-23
you don't need to fsck with reiserFS, thats what the journal is for, reiser will check the file system if there's problems on boot and its very quick, not like ext3. XFS is even better still, fast as lightening on checking the disk on boot up after hitting the reset button or pulling the plug.

---

### Post by wizzkid on 2006-05-23
sounds good! is there a way to convert my reiserfs to XFS? :) 

thanks

---

### Post by CitizenKane on 2006-05-23
I found a guide for converting from reiser to XFS.  I don't have a way to try it right now but you can give it a try!

[http://www.chesh.com/neil/reiserfstoxfs.html](http://www.chesh.com/neil/reiserfstoxfs.html)

---

### Post by Bandit on 2006-05-24
I noticed XFS being slow on Kubuntu Flight6.
I know on SuSE 10.1 it was lightning fast.
Never tried ReiserFS on Kubuntu, but I do know on SuSE that is was always slow to me.
But to me so far Ext3 is faster then XFS on Kubuntu Dapper.
Me running RAID0 might having something to do with it, but it was slow.
Hopefully XFS runs well for you. Its worth a try anyway.
I recomend trying all of them out when ever you can and then choosing which runs best.

Cheers,
Bandit

---

### Post by wizzkid on 2006-05-25
Thanks a lot guys :)

---

### Post by heatvent on 2006-06-06
I have tried reiserfs, but it's kinda noisy (very clicky type noise) on my Maxtor hard drive, so I went back to ext3.

---

### Post by az on 2006-06-06
[QUOTE=deanjm1963]you don't need to fsck with reiserFS, thats what the journal is for, reiser will check the file system if there's problems on boot and its very quick, not like ext3. XFS is even better still, fast as lightening on checking the disk on boot up after hitting the reset button or pulling the plug.[/QUOTE]
Ext3 is also journaled.  Otherwise it would just be ext2.

You still need to check reiserfs, it just is not set up by default to do it automatically like ext3 is.

---

