---
title: "Permissions in a live session on boot from CD"
date: 2010-07-19
forum: General Help
---

### Post by ThePossum on 2010-07-19
Have problem with HD too full so I have booted from a live CD hoping to copy my document and data files onto an external drive.

Have a problem with a couple directories on my HD.  They have a X on them and when I try to copy them I get an error message that I do not have permission to read them.  Same thing happens when I go to open the directory to see what files are in there.

Need help on this asap so I can get the permissions changed in live CD session so I can copy them to the external drive.

No luck doing it in a regular boot to my HD as it will not allow me in due to the HD being full.  Even in terminal I can't access the directories in question because the seem not to exist but yet when I do a df command they show up.

Any quick help will be appreciated.

Thanks,

Bryce

P.S.  This problem occurred after I updated to ver 10.4

---

### Post by gordintoronto on 2010-07-19
From the LiveCD, open a terminal session and enter the command:
gksudo nautilus

That gives you a file manager with root permissions.

---

### Post by ThePossum on 2010-07-21
Thanks,

I will give that a try.

---

