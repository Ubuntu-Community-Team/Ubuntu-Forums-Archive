---
title: "Files protected/won't boot"
date: 2011-03-14
forum: General Help
---

### Post by cabooze on 2011-03-14
Hi there, well first i have 2 problems,
First is, after i reinstalled windows 7 ubuntu won't boot.
It's not that bad because i wanted to reinstall ubuntu anyway. Problem is, I do want to copy some files that are on my ubuntu harddrive. so i booted ubuntu via disc, and tried to copy the files to my windows hdd, but it says that i 'm not the owner and i'm not allowed,
how can i fix this?
thnx

---

### Post by antaios256 on 2011-03-14
After i installed windows i did have to re-install grub to allow for it to boot, as the windows bootloader will take over this when its installed. if that fails the only thing i can recomend is trying to change ownership of the files.

boot from live cd/usb

sudo chown ...

then copy

however as i am relatively new to ubuntu/linux i could be off base here if someone else can confirm/tell me if im off-base before i ruin your file structer it would be good.

---

### Post by cabooze on 2011-03-14
Hmm, I'm new in linux, so how do i use chown?

---

### Post by antaios256 on 2011-03-14
deleted

---

### Post by antaios256 on 2011-03-14
sorry about my late reply actually im new to linux myself but to use the chown

chown -hR root /folder
                                    
           root being the user who is taking ownership

this will take ownership for root of the /folder and all subdirectories

again if anyone that is more experience can offer a suggestion would be good

---

