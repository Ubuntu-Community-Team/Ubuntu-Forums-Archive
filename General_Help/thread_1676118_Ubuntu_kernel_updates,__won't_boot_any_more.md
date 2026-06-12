---
title: "Ubuntu kernel updates,  won't boot any more"
date: 2011-01-26
forum: General Help
---

### Post by k999 on 2011-01-26
I recently convinced my girlfriend to use Ubuntu on her laptop instead of Windows, by installing wubi (it's not dangerous, you can use Windows when you need to, etc...)

Today there was a kernel update, and some other updates too. We installed them, and now Ubuntu won't boot any more. The Windows boot menu appears, and we choose Ubuntu, then when grub starts it shows "Try (hd0,0): NTFS" for about half a second. Then there's an immediate error:

error: unknown command 'loadfont'
error: file not found.

which shows for about a second or so, and then the computer reboots and tries again.

Did someone forget to test the updates on wubi? Any good ideas on the best way to fix this? I'm sure I can get it fixed, but it'll probably take me a little while to find out what's wrong and get that fixed, so any hints would be nice.

---

### Post by coffeecat on 2011-01-26
Have a look at the first post in the Wubi Megathread:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

From what you describe it sounds as though you are experiencing problem #2. You don't say which version of Ubuntu you are running and whether you did a version upgrade, but the fixes are there for the different scenarios.

---

### Post by k999 on 2011-01-26
Thanks! That looks like exactly what I'm looking for.

---

