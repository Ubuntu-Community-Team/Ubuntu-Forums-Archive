---
title: "invalid environment block failed to boot default entries"
date: 2010-03-24
forum: General Help
---

### Post by jamesvar_70 on 2010-03-24
invalid environment block failed to boot default entries
I am having the same problem

Invalid Environment Block. I have a dual boot system with Ubuntu 9.10 and windows
i was getting the above message and i found the following solution

pressing E when grub loads, then delete the 2 rows:

recordfail=1
save_env recordfail

Then press Ctrl-X to boot.

When I do this i get the error again as

error: Invalid environment block
Failed to boot default entries
Press any key to continue

strangely i am now unable to load windows also

Any help would be grateful.

---

