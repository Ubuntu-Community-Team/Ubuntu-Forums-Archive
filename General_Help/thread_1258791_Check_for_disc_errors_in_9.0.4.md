---
title: "Check for disc errors in 9.0.4?"
date: 2009-09-05
forum: General Help
---

### Post by probedb on 2009-09-05
Hi folks,

I run sabnzb+ for usenet stuff and it keeps reporting disc errors when downloading sometimes.

I'm running an Acer Revo and it's only 3 months old so not convinced it's disc errors.

How do you do disc checks? In Windows I'd just tell it to do a chkdsk at the next boot?

I don't have any GUIs running, it's purely bash.

Ta :)

Paul.

---

### Post by ssulaco on 2009-09-05
Ubuntu does a diskcheck I believe the 30th boot........you can force a fsck (file sys check) to be run on next boot.

$ sudo touch /forcefsck

---

### Post by probedb on 2009-09-06
Cheers for this but it doesn't seem to have done anything :(

Ran that command then

```
sudo shutdown -r now
```

but it just did a normal reboot?

---

### Post by ssulaco on 2009-09-06
Sorry....drop the $ .....

```
sudo touch /forcefsck 
```

as you are root,you should be prompted for your password........reboot

---

### Post by probedb on 2009-09-07
Yep I know $ is the prompt ;)

Still didn't do anything...does it put logs anywhere?

---

### Post by ssulaco on 2009-09-07
Not sure about logs....check these links out
[http://spsneo.com/blog/2008/07/13/how-to-force-fsck/](http://spsneo.com/blog/2008/07/13/how-to-force-fsck/)
[http://embraceubuntu.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://embraceubuntu.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)
[http://ubuntuforums.org/showthread.php?t=308956](http://ubuntuforums.org/showthread.php?t=308956)

try this,

```
sudo touch /forcefsck && reboot
```

Ive tried both commands and they work.

---

### Post by Sidewinder1 on 2009-09-07
I've never tried it, but I read that "really bad things can happen" if you run fsck on a MOUNTED drive. Perhaps that has been fixed in later versions of ubuntu, but I'd make certain it's UNMOUNTED first, just to be safe.
HTH,
Side

---

### Post by capscrew on 2009-09-07
> **Sidewinder1 said:**
> I've never tried it, but I read that "really bad things can happen" if you run fsck on a MOUNTED drive. Perhaps that has been fixed in later versions of ubuntu, but I'd make certain it's UNMOUNTED first, just to be safe.
HTH,
Side

The partitions are not mounted (yet) on booting (or rebooting) when the fsck is performed.  It will not be a problem.

[**_[COLOR="DarkSlateGray"]Here[/COLOR]_**]("http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/") is some additional information.

---

### Post by probedb on 2009-09-08
> **ssulaco said:**
> Not sure about logs....check these links out
[http://spsneo.com/blog/2008/07/13/how-to-force-fsck/](http://spsneo.com/blog/2008/07/13/how-to-force-fsck/)
[http://embraceubuntu.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://embraceubuntu.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)
[http://ubuntuforums.org/showthread.php?t=308956](http://ubuntuforums.org/showthread.php?t=308956)

try this,

```
sudo touch /forcefsck && reboot
```

Ive tried both commands and they work.

Watched it reboot this time, worked a treat so big thanks :)

---

