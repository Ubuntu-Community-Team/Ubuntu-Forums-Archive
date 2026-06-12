---
title: "Brasero disk burner not working?"
date: 2009-09-18
forum: General Help
---

### Post by gismo93 on 2009-09-18
So I used brasero disk burner today as I don't burn many cd's.

I wanted to burn roughly 12 songs to a blank disk so opened up brasero and the interface was fairly simple.

I clicked on create audio project and selected all my songs and such, and clicked burn.

It started "normalizing tracks" but keeps doing this for about 2 hours now without any noticeable progress?

---

### Post by The Cog on 2009-09-18
Try k3b instead. It's my "Old Faithful".

---

### Post by TUXOR21 on 2009-09-19
> **gismo93 said:**
> So I used brasero disk burner today as I don't burn many cd's.

I wanted to burn roughly 12 songs to a blank disk so opened up brasero and the interface was fairly simple.

I clicked on create audio project and selected all my songs and such, and clicked burn.

It started "normalizing tracks" but keeps doing this for about 2 hours now without any noticeable progress?

I have exactly the same problem :(

---

### Post by TerryHowe on 2009-09-19
I never had a problem with Hardy Heron, but Brasero doesn't seem to work anymore with Jaunty.  I just noticed, I don't burn CDs often.  Anyone know anything?

---

### Post by TerryHowe on 2009-09-19
K3b does work nice.

---

### Post by SuperSonic4 on 2009-09-19
k3b has never chucked up a problem for me. Plus it has an excellent little noise when it finishes xD

---

### Post by The Cog on 2009-09-20
> **SuperSonic4 said:**
> k3b has never chucked up a problem for me. Plus it has an excellent little noise when it finishes xD

That tune doesn't play for me on Jaunty. It's configured to, but no sound comes out. I hope it starts working again in Karmic.

---

### Post by SlugSlug on 2009-09-20
same problem here, I too use k3b

---

### Post by wjwh on 2009-10-19
> **TerryHowe said:**
> I never had a problem with Hardy Heron, but Brasero doesn't seem to work anymore with Jaunty.  I just noticed, I don't burn CDs often.  Anyone know anything?

I would like to echo this comment.  I have made a video DVD iso file from with DeVeDe and burned it to a disc (DVD-R) using Brasero in Ubuntu 9.04.  The resultant DVD doesn't play properly on my DVD player.  It plays for about 10 seconds, then stalls for about 20 seconds, then plays (with the 20 second gap) for another ten seconds, then hangs again for 20, and so on.  This seems to me to be a Brasero problem in 9.04.  I have taken the same iso file to my old 8.04 setup and the older Brasero burns it perfectly.

Another feature of the new Brasero is that the disc which it produces isn't recognised by a computer operating Windows media Player.

---

### Post by sdowney717 on 2009-10-19
there is always nero linux

[http://www.nero.com/enu/downloads-linux4-trial.php](http://www.nero.com/enu/downloads-linux4-trial.php)

---

### Post by claracc on 2009-10-19
You have to untick the extension (i don't know the exact name in english, perhaps complement) Normalization. Brasero Menu, edit, extensions (or complement) and untick the normalization.

After it brasero will burn the songs.

Regards

---

### Post by wjwh on 2009-10-27
> **wjwh said:**
> I would like to echo this comment.  I have made a video DVD iso file from with DeVeDe and burned it to a disc (DVD-R) using Brasero in Ubuntu 9.04.  The resultant DVD doesn't play properly on my DVD player.  It plays for about 10 seconds, then stalls for about 20 seconds, then plays (with the 20 second gap) for another ten seconds, then hangs again for 20, and so on.  This seems to me to be a Brasero problem in 9.04.  I have taken the same iso file to my old 8.04 setup and the older Brasero burns it perfectly.

Another feature of the new Brasero is that the disc which it produces isn't recognised by a computer operating Windows media Player.

It appears that I was blaming Brasero wrongly.  I have installed k3b and it gives exactly the same result.  So, the problem must be with Ubuntu 9.04 or with my system - Intel core 2 Quad Q8200 CPU, 2.33GHz: Geforce nVidia 9400 GT Graphics card: LG SATA 20 speed dual layer DVD burner: Seagate Sata 1Tb HDD: 4GB RAM

---

### Post by NFblaze on 2009-10-27
Use K3b. Unfortunately Brasero, has never been that good. Even today when I used it in 9.10 Beta it locked up my eject button on my tray when I canceled an in-progress burn. I've never had an issue with k3b.

---

### Post by wjwh on 2009-10-28
> **NFblaze said:**
> Use K3b. Unfortunately Brasero, has never been that good. Even today when I used it in 9.10 Beta it locked up my eject button on my tray when I canceled an in-progress burn. I've never had an issue with k3b.

As I said in my previous post, I have exactly the same problems when using K3b as I have using Brasero!

---

### Post by editrix on 2009-10-28
If you search Launchpad, you'll find that there have been many, many bugs regarding CD/DVD burning since they switched to using wodim, I think back in Hardy or earlier. I posted about this here:
[http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700)
**How to burn a CD (and DVD) despite bug #149076**

The upshot of which is to use ImgBurn under Wine.

---

### Post by wjwh on 2009-11-05
It would be interesting to know what sort of drive is being used in these cases where Brasero, ksb, etc., don't work properly.  From what I have seen on searching the various forums, in almost every case where the type of drive is mentioned it is an LG drive.  Do we have a problem here, not in the burning software, but in the driver being used for the LG DVD/CD writer?

---

### Post by editrix on 2009-11-06
> **wjwh said:**
> It would be interesting to know what sort of drive is being used ... Do we have a problem here, not in the burning software, but in the driver being used for the LG DVD/CD writer?

According to sudo lshw -C disk:

  *-cdrom:0
       description: CD-R/CD-RW writer
       product: CW078D CD-R/RW
       vendor: CyberDrv
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 150E
       serial: 3CyberDrvCW078D CD-R/RW  150EO
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open

I don't think the driver is the main culprit (although anything's a possibility). The many, many bug reports mention several brands of cd burner.

---

### Post by wjwh on 2011-07-20
> **wjwh said:**
> It would be interesting to know what sort of drive is being used in these cases where Brasero, ksb, etc., don't work properly.  From what I have seen on searching the various forums, in almost every case where the type of drive is mentioned it is an LG drive.  Do we have a problem here, not in the burning software, but in the driver being used for the LG DVD/CD writer?

After nearly two years I have finally found that my particular problem was probably due to faulty hardware.  A few nights ago, my LG DVD/CD writer went on fire (literally!  There were flames coming out of it).  Fortunately nothing else seems to have been damaged and the replacement optical drive burns DVDs perfectly with Brasero.  So, the problem seems to have been a faulty drive!

---

