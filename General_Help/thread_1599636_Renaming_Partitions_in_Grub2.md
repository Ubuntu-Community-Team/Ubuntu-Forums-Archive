---
title: "Renaming Partitions in Grub2"
date: 2010-10-18
forum: General Help
---

### Post by klausner on 2010-10-18
I'm trying to change the name of a partition that grub mislabels. I've tried editing */etc/grub.d/30_os-prober*, but I keep getting syntax errors.

The lines I changed are: 
```
      case ${LONGNAME} in
        Windows\ Vista*|Windows\ 7*)
        ;;
```

replacing them with:
```
      case ${LONGNAME} in
        Windows\ Vista*)
        LONGNAME="Vaio Recovery Partition"
        ;;
      case ${LONGNAME} in
        Windows\ 7*)
        ;;
```

but *update-grub* barfs on:
     ```
 [COLOR="Red"]case ${LONGNAME} in[/COLOR]
        Windows\ 7*)
        ;;
```

with the error:
> /etc/grub.d/30_os-prober: 163: Syntax error: word unexpected (expecting ")")

where line 163 is the one marked above in red.

Can someone please tell me what my error is?

---

### Post by VMC on 2010-10-18
Have a look at this [guide]("http://ubuntuforums.org/showthread.php?t=1287602"). Go to Section # **3. CHANGING WINDOWS/OTHER OS TITLES**

---

### Post by klausner on 2010-10-18
> **VMC said:**
> Have a look at this [guide]("http://ubuntuforums.org/showthread.php?t=1287602"). Go to Section # **3. CHANGING WINDOWS/OTHER OS TITLES**

Thanks. I had seen it, but the section he quotes doesn't match my config file. Besides, I thought I was doing essentially the same thing, just using the existing case statement instead of a bunch of if/elif lines.

---

