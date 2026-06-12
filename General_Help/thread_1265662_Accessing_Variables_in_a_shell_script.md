---
title: "Accessing Variables in a shell script?"
date: 2009-09-13
forum: General Help
---

### Post by lightnb on 2009-09-13
I'm still confused about when to use brackets vs curly braces vs parenthesis, etc. and the script is producing "bad substitution" errors.


```

for (( i=$NUM_OF_COPIES_TO_KEEP-1; i > 0; i-- ))
do
   # Move file i-1 to i
   if [ -f ${$BACKUP_FOLDER$BACKUP_FILE_NAME"."${$i-1}"."$BACKUP_EXTENSION} ]
   then
      echo "File ${$i-1} exists, Moving to "$i
      SOURCE=$($BACKUP_FOLDER$BACKUP_FILE_NAME"."${$i-1}"."$BACKUP_EXTENSION)
      DEST=$($BACKUP_FOLDER$BACKUP_FILE_NAME"."$i"."$BACKUP_EXTENSION)
      mv $SOURCE $DEST
   else
      echo "File ${$i-1} Does Not Exist, Skipping..."
   fi
done

```

The purpose of this code is to move (rename) backup files incrementally, in preparation for creating a new one. For example: file.1 becomes file.2, file.0 becomes file.1, and then we can safely replace file.0 with the new backup.

---

### Post by Brandon Williams on 2009-09-14
The double parentheses, "(( ... ))" and "$(( ... ))", indicate arithmetic context. Whenever you are performing simple arithmetic against the variable, you'll want to put it inside double parentheses. This include the bash for loop construct that you've used. Bash allows double parentheses to go anywhere, while posix only allows them as part of a variable expansion (e.g. "$(( i - 1 ))"). Note that you don't need to put a '$' in front of the variable name to get substitution in arithmetic mode.

Brackets are used to mark the start and end of a string variable expansion when the start and end would not otherwise be obvious and/or when special expansion constructs are used. For example:
```
BACKUP_FILE=some.filename
BACKUP_FILE_EXTENSION=bkup
# the following would output some.filename_EXTENSION
echo ${BACKUP_FILE}_EXTENSION
# the following would output some.filename.bkup
echo $BACKUP_FILE_EXTENSION
# the following would print some.bkup
echo ${BACKUP_FILE%.*}$BACKUP_FILE_EXTENSION
```

Brackets are used to indicate array subscripts, as they are in most other programming languages. This is also not a feature of the posix shell, since arrays aren't supported by the posix shell.

And finally, "$( ... )" is used for command substitution, just like "` ... `".

So, with all of that in mind, here's a cleaned up version of your code that does what I think you want it to do:
```
for (( i=NUM_OF_COPIES_TO_KEEP-1; i > 0; i-- ))
do
   # Move file i-1 to i
   if [ -f "$BACKUP_FOLDER$BACKUP_FILE_NAME.$(( i-1 )).$BACKUP_EXTENSION" ]
   then
      echo "File $(( i-1 )) exists, Moving to $i"
      SOURCE="$BACKUP_FOLDER$BACKUP_FILE_NAME.$(( i-1 )).$BACKUP_EXTENSION"
      DEST="$BACKUP_FOLDER$BACKUP_FILE_NAME.$i.$BACKUP_EXTENSION"
      mv $SOURCE $DEST
   else
      echo "File $(( i-1 )) Does Not Exist, Skipping..."
   fi
done
```


PS: Questions like these should probably go in one of the forums related to programming; not general help.

---

### Post by lightnb on 2009-09-17
Thanks for the clarification and detailed explanation!

The script is working now.

---

