---
title: "cp command tweaks"
date: 2012-06-15
forum: General Help
---

### Post by xxsmarty on 2012-06-15
I have been writing a shell script for copying data from removable disks secretly but all I have done is this , some I got from Internet and some from my side.
I want a progress bar (simple) just to tell how much copying has been done.
I am not med in shell program so please explain whatever you do.
Please help me.
```

#!/bin/bash -x
#my copy version

targ="/media/Disk E:/my/"


#if [ $1 = "t" ];
#then
echo "Enter the target name"
read targ
#fi


echo "Enter the source:"
read source
dest_size=0
org_size=$(stat -c %s $source)
cp -r -f -v  "$source" "$targ" & 
while [ $orig_size -gt $dest_size ] ; do
   dest_size=$(stat -c %s $targ)
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

---

### Post by Charlietje on 2012-06-15
Dear,

Install pv
```
sudo apt-get install pv
```

my shell script is called  **bcp** and is located at **/usr/local/bin/**:


```
#!/bin/sh


if [ $# -ne 2 ]; then
	echo "Usage: bcp source destination"
	exit
fi

SIZE=`du -b "$1" | cut -f 1`
echo $SIZE


if [ -d "$2" ]; then
	pv -p -e -r -s $SIZE "$1" > "$2"/"$1"
else
	pv -p -e -r -s $SIZE "$1" > "$2"
fi
```

---

### Post by xxsmarty on 2012-06-15
Thank you very much , you have solved my problem.

---

### Post by xxsmarty on 2012-06-15
Can you tell me some more about the pv command.
Here I have some problem
```

pv -p -e -r -s $size [COLOR=Red]"$1" > "$2"/"$1"[/COLOR]

```
```

    pv -p -e -r -s $size [COLOR=Red]"$1" > "$2"[/COLOR]

```

---

