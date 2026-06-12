---
title: "Help backing up files."
date: 2009-10-06
forum: General Help
---

### Post by Mutil8r on 2009-10-06
Recently I'v had some boot up errors and tried to fix it. now I just get stuck at the Ubuntu loading logo. When I tried recovery, it said it had to be fixed manualy. I think the

sudo nano /etc/usplash.conf

did it. Need help fixing boot problem or how to back up my files through Live CD cuz I really can't access it anymore.

---

### Post by c0mput3r_n3rD on 2009-10-06
> **Mutil8r said:**
> Recently I'v had some boot up errors and tried to fix it. now I just get stuck at the Ubuntu loading logo. When I tried recovery, it said it had to be fixed manualy. I think the

sudo nano /etc/usplash.conf

did it. Need help fixing boot problem or how to back up my files through Live CD cuz I really can't access it anymore.


No that nano command wouldn't have done it; Nano's just a text editor.  If you boot from the live cd, you should be able to go to Places -> hddName and be able to access all your files.  Else, if you're interested on doing it form the prompt, you'd have to look in your ```
 /media 
``` directory.

---

