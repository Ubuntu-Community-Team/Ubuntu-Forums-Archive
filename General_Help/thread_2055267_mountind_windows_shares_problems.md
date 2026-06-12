---
title: "mountind windows shares problems"
date: 2012-09-09
forum: General Help
---

### Post by eagletjs on 2012-09-09
i am trying to mount my windows shared folder i have installed smbfs, made the dir, and added "//192.168.0.111/My Documents /home/username/Windows cifs uid=username[COLOR=#ff0000][COLOR=#000000],user=username[/COLOR][COLOR=#000000],pasword=password[/COLOR][COLOR=#000000] 0 0" to the fstab file and remounted. it gives me error line 14 in /etc/fstab is bad. but if i change //192.168.0.111/My Documents to //192.168.0.111/Videos it works. how can i get My Documents to work?[/COLOR][/COLOR]

---

### Post by 2F4U on 2012-09-09
Try to replace

[COLOR=#ff0000][COLOR=#000000]//192.168.0.111/My Documents

by

[/COLOR][/COLOR]
[COLOR=#ff0000][COLOR=#000000]//192.168.0.111/My[/COLOR][/COLOR]**\040**[COLOR=#ff0000][COLOR=#000000]Documents

Most likely, the problem is due to the space contained in the path.
[/COLOR][/COLOR]

---

### Post by eagletjs on 2012-09-09
thanks that fixed my problem

---

