---
title: "Dual boot Natty/Win7 - moving home to windows partiiton"
date: 2011-07-11
forum: General Help
---

### Post by Dr_Jez on 2011-07-11
I have been looking for an easy guide to this. 

I know it is possible to move the ubuntu home directory but what is the best way to move it safely to an NTFS partition that already has valuable data in?

I did this in a previous install, but the implementation was flaky, so I am hoping for advice!

---

### Post by 3Miro on 2011-07-11
Do you remember where you read the tutorial for this?

AFAIK NTFS and ext* have very different permission schemes and hence you cannot put /home on an NTFS partition (at least not without massive issues). I highly advise you to not do that.

If you can indeed move /home, then it should make no difference whether or not you already have data on it. Just don't reformat it.

---

### Post by seawolf167 on 2011-07-11
Just mirroring what 3Miro said, you cannot move /home from ext to NTFS. You probably could move the folders like ~/Videos, ~/Pictures because they don't have configuration files in them like ~ does, but still, it would be much easier IMO to leave them where they are.

---

### Post by dFlyer on 2011-07-11
As far as I know there is no best way to move /home to an NTFS partition. To do so would be entering permission hell.

---

### Post by Dr_Jez on 2011-07-11
No, I don't remember where the tutorial was, one of the reasons I am reinstalling from cold is that I was not sure how I had put everything together, this time I am keeping a better record. 

Thanks for the warning guys, guess I was following the wrong approach. It also explains why my previous version was so flaky!

So, how can I make ubuntu point to the already established music, videos and general data store on what windows calls D drive?

---

### Post by Bucky Ball on 2011-07-11
D: should appear in your File Manager once Ubuntu is installed (but it probably won't be called that). Just click on the partition and access the files.

---

### Post by nothingspecial on 2011-07-11
Open the parent folder in nautilus and right click each folder and choose "make link" (or something like that".

Then move the link to your home folder.

Or drag them over with Shift-Ctrl held down.

---

### Post by Dr_Jez on 2011-07-11
Thank you for all the advice.

Jez

---

### Post by ajgreeny on 2011-07-11
You probably need to make sure your D: drive, ntfs partition is mounted at boot in ubuntu either by using ntfs-config or by manually editing your /etc/fstab file.

That way all your data files, ie docs, videos, photos, music, etc etc will be available not only to windows, but also to ubuntu straight after boot up.

---

