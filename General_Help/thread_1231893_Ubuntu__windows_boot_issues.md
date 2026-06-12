---
title: "Ubuntu / windows boot issues"
date: 2009-08-05
forum: General Help
---

### Post by xTDee on 2009-08-05
Okay here's my issue. I have a compaq presario sr 2020nx desktop running windows vista, I took the hard drive out of my old Dell dimension desktop so I could have seperate operating systems on seperate hard drives. I reinstalled ubuntu 9.04 on the new hard drive and it asked during installation if I wanted to install grub on the other hard drive and I said yes thinking it would give me the option to dual boot one of them. Now vista won't load.. When I select vista I get "Error 13: invalid or unsupported executable format" I've tried to run my windows installation disk to repair the mbr like all of google says but my drives arent even showing up on there. How do I fix this? Please help, I've only been using ubuntu for about 8 months and am still very much a newbie.

---

### Post by nhanquy on 2009-08-05
It sounds like you have vista on another drive.Add this to the Windows section:

```

map (hd0) (hd1)
map (hd1) (hd0)

```read : [http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

---

### Post by xTDee on 2009-08-05
I tried that but it did not work, I think grub was corrupted somehow but I reinstalled ubuntu again which I didn't want to do and now it's working. Both boot fine. Not sure what happened but it's fixed now.

---

