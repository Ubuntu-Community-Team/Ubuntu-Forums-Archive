---
title: "Move/rename with a following link."
date: 2011-07-18
forum: General Help
---

### Post by Zebediah49 on 2011-07-18
I feel like this should have come up before, but is there a convenient way of moving something [directory is what I care about] while leaving a symbolic link in its place?  Currently the best way I can find is:

Terminal:
-script of 'mv "$1" "$2"; ln -s "$2" "$1"'
-requires typing out the target name, since it tab completion doesn't work on non-existent things.

GUI:
-move
-rename [copy content first]
-link back
-rename link [paste previous content]

The terminal way defeats the point of using the GUI to easily drag and drop things around, and the GUI is rather clumsy when I have to use copy and paste to even make it work.  Being able to manually edit a link target would simplify it, but I don't know of a way to do that.

Note that I'm pretty sure I don't want a terminal solution here, because it's stuff which I don't want to type (and sometimes can't.. seriously, I don't want to try to type a star).  Example:

#source:
foo/Some Long thing that has ~random~ characters[a#$%] (%^^) that are annoying!/
#target:
bar/Something Short/

---

### Post by idoitprone on 2011-07-18
pushd and popd?

```

$cd /
$ pushd ~/git
~/git /
$ HAT=`pwd`
$ popd
$ pwd
/
$ echo $HAT
/home/user/git

```i made an example. where the variable is still there after using pushd and popd

Ignore what i said, i was reading the problem wrong

i will help write a script that will take arguments just like mv

```

#!/bin/bash

LINKARGS=-s

if test $# -eq 2
   then
      echo "more or less than 2 arguments has been passed" 1>&2
      echo "Usage: mv <OLDFILE> <NEWFILE>" 1>&2
      exit 1
fi

mv "$1" "$2"
ln $LINKARGS "$2" "$1"

exit 0
```save it in a file and add excute permissions

---

### Post by Zebediah49 on 2011-07-18
> **idoitprone said:**
> pushd and popd?

```

$cd /
$ pushd ~/git
~/git /
$ HAT=`pwd`
$ popd
$ pwd
/
$ echo $HAT
/home/user/git

```i made an example. where the variable is still there after using pushd and popd

Ignore what i said, i was reading the problem wrong

i will help write a script that will take arguments just like mv

Correct, but I'm still glad I read that.. pushd and popd are a couple gems I previously was unaware of, and have reimplemented via things of the form
OLDDIR=$PWD; cd $WHEREVER; ... cd $OLDDIR;
structures.

The real question is if you have any ideas about how to avoid having to type out a destination name.

---

### Post by idoitprone on 2011-07-18
> **Zebediah49 said:**
> Correct, but I'm still glad I read that.. pushd and popd are a couple gems I previously was unaware of, and have reimplemented via things of the form
OLDDIR=$PWD; cd $WHEREVER; ... cd $OLDDIR;
structures.

The real question is if you have any ideas about how to avoid having to type out a destination name.
i sort of edited my post and wrote something. It is simple and it will fail under certain conditions. I can edit it, but it will take time

---

### Post by Snowboi on 2011-07-18
Im thinking right clicking on an item then selecting move to and then use a preset destination. If this is not the type of answer your looking for please elaborate your question more thoroughly :confused:.

---

### Post by idoitprone on 2011-07-18
> **Zebediah49 said:**
> Correct, but I'm still glad I read that.. pushd and popd are a couple gems I previously was unaware of, and have reimplemented via things of the form
OLDDIR=$PWD; cd $WHEREVER; ... cd $OLDDIR;
structures.

The real question is if you have any ideas about how to avoid having to type out a destination name.

well we cant really make up destination names can we? I just write a script so i only need to type it once and thats it. You are making you script compilicated. Try not to do that ok?

---

### Post by Zebediah49 on 2011-07-18
> **idoitprone said:**
> well we cant really make up destination names can we? I just write a script so i only need to type it once and thats it. You are making you script compilicated. Try not to do that ok?

Sorry, I guess I was being somewhat vague there.  The reason I was asking for a GUI solution is because most of the time I can get the new name from the old name and the delete key.  The goal here is to avoid using a terminal at all if I can help it.

I think I'm going to look in to using a pop-up text field prompt, combined with something similar to what was posted above and an addition to the drag-and-drop interface.
--Two things I have no idea how to do; will be fun.

---

