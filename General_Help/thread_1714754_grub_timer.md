---
title: "grub timer"
date: 2011-03-25
forum: General Help
---

### Post by NeverHide on 2011-03-25
I'd like to know if there is a way to disable the timer on grub so when i boot my pc grub will wait for my choice on the operating system instead of booting to the currently selected one after 10 secs(if u don't press any key that is)

---

### Post by nice_like_rice on 2011-03-25
sudo gedit /etc/default/grub

then change the line which says something like "GRUB_TIMEOUT 10" and put a # in front of it.

like 

```
#GRUB_TIMEOUT 10
```

---

### Post by drs305 on 2011-03-25
I believe if Grub 2 doesn't find a timeout it will default to 5 seconds.

You can set the timeout to **-1** in /etc/default/grub to require user input.
> GRUB_TIMEOUT=-1

---

### Post by NeverHide on 2011-03-30
I tried both methods but unfortunately in both cases the timer goes to 10 sec :(

---

### Post by wilee-nilee on 2011-03-30
> **NeverHide said:**
> I tried both methods but unfortunately in both cases the timer goes to 10 sec :(

Did you run update-grub after changing the /etc/default/grub

---

### Post by NeverHide on 2011-03-30
> **wilee-nilee said:**
> Did you run update-grub after changing the /etc/default/grub


:-\":-\":-\":-\":-\":-\"
just a little thing that i forgot to do :lolflag:

thank you very much :D

---

### Post by shields on 2011-09-26
I always forget that little thing!!!

Thanks!

---

