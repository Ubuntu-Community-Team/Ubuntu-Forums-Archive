---
title: "A little script help please?"
date: 2009-10-10
forum: General Help
---

### Post by t0p on 2009-10-10
I want to keep a log of the size of my SSD to see how quickly it wears out. So I want a script to do the following:

When called, it will print the date;

Then it runs the command df:

```
t0p@deimos:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              3842376   2762696    884492  76% /
tmpfs                  1027472         0   1027472   0% /lib/init/rw
varrun                 1027472       124   1027348   1% /var/run
varlock                1027472         4   1027468   1% /var/lock
udev                   1027472       172   1027300   1% /dev
tmpfs                  1027472        76   1027396   1% /dev/shm
/dev/sdc1              3928964   1113104   2616280  30% /home
/home/t0p/.Private     3928964   1113104   2616280  30% /home/t0p/Private
/dev/sdb1            387630708  16288020 351807248   5% /media/disk

```

It extracts the disk space, from the line beginning /dev/sda1, and prints that next to the date:

```
10/10/2009     3842376
```

So what commands should I look at for this?

---

### Post by slakkie on 2009-10-10
```

#!/usr/bin/env bash

# You might want to use some kind usage thing here
[ -z "$1" ] && exit 1

_date=$(date "+%Y%m%d")

for i in $* ; do
    echo -n "$_date "
    df -k $i | tail -1 | awk '{print $2, $3}'
done

```

I'll leave the rest up to you

---

### Post by delcypher on 2009-10-10
Just in case you don't know how to implement slakkie's script (nice script by the way)

1. save the script to a file e.g. myscript.sh
2. Make the script executable using the command (where /path/to is the directory your script is in)
```
chmod u+x /path/to/myscript.sh
```
3. slakkies's script is design so that it needs at least one argument. example usage would be```
./myscript /home /dev/sda1
```
This would show the disk usage for the drive that has /home on it and the usage of the drive /dev/sda1 

of course you can just can use the name of the mount point instead of /dev/sda1

Have fun!

---

### Post by t0p on 2009-10-10
Thanks slakkie!  And thanks delcypher (I don't think I could have understood it without your help).
Thanks!!! :)

---

### Post by t0p on 2009-10-10
Back again! with a couple of questions.

I want the output of this script to go into a file.  I know how to get it to send the date to the file:

```
echo -n "$_date " >> file
```

but I don't know how to make the next line send the disk size data to the file.

Also, I want each day's data to appear on a different line.  How do I do that?

---

### Post by ppirilla on 2009-10-10
I think what you want to do is run the command "./myscript /dev/sda1 >> file"

---

### Post by prshah on 2009-10-10
> **t0p said:**
> I want to keep a log of the size of my SSD to see how quickly it wears out. So I want a script to do the following:
```
10/10/2009     3842376
```


You can also try```
logger $(date "+%Y/%m/%d") `df  | grep sda1|awk '{print  $2 }'`
```

logger is a program that writes directly to the debug log (dmesg).

Put that line in a simple text file, make it executable, and you can even have it called by cron periodically. Post back if you want more details.

---

### Post by t0p on 2009-10-10
> **ppirilla said:**
> I think what you want to do is run the command "./myscript /dev/sda1 >> file"

That did the trick!  Thanks ppirilla!

---

