---
title: "Discussion on improving boot time"
date: 2010-12-29
forum: General Help
---

### Post by Dreamboat on 2010-12-29
I am using Ubuntu 10.04 on a 64 bit machine and I notice my boot times are not impressive. It takes a while, i guess a few extra seconds but it doesn't feel good cause I know what linux stands for, speed. Been using it for a while. The time is from the grub menu to the point where the purple screen comes in.

I installed sysv-rc-conf and flushed out some useless stuffs from booting up. Still would like to know if there is some extra tweaks that can tune my machine.

/var/log/messages and dmesg shows no errors or suspicious stuffs, but still I guess somethings can be improved here. Any suggestions in this matter would be of great help while I dig deep into this. 

Thanks Ubuntu buddies .. wishing a happy new year ahead. With lots of Ubuntu days.

---

### Post by galvatron408 on 2010-12-30
you should boot in to init level 3 and then see if there are any particular service that seems to be a bit slow. look at those service to see if they are optimized or not.

---

