---
title: "Software center not working"
date: 2011-10-07
forum: General Help
---

### Post by Urbanblaze on 2011-10-07
When i was updating my ubuntu it crashed in the middle. Was awhile before i gto my computer knowledge friend to fix it.
Now i have ubuntu 11.04 on my acer laptop.
I can open the software center, but it won't search. Takes forever to load. So i can't download adobe or skype or anything!!!!
I can't get plug-ins either! so its kinda boring and frustrating. I've tried everything. even a few sudo commands but nothing works. I always get errors or whatever.

---

### Post by Rubi1200 on 2011-10-07
Hi and welcome to the forums :)

Open a terminal with Ctrl+Alt+T and run the following command:

```
sudo apt-get update
```

If there are error messages, copy and paste them from the terminal into a new post here so we can take a look at the errors.

Thanks.

---

### Post by Keshav2050 on 2011-10-10
"Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."

I got this error in last few lines when I went to "sudo apt-get update"

---

### Post by Keshav2050 on 2011-10-10
If I open the Ubuntu software center and go to any department it just keeps loading all the time.

---

### Post by plucky on 2011-10-10
> **Keshav2050 said:**
> "Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."

I got this error in last few lines when I went to "sudo apt-get update"

Open a terminal and use ```
sudo rm /var/lib/apt/lists/* -vf
``` then run ```
sudo apt-get update
``` and see if there are any errors.

Good Luck

---

### Post by Keshav2050 on 2011-10-11
Thank you very much, now it didn't show any errors and the software center is also working.
Thank you once again.

---

### Post by Rubi1200 on 2011-10-11
Glad you got things sorted out and are back in business.

Enjoy :)

---

