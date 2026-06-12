---
title: "Hibernate Not Working"
date: 2011-11-25
forum: General Help
---

### Post by yourself65 on 2011-11-25
i have already matched UUIDs
here is what i got in termina:


mirooz@mirooz-HP-Pavilion-dv6-Notebook-PC:~$ sudo blkid

/dev/sda1: UUID="E2B8EB0FB8EAE0D1" TYPE="ntfs" 
/dev/sda5: LABEL="iDeSigN" UUID="5952875E0769E824" TYPE="ntfs" 
/dev/sda6: UUID="0c0ffab8-dd1d-462c-b35f-601d58c376ee" TYPE="ext4" 
/dev/sda7: LABEL="Video" UUID="01CC766528A49170" TYPE="ntfs" 
/dev/sda8: UUID="03819721-b309-42ff-b4ac-efd64581ea8f" TYPE="swap" 


mirooz@mirooz-HP-Pavilion-dv6-Notebook-PC:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=03819721-b309-42ff-b4ac-efd64581ea8f

the problem still unresolved :|
its like locking the screen

---

### Post by yourself65 on 2011-11-27
Any Solutions yet.... :|

---

### Post by yourself65 on 2011-11-30
I'm Still waitin for sol.............

---

### Post by nothingspecial on 2011-11-30
Hi,

You'll get much better help if you start your own thread instead of digging up a 3 year old one.

I've moved you question to it's own thread.

Please give some more details of what you are trying to do.

---

