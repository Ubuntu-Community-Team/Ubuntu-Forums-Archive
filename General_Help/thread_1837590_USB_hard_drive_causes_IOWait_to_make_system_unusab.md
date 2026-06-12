---
title: "USB hard drive causes IOWait to make system unusable"
date: 2011-09-02
forum: General Help
---

### Post by kwgivler on 2011-09-02
I believe that I am running into this bug:

[https://bugs.launchpad.net/ubuntu/+bug/786776](https://bugs.launchpad.net/ubuntu/+bug/786776)

"When attempting to write files to most USB drives, the system will bog down to 100% CPU on IOWait and about 12-18 system load. The larger the file, the worse the condition. Copying a 4.6GB disk image locks the system up for over 45 minutes to complete its task. This is on a 3.0GHz hyperthreaded I7. Ubuntu 10.10

The system should be able to handle this activity with minimal load and IOWait, and should never effect system performance."

I am using 11.04. Google seems to suggest that a handful of users are affected. I have not seen any solutions. I recently migrated from Gentoo hoping to have an easier to maintain desktop distro, and I did not have this problem under Gentoo.

Any help would be greatly appreciated. Thank you very much :)

---

