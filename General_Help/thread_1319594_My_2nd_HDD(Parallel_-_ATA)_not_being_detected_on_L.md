---
title: "My 2nd HDD(Parallel - ATA) not being detected on Linux Ubuntu"
date: 2009-11-08
forum: General Help
---

### Post by dez0829 on 2009-11-08
I'm new with Linux-Ubuntu and I'm just wondering if someone come help me with my current problem. I have 2 sets of HDD (both are Parallel - ATA [master/slave]). I also have a dual OS installed on my PC the other one being Windows XP. When I am using Windows XP, I have no problem in accessing my 2nd HDD. However, when I switch on my Linux - Ubuntu the 2nd HDD is not being detected on the list of connected drives, I have my important files store on my second HDD. I'm trying to get my self familiarize with Linux-Ubuntu as I would like to disposed or uninstall Windows XP totally from my PC.

---

### Post by P4man on 2009-11-08
Hi, Are you sure its not listed when you go to Places (main menu) dont you see something there like "160 GB volume" ?

If not, open a terminal and type
```

sudo fdisk -l
```

and 

```
mount
```

and copy paste the output here. You can open a terminal from applications > accessories.

---

