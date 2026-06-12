---
title: "RDP to Windows and umlauts"
date: 2011-12-08
forum: General Help
---

### Post by matunaator on 2011-12-08
When trying to connect to a Windows server by RDP (tsclient or remmina) I get combinations of characters instead of the umlauts i have typed, the layout i'm using is "ee".
Ö becomes ";O", Ä "'A", Ü "[U" and Õ "]O".
Changing the keyboard mapping from common to other mappings does not solve this problem.
Is there anything else i can try?

---

### Post by lukeiamyourfather on 2011-12-08
I've used rdesktop to connect to Windows machines before without issue. Though I've not used characters with umlauts during a session. It sounds like a fairly specific issue, if you don't hear back on this forum you might try the mailing list for rdesktop (which is used as the backend of tsclient). Out of curiosity does this happen if you connect from a Windows machine? If not, does that machine have any language packs or localization settings? As in - is this a localization issues or an RDP issue, know what I mean?

---

### Post by matunaator on 2011-12-08
When I'm connecting from another Windows machine everything is fine, XP or Win7. 
The machine I'm connecting to is running Windows 7 and no localization packs have been installed (it's in English), and uses the Estonian keyboard layout (ee) without any problems. 
The Ubuntu version I'm using is also in english and uses the ee keyboard mapping, also without any problems but this RDP thing.
I just tried to connect from another Linux OS (PCLinux) using the same RDP clients and it had the exact same problem.
One thing I noticed is that the "ee" mapping is missing from the RDP clients keyboard mapping menu, any way to add it there? I think it won't help because I changed it to "fi" which uses some of the same umlauts and the same problem occurred.

---

