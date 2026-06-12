---
title: "Invalid Environment Block"
date: 2009-10-17
forum: General Help
---

### Post by crushingandy on 2009-10-17
I have Karmic Koala on my external HDD, and I was running it all day, but now when I try to boot, I get this error. Invalid Environment Block. I dont understand why it was working all day and now I cant even boot. Any ideas?

Also: I read some posts about trying to fix this, and I saw that pressing E when grub loads, then delete the 2 rows:
recordfail=1
save_env recordfail
Then boot with Ctrl-X.
When I did this, I get the following error before being able to delete the two lines:
Press any key to continue
error: Invalid environment block
       Failed to boot default entries

Any help would be grateful.

---

### Post by jgeeting on 2009-10-20
Thank you, it was a good fix.
My Asus netbook would not respond to pressing the "e" key at first but then out of the blue it gave me the list. I'm not sure why? Once I got over that hump the fix was easy. Oh yeah I didn't realize it would take sudo permission but after thinking about it of course it would.

---

