---
title: "Script assistance please?"
date: 2012-02-14
forum: General Help
---

### Post by Cool Javelin on 2012-02-14
Help, I am having difficulties with a script I made to cleanup some videos from my surveillance cameras.

The script is called from crontab each night, so it is running with root privileges.
If I call the script from the command line with sudo it works.

I am using Motion to capture both stills and videos from a camera I have outside and want to delete the old stuff after 25 days.
The videos are stored in /80G/MotionVideos/Camera1
Then I have snapshots and mpeg_motion under that, then I have each day in a separate directory.

```
mark@Legolas:/80G/MotionVideos/Camera1$ ls -l
total 8
drwxrwxrwx 27 root root 4096 2012-02-14 02:12 mpeg-motion
drwxrwxrwx 27 root root 4096 2012-02-14 02:12 snapshot
mark@Legolas:/80G/MotionVideos/Camera1$

```

```
mark@Legolas:/80G/MotionVideos/Camera1$ cd snapshot
mark@Legolas:/80G/MotionVideos/Camera1/snapshot$ ls -l
total 27844
drwxrwxrwx 2 root root 1159168 2012-01-21 23:59 2012-01-21
drwxrwxrwx 2 root root 1159168 2012-01-22 23:59 2012-01-22
drwxrwxrwx 2 root root 1159168 2012-01-23 23:59 2012-01-23
drwxrwxrwx 2 root root 1159168 2012-01-24 23:59 2012-01-24
drwxrwxrwx 2 root root 1159168 2012-01-25 23:59 2012-01-25
drwxrwxrwx 2 root root 1159168 2012-01-26 23:59 2012-01-26
drwxrwxrwx 2 root root 1159168 2012-01-27 23:59 2012-01-27
drwxrwxrwx 2 root root 1159168 2012-01-28 23:59 2012-01-28
drwxrwxrwx 2 root root 1159168 2012-01-29 23:59 2012-01-29
drwxrwxrwx 2 root root 1159168 2012-01-30 23:59 2012-01-30
drwxrwxrwx 2 root root 1159168 2012-01-31 23:59 2012-01-31
drwxrwxrwx 2 root root 1159168 2012-02-01 23:59 2012-02-01
drwxrwxrwx 2 root root 1159168 2012-02-02 23:59 2012-02-02
drwxrwxrwx 2 root root 1159168 2012-02-03 23:59 2012-02-03
drwxr-xr-x 2 root root 1159168 2012-02-04 23:59 2012-02-04
drwxr-xr-x 2 root root 1159168 2012-02-05 23:59 2012-02-05
drwxr-xr-x 2 root root 1159168 2012-02-06 23:59 2012-02-06
drwxr-xr-x 2 root root 1159168 2012-02-07 23:59 2012-02-07
drwxr-xr-x 2 root root 1159168 2012-02-08 23:59 2012-02-08
drwxr-xr-x 2 root root 1159168 2012-02-09 23:59 2012-02-09
drwxr-xr-x 2 root root 1159168 2012-02-10 23:59 2012-02-10
drwxr-xr-x 2 root root 1159168 2012-02-11 23:59 2012-02-11
drwxr-xr-x 2 root root 1159168 2012-02-12 23:59 2012-02-12
drwxr-xr-x 2 root root 1159168 2012-02-13 23:59 2012-02-13
drwxr-xr-x 2 root root  659456 2012-02-14 12:58 2012-02-14
mark@Legolas:/80G/MotionVideos/Camera1/snapshot$

```

This script has been running a few days, please note the permissions.

On Feb 3, I manually changed the permissions to allow anyone to remove the folders.

The folders that have been changed to 0777 can be removed by the script. Although it is not being shown here, the folders being created by motion (permissions 0755) are not being removed each night.

Here is the script:

```
mark@Legolas:~$  cat /usr/local/sbins/KillOldSurveillance

#!/bin/bash

# set some variables with some dates
today_dir=`date +%F`
yesterday_dir=`date -d "-25 days" +%F`

echo today is $today_dir >> /home/mark/KillOldSurveillance.log
echo yesterday is $yesterday_dir >> /home/mark/KillOldSurveillance.log

# remove all camera directories that are too old
rm -r /80G/MotionVideos/Camera1/snapshot/$yesterday_dir
rm -r /80G/MotionVideos/Camera1/mpeg-motion/$yesterday_dir

# This added because the above didn't work
# now change the permissions of the current date to allow deletion later
chmod -R 777 /80G/MotionVideos/Camera1/snapshot/$today_dir
chmod -R 777 /80G/MotionVideos/Camera1/mpeg-motion/$today_dir

```

Here is the output of the log I made (see first few lines of the script)

```
mark@Legolas:~$ tail KillOldSurveillance.log
today is 2012-02-10
yesterday is 2012-01-16
today is 2012-02-11
yesterday is 2012-01-17
today is 2012-02-12
yesterday is 2012-01-18
today is 2012-02-13
yesterday is 2012-01-19
today is 2012-02-14
yesterday is 2012-01-20

```

When it wasn't working, I added the bottom part to the script to change each directory permissions so the next time the script ran it could do it's thing. But all I did was defer the problem as the permissions are not being changed each night. I'd rather just be able to delete them directly.

Thanks for your help, Mark.

---

### Post by Krytarik on 2012-02-14
Although I don't know the culprit of your permissions issue - as long as you are running the script via root's crontab, not your own, of course* - why don't you simply set up your script like this? ;-) :
```
#!/bin/bash

# set some variables with some dates
today_dir=`date +%F`
yesterday_dir=`date -d "-25 days" +%F`

echo today is $today_dir >> /home/mark/KillOldSurveillance.log
echo yesterday is $yesterday_dir >> /home/mark/KillOldSurveillance.log

# change the permissions of the directories up for deletion
chmod -R 777 /80G/MotionVideos/Camera1/snapshot/$yesterday_dir
chmod -R 777 /80G/MotionVideos/Camera1/mpeg-motion/$yesterday_dir

# remove all camera directories that are too old
rm -r /80G/MotionVideos/Camera1/snapshot/$yesterday_dir
rm -r /80G/MotionVideos/Camera1/mpeg-motion/$yesterday_dir
```* However, changing the permissions also wouldn't be possible then.

Regards.

---

### Post by Cool Javelin on 2012-04-20
Well, this seems to be working. I don't know why the earlier one didn't, but this is solved now.

Thanks.


```
#!/bin/bash

# set some variables with some dates
today_dir=`date +%F`
yesterday_dir=`date -d "-25 days" +%F`

echo today is $today_dir >> /home/mark/KillOldSurveillance.log
echo yesterday is $yesterday_dir >> /home/mark/KillOldSurveillance.log

# remove old directorys
rm -r /80G/MotionVideos/Camera1/snapshot/$yesterday_dir
rm -r /80G/MotionVideos/Camera1/mpeg-motion/$yesterday_dir
```

---

