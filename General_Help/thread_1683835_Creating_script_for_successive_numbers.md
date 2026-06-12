---
title: "Creating script for successive numbers"
date: 2011-02-08
forum: General Help
---

### Post by whatthefunk on 2011-02-08
I want to write a bash script that will assign a successive number to a file if a file of the same name is moved into the same directory.  So if there is a file called Notes in a directory and another file called Notes is moved into the directory, it will call it Notes.2.  Anybody?
Thanks

---

### Post by DaithiF on 2011-02-08
which file do you want renamed, the existing one or the new one?

and what do you want to happen if Notes.2 already exists ... some possibilities:
1. overwrite it, 
2. name the new file Notes.X where X is the next available number not already used
3. rename Notes.2 -> Notes.3, (and Notes.3 -> Notes.4, etc) and having freed up Notes.2 then rename the new one to that.

---

### Post by whatthefunk on 2011-02-08
The second of th three.  If Note exists, I want the script to create Note.1.  If Note.1 exists, Note.2.  If Note.3 exists, then Note.4 etc.  If there is a Note.3 and a Note.5 but no Note.4, I want it to create Note.6.  Im close, but I cant get it exactly right and my script seems cumbersome....

Oh, and I want the new file to be renamed...

Thanks for the help!

---

### Post by sisco311 on 2011-02-08
Something like:
```
#!/usr/bin/env bash

err ()
{
  echo "$0: cannot stat \`$1\': No such file or directory"
  echo "USAGE: $0 SOURCE DEST"
  exit 1
} >&2

SOURCE="$1"
DEST="$2"

[ -f "$SOURCE" ] || err "$SOURCE"
[ -d "$DEST" ] || err "$DEST"

FILE="$(basename "$SOURCE")"

if [ -f "${DEST}/${FILE}" ]; then
  max=0
  DIR="$(pwd)"
  cd "$DEST"
  shopt -s nullglob
  for backup in "${FILE}."*; do
    nr=${backup#${FILE}.}
    if [[ "$nr" =~ ^[0-9]+$ ]]; then
      if (( nr>max )); then
        max="$nr"
      fi
    fi
  done
  cd "$DIR"
  max=$(( max + 1 ))
  mv -- "$SOURCE" "${DEST}/${FILE}.$max"
else
  mv -- "$SOURCE" "$DEST"
fi

```should do the trick.

---

### Post by DaithiF on 2011-02-08
beat me to it ... for variety:
```
#!/bin/bash

function usage() {
    echo "xmv is a wrapper for mv which on finding a file of the same name"
    echo "in the destination directory will name the new file filename.X where"
    echo "X is one greater than the suffix of any previously existing file"
    echo "of the same pattern"
    echo ""

    echo "Usage"
    echo "====="
    echo "$0 source target"
}

# bail out unless exactly 2 parameters passed
[[ $# -ne 2 ]] && { echo "$# parameters passed, this script requires 2"; usage; exit 1; }

source=$1
target=$2

# if source does not exist, bail out
[[ ! -e "$source" ]] && { echo "Source $source does not exist, exiting."; exit 1; }

# split source into file and directory
source_file=${source##*/}
source_dir=${source%/*}

# is target a directory
if [[ -d "$target" ]]; then
    # if so, then target filename is the same as source filename
    target_file="$source_file"
    target_dir="${target%/}"
else
    # else target is a file, so split it into filename and directory
    target_file=${target##*/}
    target_dir=${target%/*}
fi

# set nullglob so that the target.[0-9]* pattern expands to nothing if no such
#   files exist (rather than the literal target.[0-9]*
shopt -s nullglob

# Does target file already exist?
if [[ -e "$target_dir/$target_file" ]]; then
    # now we'll loop through all files in the target directory matching the
    # pattern, keeping track of the highest suffix seen
    max_found=0
    for f in "$target_dir/$target_file".[0-9]*
    do
        # get the numeric suffix from the end
        suffix=${f##*.}
        (( $suffix > $max_found )) && max_found=$suffix
    done
    # the suffix we will use will be max_found + 1 ... when no files were
    # found this gives the result we want of target.1
    next_suffix=$(( max_found + 1 ))

    target_file="$target_file.$next_suffix"
    echo "(target file mapped to $target_file)"
fi

mv "$source" "$target_dir/$target_file"

```

---

### Post by whatthefunk on 2011-02-09
Thanks guys!  Both those work perfectly!

---

