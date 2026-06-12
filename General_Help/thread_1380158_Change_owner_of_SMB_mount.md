---
title: "Change owner of SMB mount?"
date: 2010-01-13
forum: General Help
---

### Post by mac666 on 2010-01-13
Hey
I mounted a SMB mounted in Fstab with the line:
```
//nasaret.local/Lager /media/Lager cifs auto,iocharset=utf8,uid=mac,gid=mac,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
```

But the user 'mac' doesnt own the root of the disc. making some programs like ktorrent, unable to download material to the drive.

How can i change the owner?
If i try: 
```
[CODE]mac@turd:/$ sudo chown mac /media/Lager
chown: byter ägare av "/media/Lager": Åtkomst nekas
```[/CODE] ((access denied))

anyone?

---

