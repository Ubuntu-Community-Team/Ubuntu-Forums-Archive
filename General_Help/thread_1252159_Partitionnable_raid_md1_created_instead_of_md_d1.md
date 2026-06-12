---
title: "Partitionnable raid: md1 created instead of md_d1"
date: 2009-08-28
forum: General Help
---

### Post by romain44444 on 2009-08-28
Hi every one,

I have looked for such a problem in the forum but it seems every one has the opposite problem (let exchange it!!! :D)


So,
here is my environment: 
Linux: xubuntu 8.04

4 sata disks: sd[a-d]
Mount description:
# /dev/sda1   /  ext3
# /dev/sda5  swap    sw

What I want to do is:
Creates a RAID1 array using 2 of the 3 other HD (sdb and sdc)

So I have created one partition on sdb and sdc of type Linux raid autodetect

Then I create my ARRAY
```

mdadm -Cv /dev/md_d1 -l1 -n2 -a4 /dev/sdb1  /dev/sdc1

```
It works ==> I have created my partitions on this new "device":
/dev/md_d1p[1-4]

I launch my array without any problem with:
```

mdadm --assemble /dev/md_d1

```

and my /etc/mdadm/mdadm.conf owns the array line:
```

cat /etc/mdadm/mdadm.conf | grep ARRAY
ARRAY /dev/md_d1 level=raid1 num-devices=2 UUID=98065ad6:07293e11:f8e94fc3:6fa00f45

```

But when I reboot, the assemble array is /dev/md1 and not /dev/md_d1 

I can manually stop the array /dev/md1  and then start  /dev/md_d1 

but of course when I boot, I want to mount my /dev/md_d1p[1-4] so it would be gorgeous to resolve this automatic array build problem!!


Does anyone of you has an idea?

---

