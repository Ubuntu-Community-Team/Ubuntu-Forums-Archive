---
title: "Bash script to move file to the trash"
date: 2012-08-21
forum: General Help
---

### Post by Stonecold1995 on 2012-08-21
I'm trying to create a Bash script which will move files to the trash, basically something that does the same thing as "kioclient move file1 file2 file3 trash:/" but more easily.  This is the script so far:

```
#!/bin/bash

IFS=" " # is this really needed?

# make sure a file to throw away is specified
if [ "$1" = "" ]; then
   echo -e "trash: missing operand\nTry 'trash --help' for more information"
   exit 1
fi

# if --help is passed on to the script, display the help
if [ "$1" = "-h" -o "$1" = "--help" ]; then
   cat << _EOF
Usage: trash FILE(s)...
Move FILE(s) to the trash (same as 'kioclient move FILE(s) trash:/').

  -h, --help     display this help and exit

_EOF
   exit 0
fi

# go through each file, and if it's a directory tell the user that it
# can't be trashed (Todo: impliment a --recursive option to bypass this,
# and a --verbose option to explain what's happening)
for target in "$@"; do
   if [ -f $target ]; then
      kioclient move $target trash:/
   else
      echo "trash: omitting directory '$target'"
   fi
done
exit 0
```

I plan to move this script to /usr/local/bin so that I can run "trash file1 file2 file3" much like I could run "rm file1 file2 file3".  So my question is, how do I add an option to make it verbose, how do I add an option to make it recursive?  Currently, if I pass on any parameters that don't cause the script to exit (like --help does), then it will try to send the parameter to the trash.  For example, if I were to add a verbose feature so the command is "trash -v file1 file2 file3" it would make it verbose, BUT it would try to send "-v" to the trash, which obviously is impossible as it isn't a file.

I'm relatively new to Bash scripting so some of this gets really confusing to me.

---

### Post by asmoore82 on 2012-08-22
No, mangling the IFS should not be necessary. I've never seen a situation where there wasn't a cleaner solution than IFS hacks. As Master Yoda said "quicker, easier, more seductive; but not stronger."

The magic bit you are missing is **shift**.

The shift command (actually a bash shell builtin I believe) "rotates" down command line arguments so you process multiple or none at all cleanly before moving on to actually doing the job.

So you get into a structure like this:
```
[COLOR="Blue"]#pseudo script for command line arg processing[/COLOR]
until [ -z "$1" -o -f "$1" ]
do
    case "$1" in
        "-v"|"--verbose")
             #be verbose is now true
             **shift**
             ;;
        "-f"|"--force")
             #forceful is now true
             **shift**
             ;;
        *)
             #unrecognized arg
             **shift**
             ;;
    esac
done
```

Note that this structure doesn't allow arguments after the first file. But it also allows a user to successfully delete a file named "--verbose" or "--force" without further complication. The alternative, and what GNU `rm` actually does, is to test for a leading dash so that the only way to delete such a file is by full or relative path "./--verbose" - then you could get 1 step fancier and allow a lone double dash to always terminate arguments and move on to filenames no matter how strange the names :P.

In other words, the bash logic for the `rm` behaviour could be something like this:
```
while [ "${1:0:1}" = "-" ]
do
    #...
done
```

---

### Post by Vaphell on 2012-08-22
you can end switch segment with --, after that everything is treated as a name.
```
$ > -v
$ rm -v
rm: missing operand
Try `rm --help' for more information.
$ rm -- -v
$
```

---

