---
title: "weird bash programming problem"
date: 2010-01-05
forum: General Help
---

### Post by david90 on 2010-01-05
```
function raid_check
{
    mdadm --detail $RAID_DISK
    if [ $? = 0 ]; then #check to see if $RAID_DISK is active
    {
        RAID_CHECK_MSG="$RAID_CHECK_MSG $RAID_DISK detected.\n"
        
        RAID_DISK_ACTIVE_DEVICES_CHK=$(mdadm --detail $RAID_DISK | grep "Active Devices" | awk '{print $4}')
        RAID_DISK_WORKING_DEVICES_CHK=$(mdadm --detail $RAID_DISK | grep "Working Devices" | awk '{print $4}')
        #check for # of active and working raid devices.
        if [ "$RAID_DISK_ACTIVE_DEVICES_CHK" = $RAID_DISK_ACTIVE_DEVICES ] &&  [ "$RAID_DISK_WORKING_DEVICES_CHK" = $RAID_DISK_WORKING_DEVICES ]; then
        {
            RAID_CHECK_MSG="$RAID_CHECK_MSG $RAID_DISK is working properly.\n"
            RAID_CHECK_MSG="$RAID_CHECK_MSG RAID_DISK_ACTIVE_DEVICES_CHK: $RAID_DISK_ACTIVE_DEVICES_CHK\n"
            RAID_CHECK_MSG="$RAID_CHECK_MSG RAID_DISK_WORKING_DEVICES_CHK: $RAID_DISK_WORKING_DEVICES_CHK\n"
            RAID_CHK="OK"
        }
        else
        {
            RAID_CHECK_MSG="$RAID_CHECK_MSG $RAID_DISK is not working properly. One or more raid disk might have failed.\n"
            RAID_CHECK_MSG="$RAID_CHECK_MSG RAID_DISK_ACTIVE_DEVICES_CHK: $RAID_DISK_ACTIVE_DEVICES_CHK\n"
            RAID_CHECK_MSG="$RAID_CHECK_MSG RAID_DISK_WORKING_DEVICES_CHK: $RAID_DISK_WORKING_DEVICES_CHK\n"
            RAID_CHK="ERROR"
        }
        fi
        
    }
    else
    {
        RAID_CHECK_MSG="$RAID_CHECK_MSG Can't get information about $RAID_DISK.\n"
        RAID_CHK="ERROR"
    }
    fi

}
```When I run the code above with crontab as super user, the command "mdadm --detail $RAID_DISK" returns a 1.  Assume that $RAID_DISK exists.

When I run the script by using the command prompt, then the command  "mdadm --detail $RAID_DISK" returns a 0.

Why is the exit code for the program mdadm different?

---

### Post by amauk on 2010-01-05
mdadm is in /sbin
/sbin is not, by default, in cron's path variable

use the absolute path to mdadm

```
function raid_check
{
    [COLOR="Red"]/sbin/mdadm[/COLOR] --detail $RAID_DISK
    if [ $? = 0 ]; then #check to see if $RAID_DISK is active
    {

```

---

### Post by david90 on 2010-01-05
Thanks. That solved the problem.

---

