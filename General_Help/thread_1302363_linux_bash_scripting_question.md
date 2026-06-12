---
title: "linux bash scripting question"
date: 2009-10-27
forum: General Help
---

### Post by david90 on 2009-10-27
This statement:
RAID_FAILDEV_CHK=$(mdadm --detail /dev/md0 | grep "Failed Devices")

returns:
Failed Devices : 0

The problem i'm having is that the returned string in var. RAID_FAILDEV_CHK has an invisible character at the end (after the 0).  How do I trim off this character?  I think it is a return/newline character.

---

### Post by dcstar on 2009-10-27
> **david90 said:**
> This statement:
RAID_FAILDEV_CHK=$(mdadm --detail /dev/md0 | grep "Failed Devices")

returns:
Failed Devices : 0

The problem i'm having is that the returned string in var. RAID_FAILDEV_CHK has an invisible character at the end (after the 0).  How do I trim off this character?  I think it is a return/newline character.

Try:

```
RAID_FAILDEV_CHK=$(mdadm --detail /dev/md0 | grep **-Z **"Failed Devices")
```

---

### Post by david90 on 2009-10-29
> **dcstar said:**
> Try:

```
RAID_FAILDEV_CHK=$(mdadm --detail /dev/md0 | grep **-Z **"Failed Devices")
```

It didn't work.  here is my script

```
#!/bin/bash
RAID_FAILDEV_CHK=$(mdadm --detail /dev/md0 | grep -Z "Failed Devices")

if [ "${RAID_FAILDEV_CHK}" = "Failed Devices : 0" ]; then
    echo "good"
fi

```

if I do echo  ${RAID_FAILDEV_CHK}, it would return "Failed Devices : 0" but with an extra invisible character behind the 0.  I'm looking for a clean way to excute the if statement above.

Another way to make the if statement above work is to insert the return character in the string "Failed Devices : 0".  How do I do that?

---

### Post by eckirchn on 2010-06-15
Your missing a leading " "

My sequence:
[INDENT][root@Server cron.hourly]# df | grep md0
[INDENT]/dev/md0             1922871344 520999316 1399918504  28% /mnt/md0
[/INDENT]
[root@Server cron.hourly]# more test.sh
[INDENT]#!/bin/bash
RAID_FAILDEV_CHK=$(mdadm --detail /dev/md0 | grep -Z "Failed Devices")

if [ "${RAID_FAILDEV_CHK}" = " Failed Devices : 0" ]; then
    echo "good"
fi
[/INDENT][root@Server cron.hourly]# ./test.sh
[INDENT]good
[/INDENT][/INDENT]
> **david90 said:**
> It didn't work.  here is my script

```
#!/bin/bash
RAID_FAILDEV_CHK=$(mdadm --detail /dev/md0 | grep -Z "Failed Devices")

if [ "${RAID_FAILDEV_CHK}" = "Failed Devices : 0" ]; then
    echo "good"
fi

```if I do echo  ${RAID_FAILDEV_CHK}, it would return "Failed Devices : 0" but with an extra invisible character behind the 0.  I'm looking for a clean way to excute the if statement above.

Another way to make the if statement above work is to insert the return character in the string "Failed Devices : 0".  How do I do that?

---

