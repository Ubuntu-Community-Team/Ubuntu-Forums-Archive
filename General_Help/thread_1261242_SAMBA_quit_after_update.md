---
title: "SAMBA quit after update"
date: 2009-09-08
forum: General Help
---

### Post by LeeS_AIA on 2009-09-08
First off I'm not very experienced at this. I have a small office and we use a Ubuntu file server.

Last Friday I did an update, I should have left everything alone, all was working fine. The connection to the server stopped and is not viewable from other pc's and a mac.

In the SWAT (Samba Web Administration Tools) it says that Samba is not running. Selecting restart or start will not make it run.

I've tried removing and reloading sanba, but that doesn't seem to work. After removing a reload indicates that it's already loaded? I've looked in /usr/sbin for smbd it doesn't reside there.

Any advice would be greatly appreciated.

Help!!

Thanks!

---

### Post by rob-ward on 2009-09-08
If you just need to start samba then the command is
```

sudo /etc/init.d/samba start
```

Not sure if that is your problem or not but see what it says.

---

### Post by LeeS_AIA on 2009-09-08
Thanks, tried that....no luck! I'm really baffeled!

---

