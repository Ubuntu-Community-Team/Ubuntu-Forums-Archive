---
title: "Nautilus how to right-click folder and add new sub-folder"
date: 2012-08-01
forum: General Help
---

### Post by Ralph L on 2012-08-01
I would like very much to be able to right-click a folder in nautilus and add a sub-folder within that folder.  Does anybody have a nautilus extension to do this?

Thanks in advance.

---

### Post by Vaphell on 2012-08-01
in terminal run
```
sudo apt-get install zenity
```
zenity allows for creating simple dialog windows which can be used to GUIfy shell scripts

create a script file under .gnome2/nautilus-scripts (ctrl+h to unhide hidden dirs like .gnome2), chosen name will be shown as an entry name in context menu. Make it executable
Its content
```
#!/bin/bash

subdir=$( zenity --entry --text="Enter name" )

while read sdir
do
  if [ -d "$sdir" ]
  then
    mkdir -p "$sdir/$subdir"
  fi
done <<< "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```
if everything is ok, Scripts group should appear in rightclick menu and under it you can find all nautilus-scripts you have.

n-s passes everything that is selected to the script, so you can create subdirs in multiple dirs. Also you should be able to create a longer sequence of subdirs if you enter names separated by / (dir1/dir2/dir3)

If you need more refined approach you can look into Nautilus Actions tool, which is roughly a more powerful version of nautilus scripts mechanism, but offers more knobs to control the behavior (ie, show entries only for filetypes, only for single or multiple selection, only for files/dirs...)

---

### Post by Ralph L on 2012-08-02
Vaphell

Thank you very much for responding.  I tried your script, first placing it in ralph/.gnome2/nautilus-scripts.  (This was the only file in nautilus scripts, although the folder was already there.)  However, it would not come up in the context menu, when I right-clicked a folder.  I also put a copy in /usr/share/nautilus-scripts as instructed by Nautilus scripts manager.  It still did not appear in the right-click context menu.

I ran it from Terminal and Zenity came up and asked for the name, but after I entered the name, it did not create a folder.  However, this is probably, because it was in the wrong environment (Terminal, not Nautilus).  I also ran it from Nautilus Actions, using %f as the working directory.  Zenity came up and asked for input, but again it did not create a folder.  As a side note, when I used Nautilus Actions, I had to put it in /usr/local/bin.  I could not make it run from $HOME/.gnome2/nautilus-scripts, but this is an issue with Nautilus Actions.

I also created a separate Nautilus Actions item with mkdir as the path, "untitled folder" as the parameter, and %f as the Working Directory.  This created the sub-folder "untitled folder" like I wanted, but I would like the "untitled folder" to be highlighted and ready to be renamed just by starting to type--like the standard Create Now Folder in the context menu.  As an alternative to using your script with Zenity, do you know how to make the mkdir newly created folder highlighted and ready for typing in the new name?

Note:  My scripting skills are almost non-existent.  I don't know what sdir is in your sript, and I don't know what the -d is in if [ -d "$sdir" ].  Also I didn't understand what "n-s" is in your comment.

Any further help would be appreciated.

Ralph

---

### Post by Vaphell on 2012-08-05
n-s was a shorthand for nautilus scripts, i didn't feel like typing it in full ;-)

did you make sure the script is executable when trying the nautilus scripts route? I think nautilus autodetects executable files in that location, at least in my case it did.

nautilus scripts passes the data in NAUTILUS_SCRIPT_SELECTED_FILE_PATHS variable, in form of paths separated by newlines. In such cases while loop is best
```
while read my_variable
do
  mkdir -p "${my_variable}/${new_subdir}"
done <<< "$some_multiline_string"
```

nautilus actions on the other hand passes selected objects as parameters and parameters are $1, $2, $3, ... or $@ for 'list of all params'
if you go the route with script parameters like in case of nautilus-actions, for loop is your friend
```
for my_variable in "$@"
do
  mkdir -p "${my_variable}/${new_subdir}"
done
```

sdir was simply my custom variable (in examples above shown as my_variable to showcase that the name is of user's choosing) to store the single item from the list
*while read **var*** puts current line from input in **var**, runs the loop body with it, and then reads another line and **var** gets new value. Loop body is executed, etc, etc, until the input data runs out.
*for **var** in "$@"* is the same, the loop goes over the list and executes the loop body for each value on it.

*if [ -d "$sdir" ]* is nothing groundbreaking, it checks if the object in question (stored currently in the loop variable) is a directory and only then attempts to run mkdir.

---

### Post by Ralph L on 2012-08-05
Well, this is embarassing.  The script has been in the context menu the whole time.  It was in a sub-folder under the name "Scripts", duh.  And it worked very well!!!  I just wasn't expecting it to be in a sub-folder.

Thank you so much.
Ralph

---

### Post by Vaphell on 2012-08-06
nautilus scripts does that, nautilus actions plants menu items at the top level so no additional navigation required. Changing the script to work with N-A is not that hard.

---

