---
title: "Accidentally deleted /lib/"
date: 2010-11-09
forum: General Help
---

### Post by Josh96 on 2010-11-09
Well, I was being stupid, and while trying to install linux to my wii, I deleted the /lib/ folder by accident using rm -r. :( Is there anything I can do to get it back? Will I have to reinstall, and if I do, can I make a list of my currently installed files to install them later?

Thanks from a dumb noob.

---

### Post by WorMzy on 2010-11-09
A reinstall would be the safest option. You could, however, try booting from a LiveCD and copying it's /lib/ onto your Ubuntu partition. That should, in theory, make your system usable. After that, try booting into the partition and running

```
sudo apt-get check
```

Please note that I have no idea whether this would work or not; but, to my knowledge, the contents of /lib/ very rarely change.

---

### Post by Ancanus on 2010-11-09
And for future cases, you might want to make an alias of rm to rm -i so it prompts you every time.

---

### Post by WorMzy on 2010-11-09
Oh, I'd recommend that you make a backup of any important files before trying the LiveCD copy approach. Just in case something goes drastically wrong. Which is a possibility.

---

### Post by alphaamanitin on 2010-11-09
Just to let you know I did this awhile back...  Nothing I did was able to recover the lost install and I had to reinstall.  Though I believe I did have the drive encrypted so that might have complicated things.  If you are like me you lost so much it was impossible to rebuild. The steps I followed for recovery a Ubuntu install did not work-mounting the old drive using a liveCD and trying to chroot and rebuild-FAILED.

AlphaA

---

