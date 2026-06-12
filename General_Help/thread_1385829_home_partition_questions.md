---
title: "/home partition questions"
date: 2010-01-20
forum: General Help
---

### Post by Crowchild on 2010-01-20
For a few years I've kept a separate partition for my home folder and have found that to pretty useful as I mess around and occasionally need to reinstall Ubuntu. Now, I'd like to branch out and try a few other distros and don't want to have the ./* folders messing with my installation.

How I go about creating symbolic links from my new home folder which is on the / partition to the Music, Documents, Pictures folders on what used to be my home partition?

And, do you think this is the proper way to go about this?

Thanks.

---

### Post by pmlxuser on 2010-01-20
simple just delete your current music folder and then do
```

$ln -s /path-to-old-home-music-folder  Music

```

this will work if you have wrxwrx right to that folder from your current distro.

---

### Post by Barriehie on 2010-01-20
> **Crowchild said:**
> For a few years I've kept a separate partition for my home folder and have found that to pretty useful as I mess around and occasionally need to reinstall Ubuntu. Now, I'd like to branch out and try a few other distros and don't want to have the ./* folders messing with my installation.

How I go about creating symbolic links from my new home folder which is on the / partition to the Music, Documents, Pictures folders on what used to be my home partition?

And, do you think this is the proper way to go about this?

Thanks.

It should work like any other link! :) As a test I'ld rename the current Pictures > Pictures.old and then:
```

ln -s /current_pictures_folder /home/username/Pictures

```

I've discovered, as you have, that having a seperate home partition is a GOOD idea!  I think you have a workable plan.
HTH,

---

