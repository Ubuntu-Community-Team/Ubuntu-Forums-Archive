---
title: "Gladinet replacement?"
date: 2010-04-02
forum: General Help
---

### Post by weavermount on 2010-04-02
Hello I was looking at getting more than 2 gigs of cloud storage some where and the only options cheap enough for me are Google (80gigs at $20/year) and Microsoft(wtf 25 gigs free). The trick with those services though is that you have to manually upload and manage files; you can't just upload and existing file structure. Gladinet is client for a bunch of clouds that gives you a powerful enough interface to actually use-up 25 gigs .... and windows only, and I haven't found a replacement.

So does anyone know of a way to get cloud storage set up with:
1) Ubuntu
2) $30/year (or less)
3) 20 gig (or more)
4) Upload whole directories/Preserves files structure

thanks all

---

### Post by searchfgold6789 on 2011-01-20
I too am looking for a way to mount my skydrive thingy. I really hope that the Wine Appdb gets some info on Gladinet soon, at least.
Bump

---

### Post by marli2 on 2011-01-25
maybe this might help?
[http://www.groovypost.com/howto/microsoft/windows-7-map-network-drive-live-skydrive-using-office-2010/](http://www.groovypost.com/howto/microsoft/windows-7-map-network-drive-live-skydrive-using-office-2010/)
if win7 can do it I assume linux can.

Maybe sombody can extend this for linux, or even better re-write it so that windows isnt needed to find the path.

---

### Post by marli2 on 2011-01-26
seems this is MSdavfs(or thats what in calling it)
a special B'stard child of webdav
i just spent 4 hr with mount.davfs and i still cant get in.

---

### Post by ST3ALTHPSYCH0 on 2011-04-06
I spent a good bit of time working with this the other day.
I found a workaround. It uses FUSE, but I've not seen any instability:
[http://www.fuduntu.org/forum/viewtopic.php?f=13&t=466](http://www.fuduntu.org/forum/viewtopic.php?f=13&t=466)

Don't worry, they have .deb packages too.

EDIT:
Just realized I necrobumped a 3 month old necrobump, but it didn't appear to be solved, and it was in the top 5 returns on "Skydrive". PS, OP, this can be marked [Solved], promise.

---

### Post by buyucu on 2011-12-24
Try SMEstorage. It gives you free 2GB S3 space and additionally 2 more providers ... such as SKYDRIVE, DROPBOX ... and many more.

Looks similar to gladinet. I'm trying sme at the moment. Looks good.

---

### Post by nothingspecial on 2011-12-24
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

