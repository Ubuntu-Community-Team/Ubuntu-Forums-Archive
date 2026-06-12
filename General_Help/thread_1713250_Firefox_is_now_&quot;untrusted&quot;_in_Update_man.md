---
title: "Firefox is now &quot;untrusted&quot; in Update manager. (Want to switch back to Stable release)"
date: 2011-03-23
forum: General Help
---

### Post by tdr2009 on 2011-03-23
Ok.
I accidentally messed up my keys for Firefox (I wanted to download the dailies, but now don't want to). Now, when I want to update, it won't even download the dailies either, it says it is "untrusted". I want to get everything back to normal, where it will stop downloading the dailies and return to the stable releases. I think I added these keys manually, because none of the Pre-Release options are checked in the Settings menu in update manager.
Please please help!!!! 
I see now how I mess up stuff when playing with Ubuntu lol.
I have Ubuntu 10.10.

---

### Post by lovinglinux on 2011-03-23
Disable the firefox ppa in the software sources, then run this:

```
sudo apt-get update
sudo apt-get install --reinstall firefox
```

---

### Post by tdr2009 on 2011-03-23
> **lovinglinux said:**
> Disable the firefox ppa in the software sources, then run this:

```
sudo apt-get update
sudo apt-get install --reinstall firefox
```
Thanks. Before you replied, I found a way to upgrade to stabe version of Firefox 4, but I hope your code makes it only download stable updates from mozilla instead of the dailies. If not, is their a way to fix that?

---

### Post by lovinglinux on 2011-03-23
> **tdr2009 said:**
> Thanks. Before you replied, I found a way to upgrade to stabe version of Firefox 4, but I hope your code makes it only download stable updates from mozilla instead of the dailies. If not, is their a way to fix that?

See [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247) for instructions on how to upgrade Firefox using the stable ppa.

If you are using firefox-next, mozilla-daily or mozilla-security, then you need to disable the ppa and reinstall Firefox using the firefox-stable ppa.

---

### Post by tdr2009 on 2011-03-23
> **lovinglinux said:**
> See [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247) for instructions on how to upgrade Firefox using the stable ppa.

If you are using firefox-next, mozilla-daily or mozilla-security, then you need to disable the ppa and reinstall Firefox using the firefox-stable ppa.
That's the EXACT same one I used for Firefox 4 stable. Wow, I think I just noticed I had my question answered myself ](*,)
Thanks for helping though :D

---

