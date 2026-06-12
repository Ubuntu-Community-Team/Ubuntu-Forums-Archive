---
title: "ffmpeg version issues"
date: 2010-06-16
forum: General Help
---

### Post by inameiname on 2010-06-16
ffmpeg 0.6 just came out today: [http://linux.softpedia.com/get/Multimedia/Video/FFmpeg-3054.shtml](http://linux.softpedia.com/get/Multimedia/Video/FFmpeg-3054.shtml), and using checkinstall, I am able to successfully compile it into a deb file, and install it. However, when I update, the old ffmpeg (a higher version number for some reason) gets reinstalled.

Using aptpolicy:

aptpolicy ffmpeg
ffmpeg:
  Installed: 0.6-1
  Candidate: 4:0.5.1-1ubuntu1
  Version table:
     4:0.5.1-1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
 *** 0.6-1 0
        100 /var/lib/dpkg/status

Why does the version in the repos have a '4:' in front of it, preventing me from easily updating?

---

### Post by inameiname on 2010-09-08
This was solved a while ago. The version issue was updated just fine in a later version available in a PPA. Of course, with the latest ffmpeg, there is an issue with mencoder and mplayer not working for it, without a code fix, or an upgrade to 2:1.0-rc4. No biggie, as that was also found.

---

