---
title: "e2fsck fails device or resource busy"
date: 2011-03-03
forum: General Help
---

### Post by weekender on 2011-03-03
I thought that I would share this fix.

My son's netbook with 10.10 netbook remix failed to boot. Using the Live install CD and Gparted I couldn't repair the EXT4 filesytem. The error reported was:

e2fsck : Device or resource busy while trying to open ...

After trying many solutions and web searching I decided to try a different live CD and tried Knoppix 6.4.4

Using the command interface I typed e2fsck -v -f -y /dev/xxxx
(xxxx = your device). This worked first time and the machine rebooted without hesitation.

Hope this helps,

Andy

---

### Post by Ooh boon two on 2011-03-17
Out of curiosity, what did you try beforehand (Netbootin or the standard liveCD?).  I'm not very computer savvy, but I'll try Knoppix.

---

