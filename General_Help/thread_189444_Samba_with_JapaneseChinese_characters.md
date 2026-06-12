---
title: "Samba with Japanese/Chinese characters"
date: 2006-06-05
forum: General Help
---

### Post by stephen_lau on 2006-06-05
I've set up samba to share one of my HDDs with WinXP comps but it contains some folders/files which are in Japanese or Chinese characters. As a result, these folders/files do not get displayed under Windows, but the other folders are fine. So I'm wondering, is there some option that I need to set in smb.conf so that Samba can share folders which are in unicode?

---

### Post by blackjack6.21.91 on 2006-06-05
Are you sure it's not the Windows side that's at fault?

---

### Post by stephen_lau on 2006-06-05
No, because if I share the same HDD under Windows XP, the other computer sees everything fine...

---

### Post by stephen_lau on 2006-06-05
Got it working - I forgot to set the locale option in fstab when I switched over from the default ntfs to ntfs-fuse for write access, so the files/folders didn't get displayed

---

