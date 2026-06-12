---
title: "Fail to mount a win network drive"
date: 2011-12-08
forum: General Help
---

### Post by figo2476 on 2011-12-08
I am able to use "connect to server" GUI to connect the shared drive. I can create a folder inside.

The following command line works for my personal network drive, but NOT the shared drive:

sudo mount -t cifs //the_path_to_win_server /media/something -o username=my_username,domain=my_domain,password=my_password,iocharset=utf8,file_mode=0777,dir_mode=0777

Is there any permission issue?

---

