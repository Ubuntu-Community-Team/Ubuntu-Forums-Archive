---
title: "Access USB Expansion Drive from second desktop"
date: 2010-06-08
forum: General Help
---

### Post by prestondocks on 2010-06-08
I have just installed Ubuntu 10.4 64 Bit. I have a 500GB USB Expansion drive which I mounts fine in my primary users desktop (The first user I setup)

I have now setup a second account, but the USB disk does not mount. I can see the folder in /media/Expansion Drive but it says I don't have access to it. If I su to my primary user, I can access it.

I have tried chown and chmod to give ownership to a second account and to a new group I setup with both user names in, but the changes do not seem to get applied (of course used SUDO).

By the way I have tried sharing the folder from my main account, but I am not able to connect to it. It seems that nautilus does not want to connect to SMB shares.

Can anyone help?

Thanks
Simon

---

### Post by cbecker78 on 2010-06-08
How is your drive formatted?

Can you post your fstab?  It is quite possibly a problem with that.  Could be as simple as adding ",user rw," to your options...

---

### Post by prestondocks on 2010-06-09
Thanks for the response but I sorted the problem and yes it was the Fstab. I downloaded a tool for managing mounts. The problem was that I had to specify a group that contained the users who should own the mount.
 
Previously it was being mounted and permissions assigned based on the first user to log in. The second user then had no permission to access the mount.
 
Thanks

---

