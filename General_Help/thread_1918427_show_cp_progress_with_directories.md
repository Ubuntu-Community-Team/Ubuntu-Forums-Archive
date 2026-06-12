---
title: "show cp progress with directories"
date: 2012-01-31
forum: General Help
---

### Post by buffchick on 2012-01-31
So, I'm finding tons of nifty little bash scripts, scp tips, rsync tips, etc etc for copying one file to a destination while showing the progress of that copy, however, how would I go about doing this for a directory with sub-directories (cp with -r flag)

i.e. show progress for ```
cp -r /mnt/storage/media /mnt/usb/linuxbak
``` or something similar where media has a dozen files and a dozen sub-directories with files.

All help appreciated in advance! THANKS!

p.s. Running ubuntu server 11.10 so need CLI info!! :D

---

### Post by Dumbestcrayon on 2012-01-31
I believe you're looking for the term "verbose."

In the man page for cp you'll see the following 


```
       -v, --verbose
              explain what is being done

```

add a -v to your command like so

```
cp -rv /mnt/storage/media /mnt/usb/linuxbak
```

or

```
cp -r -v /mnt/storage/media /mnt/usb/linuxbak
```

---

### Post by buffchick on 2012-02-01
ah, no. I"m familiar with the verbose option. To clarify, I'm not looking to see every file copied, I'm more looking to see a progress meter much like wget.

---

### Post by Dumbestcrayon on 2012-02-01
EDIT: I found some scripts on another website that will be useful.

[Credit]("http://www.unix.com/302197445-post2.html")

```
#!/bin/bash
# Example: ./test original_file destination_file
usage()
{
   echo "Usage: $0 original_file destination_file"
   exit 1;
}

test $# == 2 || usage
orig_size=$(stat -c %s $1)

>$2
dest_size=0
cp -f $1 $2 &

while [ $orig_size -gt $dest_size ] ; do
   dest_size=$(stat -c %s $2)
   pct=$((( 69 * $dest_size ) / $orig_size ))

    echo -en "\r["
    for j in `seq 1 $pct`; do
        echo -n "="
    done
    echo -n ">"
    for j in `seq $pct 68`; do
        echo -n "."
    done
    echo -n "] "
    echo -n $((( 100 * $pct ) / 69 ))
    echo -n "%"
done
echo
```


This one is good but it only works with a single file. You could easily wrap that with another script that operates recursively. I would do that to keep the two separated. The second script would scan a directory recursively running the script above on each file.

I'd gladly write it for you, but it's midnight here and it's time for me to get some sleep. I'll surely give it a go in the morning though.

---

### Post by buffchick on 2012-02-01
wow thanks. And yeah, I've seen a lot of these bash scripts that would work on individual files but eh, I couldn't figure out how to make them work recursively. And I totally understand the time thing. I'm in Austin. :D

---

