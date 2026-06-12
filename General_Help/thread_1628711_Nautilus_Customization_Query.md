---
title: "Nautilus Customization Query"
date: 2010-11-23
forum: General Help
---

### Post by kniwor on 2010-11-23
In short, I need to hide files with certain extensions from Nautilus. Here is a more detailed description of what and why I need.

I type all my documents in latex, and while compiling many files are created in a folder that clutter the view of Nautilus, and are never ever going to be useful for me. So I need a way to hide all the files with these extensions.


Here is what I currently do. I simply run the following command in that directory. 
```
ls *.bbl *.aux *.blg *.log > .hidden
```
The problem is I have to do this every time I create a new Latex document because new files with these extensions are created. Second problem, I need this to happen for an entire directory tree (system-wide if possible, I don't think I use those extensions for any purpose in other directories either, but if this means creating a .hidden file in each directory, it's probably not the best idea). 

One simple idea is to write a script that executes at startup and creates the .hidden file in each of the directories I desire, but this is not elegant by any stretch of imagination and doesn't do exactly what I want (does reduce the clutter though).

---

### Post by kniwor on 2010-11-23
Is this a complicated issue to solve? I was looking at the mautilus-actions and nautilus-scripts n such, can someone point me what these really are. Search gives up scripts and actions but not an explanation of what it really is.

---

### Post by kniwor on 2010-11-25
Still no lead?

---

### Post by Vaphell on 2010-11-25
assuming that your stuff is in 1 dir+subdirs, this is a raw script that pretty much does what is needed. It scans a given dir and its subdirs for filetypes and throws them into .hidden
```

#!/bin/sh

if [ -z "$1" ]
then
  selected_dir="$HOME/test"
  echo Default param: $selected_dir

else
  selected_dir="$1"
  echo User param: $selected_dir
fi


cd $selected_dir
find . -type d -exec sh -c 'cd "{}"; pwd; out=".hidden"; ls *.bbl *.aux *.blg *.log > $out; if [ ! -s $out ]; then rm $out; fi;' \; 

```

selected_dir defines which dir gets scanned recursively, by default it's got some hardcoded value of choice, but it can also accept user input ($1 = first parameter, if [ -z "$1" ] checks if it's null and uses default if necessary). You can use that parametrization in nautilus-actions.
n-actions is easy to figure out. Run nautilus-actions-config-tool, create new entry, name it whatever you want
command = script_name 
parameters = %d (or whatever help window tells you the symbol for selected dir is)
conditions on single/multiple select, files/dirs allowed... restart nautilus ('killall nautilus' if i am not mistaken), if the action is good, it will show up in context menu of defined object type (file/dir, extension, whatever...)
i think that you can run it in autostart, if you don't plan to scan whole home dir, it should be fast enough

launcher on the panel? command: **sh -c '<full_path>/script_name <dir to scan (optional)>'** or if you want without full path, put the script in some dir included in system path. (echo $PATH)

---

### Post by kniwor on 2010-11-26
Thanks a ton, let me try this and see how this works. Then will post back. Appreciate the help.

---

