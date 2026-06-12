---
title: "gtkVNCViewer keyring error after 10.04 upgrade"
date: 2010-04-30
forum: General Help
---

### Post by tiwatson on 2010-04-30
Upgraded from 9.10 to 10.04 smoothly, but now gtkVNCViewer will not start. Something to do with a keyring error.

Google turns up nothing.. How do I fix this?

```

tim@tim-laptop ~$ gtkvncviewer
** Message: secret service operation failed: Cannot get secret of a locked object
Traceback (most recent call last):
  File "./gtkvncviewer.py", line 426, in <module>
    instance = GtkVncViewer()
  File "./gtkvncviewer.py", line 129, in __init__
    secret = gnomekeyring.item_get_info_sync(keyring, auth_token).get_secret()
gnomekeyring.IOError

```

---

### Post by tiwatson on 2010-05-01
Anyone got any ideas? I'm at a loss...

---

### Post by xender69 on 2010-05-12
me too, it was first working ok but now I get the same message as well.  my linux was a fresh install.

---

### Post by kingshand on 2010-11-29
same problem. anyone find a fix for this yet?

---

### Post by EdTheUniqueGeek on 2010-12-14
I have the exact same problem. Install it, it worked once. Tried to launch it again and got that error.

---

### Post by kihjin on 2010-12-22
How to fix:

**SEE BELOW FOR UPDATED SCRIPT**

This replaces "gnomekeyring.DeniedError" with "(gnomekeyring.DeniedError, gnomekeyring.BadArgumentsError)" on line 130.

---

### Post by EdTheUniqueGeek on 2010-12-23
This didn't work for me. I still got the same error.
Here is what I did:


ed@ed910 ~ $ sudo sed -i -e '130 s/gnomekeyring.DeniedError/(gnomekeyring.DeniedError, gnomekeyring.BadArgumentsError)/' /usr/share/gtkvncviewer/gtkvncviewer.py
ed@ed910 ~ $ gtkvncviewer
** Message: secret service operation failed: Cannot get secret of a locked object
Traceback (most recent call last):
  File "./gtkvncviewer.py", line 426, in <module>
    instance = GtkVncViewer()
  File "./gtkvncviewer.py", line 129, in __init__
    secret = gnomekeyring.item_get_info_sync(keyring, auth_token).get_secret()
gnomekeyring.IOError

---

### Post by kihjin on 2010-12-23
Add gnomekeyring.IOError to the exceptions list...

```

sudo sed -i -e '130 s/gnomekeyring.DeniedError/(gnomekeyring.DeniedError, gnomekeyring.BadArgumentsError,gnomekeyring.IOError)/' /usr/share/gtkvncviewer/gtkvncviewer.py

```

If you ran the FIRST sed, you'll need to manually revert first or manually add gnomekeyring.IOError to the list.

---

### Post by EdTheUniqueGeek on 2010-12-23
Awesome. That worked. Thanks a lot.

---

### Post by 3LDRU1D4 on 2012-07-15
Thank you. Copy&paste your command was enough. Worked fine.

---

