---
title: "Uninstall packages"
date: 2011-07-30
forum: General Help
---

### Post by Baloeb on 2011-07-30
This might be a simple answer but I cannot figure it out.  I recently installed K9Copy and a lot of other packages were installed along with it.  Now I want to uninstall it, but only K9Copy uninstalls, not everything else.  How can I find and uninstall all the dependent packages that came along with it?  Is there a way to get rid of everything at once?  Thanks for your help.

---

### Post by Chiel92 on 2011-07-30
> **Baloeb said:**
> This might be a simple answer but I cannot figure it out.  I recently installed K9Copy and a lot of other packages were installed along with it.  Now I want to uninstall it, but only K9Copy uninstalls, not everything else.  How can I find and uninstall all the dependent packages that came along with it?  Is there a way to get rid of everything at once?  Thanks for your help.

I think youre looking for this:
```
sudo apt-get autoremove
```

This command removes packages that were installed by other packages and are no longer needed.

---

### Post by Baloeb on 2011-07-30
Thanks!

---

