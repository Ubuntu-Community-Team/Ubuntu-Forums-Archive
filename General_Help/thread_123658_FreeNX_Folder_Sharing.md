---
title: "FreeNX Folder Sharing"
date: 2006-01-30
forum: General Help
---

### Post by scrillamaan on 2006-01-30
I've just installed FreeNX and its great and wonderful and everything everyone said it could be...almost. Has anyone gotten folder sharing to work with a normal user? I setup folder sharing using the defaults on the windows nx client, but when I attempt to connect using my normal login I get an error about smbmnt needing root. So I start a new session as root and folder sharing is fine. Is there any way to share the folder without logging in as root? I'm guessing giving my local user different permissions might do the trick, but I think sudo is there for a reason. :confused:

---

### Post by scrillamaan on 2006-02-01
Bump

---

### Post by stoffe on 2006-02-04
[QUOTE=scrillamaan]I've just installed FreeNX and its great and wonderful and everything everyone said it could be...almost. Has anyone gotten folder sharing to work with a normal user? I setup folder sharing using the defaults on the windows nx client, but when I attempt to connect using my normal login I get an error about smbmnt needing root. So I start a new session as root and folder sharing is fine. Is there any way to share the folder without logging in as root? I'm guessing giving my local user different permissions might do the trick, but I think sudo is there for a reason. :confused:[/QUOTE]
FreeNX needs smbmnt to do the actual work, and smbmnt needs root permissions to mount the shares. By default, smbmnt has suid root, but this is removed by default in Ubuntu, since a default Ubuntu install does not need it - gnome does not connect that way. That is probably why NX thought it was safe to assume it would just work - many distributions leave it as-is.

To solve the problem, all you need to do is
```
sudo chmod u+s /usr/bin/smbmnt
```

Note however, that suid root might cause a security risk, as anyone running this program runs it like it was run by root. If there are exploitable bugs in it, that might mean a risk. I'd say chances are low, but that is the reason for removing suids in any case possible in the first place.

I'm using this. It's excellent!

---

