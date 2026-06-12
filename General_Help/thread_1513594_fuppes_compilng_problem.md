---
title: "fuppes compilng problem"
date: 2010-06-19
forum: General Help
---

### Post by CyberAxe on 2010-06-19
I've followed pretty much every guide and was able to compile the latest SVN but as that wasn't working I tried downloading the latest stable version from source forge and when I compile it the two errors I get are related to it are 

metadata_ffmpegthumbnailer.cpp:29:30: error: videothumbnailer.h: No such file or directory

metadata_ffmpegthumbnailer.cpp:30:24: error: imagetypes.h: No such file or directory

And i've isntalled all the dependancies i can find as well as both the ffmpegvideothumbnailers packages i saw on apt

any help would be appreciated, thanks

---

### Post by GAVtheRAV on 2010-06-19
Hi. Funnily enough I seem to be in exactly the same situation as you except I'm installing on Gentoo. I managed to get past the errors during the "make" process by installing an older version of ffmpegthumbnailer. Originally I had v2.0.2 installed but then dropped the version down to v1.5.4 and it worked. Not sure how you would go about this on Ubuntu but hopefully it will help you

---

### Post by GAVtheRAV on 2010-06-19
Also. What problem did you have with Fuppes SVN? When I tried to use it I couldn't get it to share any media with my Xbox 360

---

### Post by CyberAxe on 2010-06-19
> **GAVtheRAV said:**
> Hi. Funnily enough I seem to be in exactly the same situation as you except I'm installing on Gentoo. I managed to get past the errors during the "make" process by installing an older version of ffmpegthumbnailer. Originally I had v2.0.2 installed but then dropped the version down to v1.5.4 and it worked. Not sure how you would go about this on Ubuntu but hopefully it will help you

Unfortunatly there doesnt appear to be an older version on the repositories :/

> **GAVtheRAV said:**
> Also. What problem did you have with Fuppes SVN? When I tried to use it I couldn't get it to share any media with my Xbox 360

on the SVN i got it to show up on the xbox and showed some media but it couldnt transcode any video, the mp3s would show up as unsupported format on the 360 and pictures just wouldnt show up at all.

Originally it wasnt showing any media but i fixed that by rebuilding the folder layout by pressing v (though it might require rebuilding the database first)

---

### Post by CyberAxe on 2010-06-20
I remember a bug fix for something similar involved linking the h file it was trying to access to the one form the newer version of the lib being used which was a different name/location, but i cant find where the newer ffmpegthumbnailvewers .h file is

---

