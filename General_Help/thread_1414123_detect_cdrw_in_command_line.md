---
title: "detect cdrw in command line"
date: 2010-02-23
forum: General Help
---

### Post by cong06 on 2010-02-23
I already have a solution, but I was hoping for a faster one:
```

lshw -short -class "disk" | grep "RW" | awk '{print $3,$4}'

```

The thing is lshw is pretty slow. I was hoping something on about the speed of:
```

cat /proc/meminfo | grep "MemTotal"

```

Any ideas?

---

### Post by gmargo on 2010-02-23
Check **/proc/scsi/scsi**, it may have what you need.  More detailed info is probably available from subdirectories under **/proc/sys/dev/** like /proc/sys/dev/cdrom/info.

---

### Post by cong06 on 2010-02-24
Ok, so this code is actually a bit better then the previous code anyway (not to mention that it's faster)
```
cat /proc/sys/dev/cdrom/info | grep "write" | awk 'BEGIN{v=0;}{ v=(v+$4);}END{print v}'
```
It adds up all the 'write options' and if the number is greater then 0, I'll install 'nautilus-cd-burner'.

But I'm a bit worried about the:
```

Can write MRW:          1
Can write RAM:          1

```
Since I don't really know what those mean...

I'm sure a more 'stable' way to do it would be to just check for 'Can write CD-' and 'Can write DVD-'

Anyway, thanks. It's quite possible that I'll figure out that I need to go the more stable way after some testing.

---

