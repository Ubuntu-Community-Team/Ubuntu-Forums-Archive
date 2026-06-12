---
title: "windows 7 disappears from boot menu after updates."
date: 2010-09-11
forum: General Help
---

### Post by Aerui on 2010-09-11
Hi I'm new to Ubuntu and have recently downloaded 10.04 I've just installed to a spare hard drive. The problem I have is after I do the latest system updates to Ubuntu my windows 7 selection disappears from the boot menu. It's there straight after the install. The only way I got it back was to re install ubuntu.

Currently I'm not using Ubuntu as I don't want to lose the windows 7 selection again and have to re install.

Has anyone seen this problem before and any advise on what I should do to ensure I can still select windows 7 from the boot menu after I update ubuntu.

Thanks
A

---

### Post by howefield on 2010-09-11
Instead of reinstalling Ubuntu, you could try the terminal command

```
sudo update-grub
```

---

### Post by Aerui on 2010-09-11
Thanks for your reply, I read on another post somewhere that some updated NTFS driver may not be working properly with grub so I purposely left out 'mountall' from the update list, the thinking being maybe this contains the updated NTFS drivers?

Anyway I have rebooted several times now and windows 7 is still listed. If it does disappear again though i'll try the update -grub.

---

