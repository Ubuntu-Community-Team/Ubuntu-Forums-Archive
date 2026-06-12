---
title: "better backup than back in time? Back in time seems to not work in Ubuntu 12.04"
date: 2012-09-14
forum: General Help
---

### Post by 777funk on 2012-09-14
I'm looking for a good backup software. Is there one that's recommended? When I searched it seemed like Back in Time was recommended. I tried it and it kept failing in Ubuntu 12.04. Seems like there may be a problem there. Is there another one that's recommended? ... or a fix known for Bk in Time?

---

### Post by 2F4U on 2012-09-14
There are a couple of programs available such as Déjà Dup. You could also try to use a probably more recent version of Back In Time from the developer ppa (**ppa:bit-team/stable**). Since Back In Time is based on rsync, you could also use rsync directly.
I, for example, don't do backups in a classical sense. Instead, I use Unison to sync my data to separate hard disk.

---

### Post by HermanAB on 2012-09-14
+1 for DejaDup.

Nothing simpler in the GUI verse.  Underneath it uses rsync and if you would bother to read the rsync man page, then you'll see that a backup program on Linux amounts to a one line script and is quite trivial.

---

### Post by 777funk on 2012-09-14
> **2F4U said:**
> There are a couple of programs available such as Déjà Dup. You could also try to use a probably more recent version of Back In Time from the developer ppa (**ppa:bit-team/stable**). Since Back In Time is based on rsync, you could also use rsync directly.
I, for example, don't do backups in a classical sense. Instead, I use Unison to sync my data to separate hard disk.

Tried this and I don't believe BIT is working. It always gives a Failed To Take Snapshot message after a while. I was backing up a Link to a folder on my Windows drive. I will try selecting from the actual folder (not the link/shortcut) and see if that works... before I give up on Back In Time.

I'll try Deja Dup as well. Deja comes with Ubuntu correct? It's labelled "Backup"?

---

### Post by Old_Grey_Wolf on 2012-09-14
I install rsync then I install the grsync ([http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)) graphical front end for rsync. Works for me.

---

### Post by tea for one on 2012-09-14
> **Old_Gray_Wolf said:**
> I install rsync then I install the grsync ([http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)) graphical front end for rsync. Works for me.

Yes, indeed, I have been using Grsync for a thousand years.

The GUI is pretty easy to understand and the backend is rsync, which is a valuable Linux application

---

### Post by tornadof3 on 2012-10-15
Does grsync *synchronise* two sources, or merely do 'selective' copying? Unison is good as it can do full (bi-direction) sync, except unison has been causing me problems recently in that it does not detect some files that do indeed need syncing so I am left with outdated files. Has anyone come across this and know any possible causes?

---

### Post by Old_Grey_Wolf on 2012-10-15
> **tornadof3 said:**
> Does grsync *synchronise* two sources, or merely do 'selective' copying? ...

I could be wrong but I do not think it does bi-directional syncing. It does differential backups which is why I use it.

---

### Post by pompel9 on 2012-10-15
I use dejadup and sync it with Ubuntu One. Woks like a charm :)

And yes, it's is installed with Ubuntu and is called backup (I think, I do not have English as the OS language).

---

### Post by Lightstar on 2012-10-15
I use FreeFileSync.  Works on both windows and linux.
It can do mirroring.

I'm enjoying it a lot so far.  Reminds me of MS SyncToy that I used for awhile on my windows box.

[http://sourceforge.net/projects/freefilesync/]("http://sourceforge.net/projects/freefilesync/")

---

### Post by tornadof3 on 2012-10-29
Having just installed and tested FreeFileSync, it seems to work a treat and is getting all files properly! THanks for that idea

---

