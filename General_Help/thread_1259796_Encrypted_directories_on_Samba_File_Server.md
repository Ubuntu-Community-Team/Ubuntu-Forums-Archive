---
title: "Encrypted directories on Samba File Server"
date: 2009-09-06
forum: General Help
---

### Post by stefanadelbert on 2009-09-06
I'm setting up a file server for a small office and want to give each user a login and a shared folder. The directors would like some privacy though. So, I would like to give each user a "private" sub-folder within their shared folder (with 0700 permissions) that is encrypted, possibly using Ecryptfs or EncFS. Ideally this folder would be decrypted each time the user logs in to the file server and then encrypted again once they log out.

This would mean that the private directory would be decrypted while the user is logged in though, so anyone with root access would have access to the decrypted files. Maybe there is a better solution.

Any ideas?

---

### Post by joseba on 2009-09-22
how as you solved this?

thx!

---

### Post by stefanadelbert on 2009-09-27
Just about the only solution that I can come up with is having users encrypt their own data using TreuCrypt or something similar and then store the encrypted files on the shared drive. It's not ideal. You got any ideas, joseba?

---

