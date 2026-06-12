---
title: "How to get back the separate /home partition to the root partition?"
date: 2011-10-12
forum: General Help
---

### Post by tokyo-joe on 2011-10-12
I have installed my Ubuntu with a separate /home partition, but I want to move /home directory back to the systems root partition.

How can I do that?

Just copy the entire /home directory to /home on the root partion and edit /etc/fstab? (Even if it's correct, I need a more specific instraction).

Thanks in advance.

---

### Post by hwttdz on 2011-10-12
Yeah, that should do it. I'd probably change the mountpoint for /home in fstab to be /old_home
then reboot/unmount/remount (you'll probably get lots of complaints about missing home directory, you might want to do the copy in single user mode or at a recovery prompt)
then do "cp -f -p -r /old_home /home"
then reboot again, check that everything's fine and finally you can turn off mounting of old home in fstab or delete the data as you choose.

---

