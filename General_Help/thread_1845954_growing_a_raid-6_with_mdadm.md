---
title: "growing a raid-6 with mdadm"
date: 2011-09-18
forum: General Help
---

### Post by brdohman on 2011-09-18
i currently have a raid-6. it contains 4 1.5tb drives and i am wanting to add 2 other 1.5tb drives. however, i'm having a problem doing so. 

my current raid is at /dev/md0. i was successfully able to run
```
mdadm --add /dev/md0 /dev/sda1
mdadm --add /dev/md0 /dev/sdb1
```

this was successful, as i can now see both of these drives listed as spares for the raid. my next step was to run
```
mdadm --grow /dev/md0 /dev/sda1
mdadm --grow /dev/md0 /dev/sdb1
```

however, when doing this i received this error
```
mdadm: can only add devices to linear arrays
```

it was my understanding that i could add arrays to the raid-6. i've searched for solutions for this, but the ones i read, didn't seem like they were relevant to my error. I tried doing this in the gui utility as well, but it wouldn't allow me to add the drives.

i looked for some guides on this, but they seemed to relate to other raid sets and not -6, so i thought i would ask here, as i want to make sure i do it properly as to not lose any data. 

i'm running ubuntu 10.10 with kernel 2.6.35-30-generic


thanks

---

