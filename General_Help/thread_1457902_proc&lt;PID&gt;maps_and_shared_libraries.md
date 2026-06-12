---
title: "/proc/&lt;PID&gt;/maps and shared libraries"
date: 2010-04-19
forum: General Help
---

### Post by Steflinux on 2010-04-19
Hello all,

Maybe some Guru reading this page can  cast some light on this **process memory question**? :KS

I recently installed Kubuntu 9.10 and openSUSE 11.2 32 bits - both  running Linux **kernel 2.6.31**.


 I don’t understand why** cat /proc/<PID>/maps** (related to the top command  here for example) returns _4 lines per shared libraries_ (for some, not  all - the usual 3 lines then).
 

3 lines make sense, like in older kernel (2.6.28, …): bss, data and  text segments. In some kernels I noticed also two entries only per  shared library (bss merged with data, or data only? That makes sense, at  least)


 However, 4 entries (!), one being a page of rights “—p” (cannot be  read, written or executed) seems very odd to me. I get the same results  on my Kubuntu and SUSE, so - hence no bug. But what then? There is  nothing much in the ELF format that give me any hint.


 An exemple for libncurses.so.5.6 (related to top):
b76ab000-b76e1000 r-xp 00000000 08:02 127570 /lib/libncurses.so.5.6
b76e1000-b76e2000 —p 00036000 08:02 127570 /lib/libncurses.so.5.6
b76e2000-b76e4000 r–p 00036000 08:02 127570 /lib/libncurses.so.5.6
b76e4000-b76e8000 rw-p 00038000 08:02 127570 /lib/libncurses.so.5.6
 

Any help appreciated. Thanks.



– Stéphane

---

