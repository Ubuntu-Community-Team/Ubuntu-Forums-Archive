---
title: "Ubuntu 10.10 is not booting up"
date: 2011-03-28
forum: General Help
---

### Post by Will F on 2011-03-28
So I am having the same trouble as is described here: [http://ubuntuforums.org/archive/index.php/t-1200023.html]("http://ubuntuforums.org/archive/index.php/t-1200023.html"). This occurred after I had been running my laptop off of a flash drive for a couple days and when I tried to boot it back up into the normal OS, it wouldn't work. So far what I have read, is that the best solution is to run $ e2fsck -fv /dev/sda5 to correct any errors. I have been able to mount the home directory and back up the encrypted data, however I have so far been unable to actually read the encrypted data. I have followed [this]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live CD method of opening a encrypted home directory") as well as [this]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html"), but have not had any luck reading my files.

I really have three questions. First, how can I easily access my encrypted files via the command line? Second, will running e2fsck erase all of my data? I have had limited experience with this tool and am unsure of whether or not it is a viable solution. Third, this is a problem that has now happened 3 times to me. I fixed the first with e2fsck, the second I had to reimage the hard drive, and now this is a third. Why does this happen and will it keep happening? If it does I don't know if I can continue to use Ubuntu unfortunately.

---

