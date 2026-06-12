---
title: "Is there a clipboard manager (or other way) that can do this?"
date: 2012-09-13
forum: General Help
---

### Post by scottkosty on 2012-09-13
Suppose I want to copy a name, say "Bob Smith", and an email, say "bsmith@clipit.rspwn.com" from a document, into 
a form that has three fields:
(1) "First Name", (1) "Last Name", and (3) email
I would like to be able to copy "Bob", then copy "Smith", then "copy [email]bobsmith@clipit.rspwn.com[/email]" and then go to the form and paste one after the other. It would be nice if after I pasted one, it was deleted from ClipIt so I don't even have to go to the history and select the next one, it's already loaded and ready to go. I think a fitting name could be "pop mode" where after you paste 
something, that entry just pop's off.

I find myself in the above situation every day and would like to solve this problem.

I posted a feature request for ClipIt here:

[https://github.com/shantzu/ClipIt/issues/17](https://github.com/shantzu/ClipIt/issues/17)

I know C++ and would be willing to try to implement this proposed feature in a C or C++ based clipboard manager if someone could guide me.

Thanks,

Scott

---

### Post by Vaphell on 2012-09-13
it should be rather easy to whip up few short scripts to do something like that, using xsel, xdotool and zenity in case of guification and binding these scripts to hotkeys.

to save:
```
#!/bin/bash

# dump current selection to a file
xsel -po > "$(date +%F_%T_%N).sel"
```

to retrieve:
```
#!/bin/bash

shopt -s nullglob

# exit if there are no .sel files
sel=( *.sel )
if (( ${#sel[@]}==0 )); then exit; fi

# window with contents of files, selection returns the file name 
z_params="--list --column=file --column=1st-line --hide-header --hide-column=1 --width=500 --height=200"
s=$( zenity --title="Buffer contents" $z_params < <( for f in *.sel; do echo -e "$f\n$( head -1 "$f" )"; done ) )

# load the selected file to the buffer
xsel -pi < "$s"

# emulate middle click to paste
xdotool click 2

# remove selected file
rm "$s"
```
or
```
#!/bin/bash

shopt -s nullglob

# exit if there are no .sel files
sel=( *.sel )
if (( ${#sel[@]}==0 )); then exit; fi

# select first file
s="${sel[0]}"

# load the selected file to the buffer
xsel -pi < "$s"

# emulate middle click to paste
xdotool click 2

# remove selected file
rm "$s"

```

---

### Post by Habitual on 2012-09-14
> **Vaphell said:**
> ```
#!/bin/bash

shopt -s nullglob

# exit if there are no .sel files
sel=( *.sel )
if (( ${#sel[@]}==0 )); then exit; fi

# window with contents of files, selection returns the file name 
z_params="--list --column=file --column=1st-line --hide-header --hide-column=1 --width=500 --height=200"
s=$( zenity --title="Buffer contents" $z_params < <( for f in *.sel; do echo -e "$f\n$( head -1 "$f" )"; done ) )

# load the selected file to the buffer
xsel -pi < "$s"

# emulate middle click to paste
xdotool click 2

# remove selected file
rm "$s"
```

very clever solution!

---

### Post by Frogs Hair on 2012-09-14
Clipit and Parcellite both in the software center if you prefer an application. The script looks like good solution though. :)

---

### Post by scottkosty on 2012-09-15
> **Vaphell said:**
> it should be rather easy to whip up few short scripts to do something like that, using xsel, xdotool and zenity in case of guification and binding these scripts to hotkeys.


Thank you very much Vaphell! I didn't know you could write a clipboard manager with such minimal code. Very nice!

I  think I wasn't clear enough in my original post. Thanks to your useful  scripts I've got a couple of scripts that do what I want -- they paste  in the same order that I copied (so no GUI needed for choosing).

A couple of notes to anyone who happens across this thread and is interested:
(1)  These don't work perfectly. Sometimes the paste just doesn't paste (and  it does pop). I did not find any error. I think the xdotool click was successfully dispatched (return code is 0) so I'm not sure what's going on.

(2)  You will paste into where your mouse is hovering over, not where your  cursor is. This is unfortunate but it's exactly this behavior (cleverly  thought of by Vaphell) that allows the whole process to work.

(3) I mapped save.sh to ctrl + alt + c and retrive.sh to ctrl + alt + v. Do what works for you.

Any  critiques of the scripts are welcomed and I will post updates of the  scripts on this post in the future if I have reason to. If you think of  an alternative implementation, please post your finding.

save.sh:
```

#!/bin/bash

storageDir='/tmp/PopPaste'

if [ ! -d "$storageDir" ]; then
  mkdir "$storageDir"
  echo "0" > "$storageDir"/numberSaved
fi

cd "$storageDir"

if [ -e numberPasted ]; then
  # Once you start pop-pasting, either finish or start over copying again.
  rm numberPasted
  echo "0" > numberSaved
fi

numSaved=0
if [ -e numberSaved ]; then
  numSaved=$( cat numberSaved )
fi

numSaved=$(( $numSaved + 1 ))
echo $numSaved > numberSaved

# Dump current selection to a file.
xsel -po > $numSaved


```retrive.sh:
```

#!/bin/bash

storageDir='/tmp/PopPaste'

if [ ! -d "$storageDir" ]; then
  # save.sh should have created this directory. Are you pasting before copying?
  exit 1
fi

cd "$storageDir"

numPasted=0
if [ -e numberPasted ]; then
  numPasted=$( cat numberPasted )
fi

numPasted=$(( numPasted + 1 ))

if [ ! -e $numPasted ]; then
  # save.sh deleted numPasted if you copied without exhausting clipboard.
  exit 2
fi

echo $numPasted > numberPasted

xsel -pi < $numPasted

# emulate middle click to paste.
xdotool click 2

rm $numPasted

onePlus=$(( $numPasted + 1 ))
if [ ! -e $onePlus ]; then
  # We pasted the last element in the clipboard.
  rm numberSaved
  rm numberPasted
fi

```

---

### Post by 3rdalbum on 2012-09-15
This thread just shows how useful Linux is. On Windows you'd need about 2000 lines of C code that touches undocumented APIs; on Ubuntu somebody can whip up a solution for you in Bash in about ten minutes.

---

### Post by scottkosty on 2012-09-15
> **3rdalbum said:**
> this thread just shows how useful linux is. On windows you'd need about 2000 lines of c code that touches undocumented apis; on ubuntu somebody can whip up a solution for you in bash in about ten minutes.

+1

---

