---
title: "Problem with suspend on one user while on others it works"
date: 2009-07-21
forum: General Help
---

### Post by dxdemetriou on 2009-07-21
Hi,
I'm using Jaunty with nv140. I don't know if the problem it is because of nvidia's module, but other users can make suspend. I tried to delete and recreate the user with the same id but nothing. Instead of suspend it locks the screen. I tried also to create another user with different name and it worked. Is there another location that X11 or Gnome remembers the account names?
Thanks

Edit: I created a username with the same id and different name, and it worked. I deleted it and recreate the account with the old username and didn't worked. It just locks the screen.

Edit2: If I switch to another user and return back to my account I can make suspend. If I log-out the switched user I can't.

Edit3: Ok, I found what the problem is, just I didn't knew where to search for
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/400928](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/400928)

---

