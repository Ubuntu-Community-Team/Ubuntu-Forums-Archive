---
title: "Problems when doing updates..."
date: 2011-10-19
forum: General Help
---

### Post by Kiraitachi on 2011-10-19
HI I have an error showing up each time I do "Sudo apt-get update"

It updates and then shows at the end:

W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


I do run apt-get update again and does not show...but..will show again the error if I close terminal and run another sudo apt-get update.....seems I have duplicates...is there a way I can solve this???

Or I have to delete manually each file???

Thanks.

---

### Post by e79 on 2011-10-19
```
sudo mkdir /var/lib/apt/lists-OLD
``````
sudo mv /var/lib/apt/lists/* /var/lib/apt/lists-OLD/
``````
sudo apt-get update && sudo apt-get dist-upgrade
```:popcorn:

---

### Post by e79 on 2011-10-20
Did it help ?

---

### Post by Kiraitachi on 2011-10-21
Hey thanks a lot sorry for a late response will try rigbt now

---

### Post by Kiraitachi on 2011-10-21
Hey thanks a lot did not think of that haha lol it was so easy and im a programmer. The thing is that I did not know that doing sudo apt get update will create a new folder with all the lists in it lol.

---

### Post by e79 on 2011-10-21
No problems, I'm glad we could sort that out.

Yeah sometimes /var/lib/apt/lists/ gets messed up and by doing the above commands, you simply removes all entry and then fetching them again through ap-get update.

If you feel the case is resolved, please mark the thread as 'Solved' using your Thread Tools.

Cheers

---

