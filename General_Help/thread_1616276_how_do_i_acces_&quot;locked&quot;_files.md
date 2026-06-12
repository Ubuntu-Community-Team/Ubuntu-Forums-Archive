---
title: "how do i acces &quot;locked&quot; files"
date: 2010-11-08
forum: General Help
---

### Post by reinaldistic on 2010-11-08
im trying to edit grub.cfg, but ubuntu wont let me save it since it's read only and i cant change that, i remember there is something through terminal you can do that through

---

### Post by Verbeck on 2010-11-08
the command is 
sudo gedit /path/to/file

btw, which ubuntu version are you using?

---

### Post by garvinrick4 on 2010-11-08
> **reinaldistic said:**
> im trying to edit grub.cfg, but ubuntu wont let me save it since it's read only and i cant change that, i remember there is something through terminal you can do that through
```
 gksudo gedit /etc/default/grub
```
change path to config files or whatever you want.
gksudo always for root (so you can save)

Alt/F2 then type in gksudo nautilus,
You are now in root of file system and can use
nautilus to navigate to file you would like to work on it root.

---

### Post by jocko on 2010-11-08
> **reinaldistic said:**
> im trying to edit grub.cfg, but ubuntu wont let me save it since it's read only and i cant change that, i remember there is something through terminal you can do that through
You shoulde NEVER edit grub.cfg yourself, that's why it's read-only (and not even root is allowed to write to it).
Whatever you do will just be reset automatically the next time something runs update-grub.

Whatever changes you want to do to your grub config, do them in the file /etc/default/grub and the files in /etc/grub.d, then generate a new grub.cfg by running this command:
```
sudo update-grub
```

---

