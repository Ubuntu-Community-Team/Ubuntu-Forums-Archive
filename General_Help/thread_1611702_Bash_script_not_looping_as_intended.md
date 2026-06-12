---
title: "Bash script not looping as intended"
date: 2010-11-02
forum: General Help
---

### Post by The Fold on 2010-11-02
Hi,

I've written a bash script to connect to each machine in our local network and update the fstab file to point certain NFS mounts to a new location.

The script is meant to read in a list of shares and a list of workstations, rsync the relevant share then connect to each workstation and update the fstab file before moving onto the next share.

In reality what is happening is it will perform the loop correctly for the first workstation in the list but will not move on to the next one. I'm really stumped on this and I'm sure it's something simple but I just can't seem to work out the answer!

```

#!/bin/bash

SHARES=$1
HOSTS=$2

while read share;
do

        rsync -av /mnt/volume/1/midas/data/${share}/ linc:/mnt/volume/1/midas/data/${share};

        while read host;
        do
                FILE=fstab-${host}
                `scp ${host}:/etc/fstab ./$FILE`;
                echo "old -> `grep ${share} ./$FILE | cut -f1 -d ' '`";
                echo "old-mount -> `ssh -T ${host} "mount | grep ${share} | cut -f1 -d ' '"`";
                `ssh -T ${host} "umount /var/lib/midas/data/${share}"`
                `cp -f $FILE $FILE-old`
                `sed -i "s/\(172.16.0.30\)\(.*\)\(${share}\)\(.*\)/172.16.0.35\2\3\4/" $FILE`;
                echo "new -> `grep ${share} ./$FILE | cut -f1 -d ' '`";
                `scp ./$FILE root@${host}:/etc/fstab`;
                `ssh -T ${host} 'mount -a'`;
                echo "ssh -> ${host}";
                echo "fstab = $FILE";
                echo "share = ${share}";

                `rm -f $FILE`;

        done < "$HOSTS"

done < "$SHARES"

```

---

### Post by DaithiF on 2010-11-02
Hi, Can I assume SHARES and HOSTS are space delimited lists, and that you pass them to your script enclosed in quotes, e.g.:
```
yourscript "share1 share2 share3" "host1 host2 host3" 

```?

if so, you have a couple of issues with the way you are looping.

1. this construct:
```
while read x
do
...
done < [COLOR=Red]something[/COLOR]

```
requires **something** to be a file from which the while loop will read its input.  It can't just be a string (as it is in your case).  You could change it in any of the following ways:
```
while read x
do
...
done <<< "$shares"

```
or
```
while read x
do
...
done < <(echo $shares)
```

or 
```
echo $shares  | while read x
do
...
done

```

But: this won't actually achieve what you want, since you want to split $shares up into its components.  So instead do:
```
for share in $shares
do
   echo $share
done

```

---

### Post by The Fold on 2010-11-02
> **DaithiF said:**
> Hi, Can I assume SHARES and HOSTS are space delimited lists, and that you pass them to your script enclosed in quotes, e.g.:
```
yourscript "share1 share2 share3" "host1 host2 host3" 

```?



Both are regular text files in the format of:

share1
share2
...

workstation1
workstation2
...

> **DaithiF said:**
> 
But: this won't actually achieve what you want, since you want to split $shares up into its components.  So instead do:
```
for share in $shares
do
   echo $share
done

```

I adjusted for this and ran as suggested i.e. script "share1 share2" "workstation1 workstation2" and this works great, although I'd prefer to have the required shares/workstations listed in a file.

---

### Post by DaithiF on 2010-11-02
> **DaithiF said:**
> Hi, Can I assume SHARES and HOSTS are space delimited lists, and that you pass them to your script enclosed in quotes, e.g.:
```
yourscript "share1 share2 share3" "host1 host2 host3" 

```?

what an odd assumption that was for me to make :) ... it makes much more sense that they be files.  
Ok, so what does the simplest possible case produce?

```
SHARES=$1
HOSTS=$2

while read share
do
   echo "Share: $share"
   while read host
   do
      echo "Host: $host"
   done < "$HOSTS"
done < "$SHARES"
```

---

### Post by The Fold on 2010-11-02
> **DaithiF said:**
> what an odd assumption that was for me to make :) ... it makes much more sense that they be files.  
Ok, so what does the simplest possible case produce?

```
SHARES=$1
HOSTS=$2

while read share
do
   echo "Share: $share"
   while read host
   do
      echo "Host: $host"
   done < "$HOSTS"
done < "$SHARES"
```

That's OK, I'm glad for the help! :)

Right, that example produces what I would expect:

```

Share: share1
Host: host1
Host: host2
Share: share2
Host: host1
Host: host2
...

```

---

### Post by DaithiF on 2010-11-02
Ok, so the problem is in here:
```
    FILE=fstab-${host}
    `scp ${host}:/etc/fstab ./$FILE`;
    echo "old -> `grep ${share} ./$FILE | cut -f1 -d ' '`";
    echo "old-mount -> `ssh -T ${host} "mount | grep ${share} | cut -f1 -d ' '"`";
    `ssh -T ${host} "umount /var/lib/midas/data/${share}"`
    `cp -f $FILE $FILE-old`
    `sed -i "s/\(172.16.0.30\)\(.*\)\(${share}\)\(.*\)/172.16.0.35\2\3\4/" $FILE`;
    echo "new -> `grep ${share} ./$FILE | cut -f1 -d ' '`";
    `scp ./$FILE root@${host}:/etc/fstab`;
    `ssh -T ${host} 'mount -a'`;
    echo "ssh -> ${host}";
    echo "fstab = $FILE";
    echo "share = ${share}";

    `rm -f $FILE`;
```
a couple of points:
1. only enclose a command in backticks (``) when you want to embed the ouput of that command in another command.  Compare these two commands:
```
echo huh?
`echo huh?`

```
the second produces an error because bash inserts the output of the backticked command into the current command and tries to execute it.  (There is no such command as 'huh?').  Only a couple of the commands above actually require backticks -- the ones where you are echoing something and embedding the result of a command in that echo statement.

2. No need for trailling ';' characters in bash

fix up those 2 issues and see where that gets you.

---

### Post by The Fold on 2010-11-02
All fixed!

Thanks for the help, it turns out is was the ssh commands causing the problem! I removed the echo commands as they were there for debugging really anyway.

Here's the final result:

```
#!/bin/bash

SHARES=$1
HOSTS=$2

while read share
do
        echo "Share: $share"
        rsync -a /mnt/volume/1/midas/data/${share}/ linc:/mnt/volume/1/midas/data/${share}

        while read host
        do
                echo "Host: $host"
                FSTAB=fstab-$host
                scp -q $host:/etc/fstab ~/$FSTAB
                ssh -Tf $host "umount /var/lib/midas/data/$share"
                cp -f ~/$FSTAB ~/$FSTAB-old
                sed -i "s/\(172.16.0.30\)\(.*\)\(${share}\)\(.*\)/172.16.0.35\2\3\4/" ~/$FSTAB
                scp -q ~/$FSTAB root@$host:/etc/fstab
                ssh -Tf $host 'mount -a'
                echo "$host done"

        done < "$HOSTS"

        echo "$share migrated"

done < "$SHARES"
```

---

