---
title: "Xdialog is not showing any text on popup"
date: 2010-03-23
forum: General Help
---

### Post by pasingh on 2010-03-23
Hi All,

I am trying this command 

"Xdialog --title IMR --yesno IMRCAME  8 25 &"

Popup is comming but nothing showing on popup window. and getting below mentioned error on terminal.

Gtk-WARNING (recursed) **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory


Please help me...



Thanks

---

### Post by kerry_s on 2010-03-23
zenity is the default dialog.

from what i can see:
```
zenity --title="IMR" --question --text="my little script" --ok-label="Yes" --cancel-label="No"
```

can you tell us exactly what your trying to do?

---

### Post by pasingh on 2010-03-23
Thanks [kerry_s]("http://ubuntuforums.org/member.php?u=132335") , this is what i want.

---

### Post by kerry_s on 2010-03-23
> **pasingh said:**
> Thanks [kerry_s]("http://ubuntuforums.org/member.php?u=132335") , this is what i want.

huh? you mean thats just what you needed to complete a script?
use "man zenity" if want to do other kinds of dialogs.
let us know if you need more help with your script.

---

### Post by pasingh on 2010-03-23
Thanks, actually I was not aware about this command, i have tried all parameters of Xdialog, searched may thing with that error. But no luck. After putting this command, script is working fine. 


Thanks a lot.  :D

---

