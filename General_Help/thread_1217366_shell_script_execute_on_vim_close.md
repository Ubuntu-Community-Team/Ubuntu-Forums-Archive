---
title: "shell script execute on vim close"
date: 2009-07-19
forum: General Help
---

### Post by tacitdynamite on 2009-07-19
i'm trying to make an encrypted text journal using a shell script, vim, and truecrypt. i've made a script that checks and mounts a truecrypt container at ~/journal, opens a new gnome-terminal in a directory inside the mounted truecrypt container, creates a new datestamped text file, and opens it up in vim.

what i need: a way to automatically de-mount the journal volume after i've exited vim. should i / can i do this in the shell script that calls vim? or does somebody know a vim option that lets you execute a script on close?

--- the details ---
right now i'm starting gnome terminal in a script with: 
```
gnome-terminal --window --working-directory=$JRN_DIR -e "bash -c jrnentry"
```where jrnentry is a script that basically calls a script that opens vim with a datestamped entry:
```
vim $FILENAME
```what i'm wondering is, is there a way in the ```
jrnentry
``` shell script can wait around for vim to exit before demounting the truecrypt volume? 

--- options i've considered but had no success with yet ---

[LIST]
[*]i've thought about using gnome terminal's 'profile preferences' > 'title and command' > 'when command exits' option. i don't really want the terminal to be held open - i DO want it to close, just not until truecrypt has dismounted the volume.
[*]i've tried using ```
vim -f
``` or ```
vim --nofork
```, which is supposed to "foreground - do not start a GUI in the background.This proves useful when gvim is run for another program that wants to wait until
the program finishes. It is also extremely useful for debugging." no luck here yet, not sure what i'm doing wrong.  specifically, i've tried a script that calls vim -f then echo' "i'm done" - the result is that "i'm done" does NOT print after vim exits, but immediately when the script is called.
[/LIST]

---

### Post by KeyserSoze93 on 2009-07-19
In vim:

```
:help autocmd
```

There are many events which can be used to trigger commands, you way want VimLeave.

You can also give a filename pattern.

---

### Post by tacitdynamite on 2009-07-20
Thanks a bunch - this is exactly what I was looking for. Once I figure out a vim function to filter out the filetype for my journal entry, I'll post it back over here for the benefit of others.

---

