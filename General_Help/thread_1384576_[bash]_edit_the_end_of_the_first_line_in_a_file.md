---
title: "[bash] edit the end of the first line in a file?"
date: 2010-01-18
forum: General Help
---

### Post by GenDeath on 2010-01-18
I'm wondering if I can create a bash script that once executer will edit or replace a line a in a file this line is the first one and its just one character that needs to be changed from a 1 to a 0.

How do I go about this?
it is for a game called EVE Online, heres what my .sh look like atm

#!/bin/sh
echo fixing prefs.ini

#fix for prefs goes here

echo starting eve
eve

---

### Post by Portmanteaufu on 2010-01-18
Sure, that's doable. How do you want to specify which line in the file?

By line number?

---

### Post by DaithiF on 2010-01-18
you could do this in lots of ways.  Using sed, an example might be:

1. by line number -- only change the first line:
```
sed -i '1s/1/0/' somefile

```2. by matching a specific string anywhere in the file
```
sed -i '/someconfigsetting: 1/s/1/0/' somefile
```or
```
sed -i 's/someconfigsetting: 1/someconfigsetting: 0/' somefile
```

note that the -i parameter will make changes in-place to the file.  You probably want to leave out this paramter while you're testing to make sure you're getting the right result -- without -i the amended file will be output to the terminal for you to view.  Once you're happy with the result, then run again with -i.

---

### Post by Portmanteaufu on 2010-01-18
Here's one way of doing it with Bash. There are probably easier ones.

```

#!/bin/bash
FILE=$1
LINE=$2
NEW_LINE=$3
FILE_SIZE=`cat $FILE | wc -l`

HEADN=`expr "$LINE" - 1`
TAILN=`expr "$FILE_SIZE" - "$LINE"`
TOP=`head -n $HEADN $FILE`
BOTTOM=`tail -n $TAILN $FILE`
if [ -n "$TOP" ]
then
        echo "$TOP" > junk
fi
echo "$NEW_LINE" >> junk
if [ -n "$BOTTOM" ]
then
        echo "$BOTTOM" >> junk
fi
mv junk $FILE

```

You would run it as:

```

script_name [File Name] [Line to Change] [New Contents of that line]

```

e.g.

```

script_name 'game.conf' 27 'can_cheat=true'

```

---

### Post by Portmanteaufu on 2010-01-18
Hoo boy -- thanks to DaithiF for reminding me that I was re-inventing the wheel.

You can do everything my last post did with this sed command: 

```

sed -i '<LINE NUMBER>s/.*/<NEW LINE>/' FILENAME

```

To use my previous example: 

```

sed -i '27s/.*/can_cheat=true/' game.conf

```

If you were dying to wrap some shell code around it, you could do this in your bashrc:

```

function line_mod() {
   USAGE="USAGE: line_mod [filename] [line number] [new line]"
   if [ -z "$1" -o -z "$2" -o -z "$3" ] 
   then
       echo "$USAGE"
       return 1
   fi
   sed -i $2's/.*/'$3'/' $1
}

```

and call it with:

```

line_mod game.conf 27 'can_cheat=true'

```

---

