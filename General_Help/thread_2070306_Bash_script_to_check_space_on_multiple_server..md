---
title: "Bash script to check space on multiple server."
date: 2012-10-12
forum: General Help
---

### Post by melc_sokat on 2012-10-12
Hello.

I`m a noob in scripting and i need a bash script to check disk space on multiple server. All i want is to run the scrip from my server and then see on console free disk space on other.
So far i only managed to get log on those server via ssh without password run the DF -HP comand. But i don`t know how to set the output ! Anyone able to help me.


#!/bin/bash
ssh -p 22 user@host  df -HP  > /tmp/df.out
ssh -p 22 user@host  df -HP  > /tmp/df.out
ssh -p 22 user@host  df -HP  > /tmp/df.out

cat /tmp/df.out | grep -vE '^Filesystem|tmpfs|cdrom' | awk '{ print $5 " " $1 }' | while read output;
do
  #echo $output
  usep=$(echo $output | awk '{ print $1}' | cut -d'%' -f1  )
  partition=$(echo $output | awk '{ print $2 }' )
 [COLOR="Red"]   echo "Running out of space \"$partition ($usep%)\" on $(hostname) as on $(date)"
fi
done[/COLOR]

Where is red text i got problems.

Any help apreciated.

---

### Post by Habitual on 2012-10-12
[noparse]```

```[/noparse] tags Please.
Thank you.


That being said:
```
#!/bin/bash
set -x
...

```

---

### Post by melc_sokat on 2012-10-12
```

raton@ubuntu:~/Script$ ./p
+ ssh -p 22 raton@192.168.81.135 df -H
+ ssh -p 22 raton@192.168.81.131 df -H
+ ssh -p 22 raton@192.168.81.133 df -H
./p: line 18: syntax error: unexpected end of file

```

---

