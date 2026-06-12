---
title: "Terminal &quot;mount&quot; command questions"
date: 2010-08-09
forum: General Help
---

### Post by fterh on 2010-08-09
1) Currently I'm sharing a Firefox profile with my Windows 7 O.S. (NTFS partition), so I have this entry in my fstab file:

```
UUID=5EB809D9B809B117 /media/windows7 ntfs defaults,sync 0 0
```

Are my options okay?

2) I was reading this [help page]("http://linux.about.com/od/commands/l/blcmdl8_mount.htm") and there are three mount syntaxes listed:

  **mount -a [-fFnrsvw] [-t ***vfstype***] [-O ***optlist***]**  
 **mount [-fnrsvw] [-o ***options*** [,...]] ***device ***|*** dir*  
 **mount [-fnrsvw] [-t ***vfstype***] [-o ***options***] ***device dir*


Out of curiosity I tried the 2nd one: sudo mount -o sync,ro /dev/sdb3 | /media/windows7 and it tells me: bash: /media/windows7 is a directory although /dev/sdb3 gets mounted anyway. So I'm guessing that syntax with the "|" is used in bash commands? Am I right?


 Anyway I tried it again with another partition (/dev/sdb5) and it says: mount: can't find /dev/sdb5 in /etc/fstab or /etc/mtab How come?


So these are my two questions :D Hope that the experts can enlighten me and clear my doubts :D

---

### Post by fterh on 2010-08-10
Bump.

---

### Post by Bachstelze on 2010-08-10
The | in the second syntax is not supposed to be typed literally. It means you specify either the device or the dir (| in some contexts means "or").

---

### Post by fterh on 2010-08-10
> **Bachstelze said:**
> The | in the second syntax is not supposed to be typed literally. It means you specify either the device or the dir (| in some contexts means "or").
Isn't or supposed to be ||? Just like &&?

---

