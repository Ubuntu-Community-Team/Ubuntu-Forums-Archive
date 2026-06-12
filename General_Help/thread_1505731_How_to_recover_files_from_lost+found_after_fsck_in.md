---
title: "How to recover files from lost+found after fsck in Ubuntu"
date: 2010-06-09
forum: General Help
---

### Post by swamytk on 2010-06-09
Yesterday, My Ubuntu 10.04 was not able to boot, displaying “Continue to wait; Press S to skip mounting or M for manual recovery” due to file system error in / and /home partitions. I went ahead with Recovery boot option and run fsck on both / and /home file systems. / was OK. Then I had problem in getting fsck cleared for /home. Then I was forced to use “fsck -p /home” (automatic fixing) and “fsck -y /home” (select yes for all prompts automatically). After these run, /home passed fsck successfully. But the real stuff showed its face when I mount /home. None of my user files were there /home except lost+found directory....

I have written a small write-up on this link on how to I got back all files: [http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/)

Can Ubuntu make this process simple - user friendly way?

---

