---
title: "cleaning custom installs"
date: 2010-04-28
forum: General Help
---

### Post by jeanlucmalet on 2010-04-28
Hi!
I've done some mistake while trying to activate x264 support in kdenlive.... 
I rebuilded ffmpeg to fit my needs and since kdenlive didn't detected the x264 codec, even using LD_LIBRARY_PATH, I decided to install it in place of ffmpeg (ie build with ./configure --prefix=/usr ....) but I learned that if you proceed like this further ubuntu upgrade won't update the ffmpeg package because it will detect that the package has modified files.....

1) is there a way to detect untracked files (that might be installed by a manual rebuild)
2) is there a way to detect modified files and force the re-installation of the package?

thanks and regards
JL

---

