---
title: "Nautilus ignore setgid"
date: 2010-12-21
forum: General Help
---

### Post by Sharai on 2010-12-21
Hello. I want to share a folder for two users, here is what I did:

-made group
-add users to group
-set chmod
-set chown
-set setgid 2775
-reboot

made echo test > /Common/testfile
going to see right - group common read&write

made file with nautilus
going to see right - group common readonly

copy file with nautilus
going to see right - group common readonly 0_o

Why? Is it a bug? This was on a clean Ubuntu 10.10 installation.
additional link [http://askubuntu.com/questions/18348/nautilus-doesnt-see-setgid](http://askubuntu.com/questions/18348/nautilus-doesnt-see-setgid)

---

