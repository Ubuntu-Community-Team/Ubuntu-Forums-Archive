---
title: "Chmod does not require root privileges"
date: 2011-03-02
forum: General Help
---

### Post by Apocalypse_666 on 2011-03-02
Hello everyone,

This morning I was going around, changing some permissions for some of my files that I want to protect and then I noticed something weird: changing privileges with chmod did not require root access (sudo)! This seems very strange to me, as it would make any protection useless. 
Is there anything I might have changed that causes this? Or is there anything I CAN change to stop this?? 
Regards,

Linus

---

### Post by mcduck on 2011-03-02
Did you use it on files owned by your user?

You of course already have permission to do whatever you want with your own files. :) You'd only need sudo if you tried to chmod a file that doesn't belong to your user.

---

### Post by Apocalypse_666 on 2011-03-02
I set a folder's permissions with chmod 000, after which I could no longer see it's contents (which is what I wanted). However, I could then change it back with chmod 777 without any problems...

---

### Post by Apocalypse_666 on 2011-03-02
Oh, I see what you mean now. I chown'ed the folder to root, after which it behaved like I wanted. I learn something everyday, ey? 
Linus

---

