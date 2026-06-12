---
title: "Help with a shell script."
date: 2006-03-21
forum: General Help
---

### Post by musther on 2006-03-21
I'm new to shell scripting, so if somebody could give me a hand, that would be great.

What I need to do is:

if directory $HOME/mydir is empty then
do a few lines
of commands
else
do a few different
lines of commands
fi

Thanks a bunch

---

### Post by Roobert on 2006-03-21
Why not this?

FOLDERSIZE=`ls -l foldername | cut -d" " -f2`

if [ "$FOLDERSIZE" -eq 0 ] ; then

    action
    action

else

    do some more stuff here

fi

---

### Post by musther on 2006-03-22
Thanks for the help, works well.

---

