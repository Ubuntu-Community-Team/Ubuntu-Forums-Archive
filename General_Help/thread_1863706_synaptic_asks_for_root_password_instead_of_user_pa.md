---
title: "synaptic asks for root password instead of user password"
date: 2011-10-18
forum: General Help
---

### Post by alenis on 2011-10-18
I made a fresh install of 11.10, keeping all my home files (located in a separate partition) intact. After that I had troubles logging in with my username/password. After many trials and errors I solved by removing my username and adding it again. Now almost everything works ok. The only odd thing is that some programs, such as synaptic or network manager, ask me for the root password instead of my user password, as usually happens in Ubuntu. What should I do to revert to the "normal" Ubuntu behavior?

---

### Post by mike555 on 2011-10-18
There is a way to set a root password, but it probably wont let you use the same password as your user password, search the forums as I can't remember how.

---

### Post by mcduck on 2011-10-18
> **alenis said:**
> I made a fresh install of 11.10, keeping all my home files (located in a separate partition) intact. After that I had troubles logging in with my username/password. After many trials and errors I solved by removing my username and adding it again. Now almost everything works ok. The only odd thing is that some programs, such as synaptic or network manager, ask me for the root password instead of my user password, as usually happens in Ubuntu. What should I do to revert to the "normal" Ubuntu behavior?

Make sure your user is still member of the admin group. (only the user created during install is automatically set as admin, any user you create afterwards is just a normal user unless you set them as admin yourself).

You can check what groups your user belongs to with the "groups" command in a terminal.

In case the user isn't an admin, you'll need to boot into recovery mode and then run "usermod -aG admin *yourusername*"

---

### Post by alenis on 2011-10-18
I added myself to the admin group and now everything seems as usual. Thank you.

---

### Post by davesmith on 2011-11-08
McDuff, could you kindly explain how to delete a user?

After installing, I went to 'users & groups' and created another account with non-administrator rights and installed Firefox, VLC and a printer. For all sorts of reasons I want to delete this account, but even when I'm logged in as the admin it says i dont have permission to delete it. What gives?

---

### Post by lechien73 on 2011-11-08
Have you tried:

```
sudo deluser USER_NAME
```

from a terminal window? Obviously replace USER_NAME with the username you wish to delete.

---

