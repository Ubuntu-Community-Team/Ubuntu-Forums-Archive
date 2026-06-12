---
title: "How do i use Lha better?"
date: 2010-02-16
forum: General Help
---

### Post by nightrazer on 2010-02-16
**Hello!**                              (* I use a Debian system 64-bit* )

I have been trying to use lha to unpack *.lha files on my system
and i haven't been able to use it for unpacking multiple files
just just using one at a time. this is what i did

**lha e (filename)**
and i melts and works fine on a single file

multiple files test
**Lha e *.lha**
and nothing...
i even tried** Lha x *.lha** and **Lha x,e *.lha**
didn't work either.. i think this worked years ago ](*,)

*however i did solve this graficly by selecting netmask *.lha and then unpack from the menu.. however i would like to be able to do this in a commandline. **any hints?***

i need them unpacked for me to use them in **uade123** for playing mods
just like i do in **Rythmbox**, however when **Rythmbox** listens to a format it has problems with, it [COLOR=Red]***[SIZE=2]crashes[/SIZE]***[/COLOR].. in fact so hard that **my Debiansytem froze**... 
i made i hard reset just to get out of it.. i couldn't switch screens or use the mouse.

---

### Post by gmargo on 2010-02-16
> **nightrazer said:**
> 
I have been trying to use lha to unpack *.lha files on my system
and i haven't been able to use it for unpacking multiple files
just just using one at a time.

According to the man page, **lha** operates on one archive at a time.

Here's a handy bash script that will gather up the *.lha files and extract each one.

```

#!/bin/bash
# Using bash to use arrays and arithmetic

# Put basenames of files in $NAMES[] array
declare -a NAMES
declare -i indx=0

# Allows file/directory names to contain spaces:
OIFS=$IFS
IFS='\

'
# Find all entries in this directory.
for FILE in `ls -d *.lha`
do
    NAMES[indx++]=$FILE
done

# Switch back to normal field separator
IFS=$OIFS

#echo "There are ${#NAMES[@]} entries:"
for (( indx=0 ; indx < ${#NAMES[@]} ; indx++ ))
do
    FILE=${NAMES[indx]}

    if [ -f "$FILE" ]; then
        echo "Extracting \"$FILE\""
        lha x "$FILE"
    else
        echo "\"$FILE\" is not a file"
    fi
done


```Or of course the classic:
```

find . -type f -name '*.lha' -print -exec lha x {} \;

```

---

