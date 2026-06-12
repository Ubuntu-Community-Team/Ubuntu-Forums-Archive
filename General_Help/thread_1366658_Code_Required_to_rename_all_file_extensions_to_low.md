---
title: "Code Required to rename all file extensions to lower case!"
date: 2009-12-28
forum: General Help
---

### Post by Rytron on 2009-12-28
Hi.
This may be a long shot, but is there a line(s) of code that would rename all file extensions to lower case? It would need to work recursively down through directories.

I know there are many great bulk renaming tools but it would be nice to do it in one go via the terminal.

Thank you.

---

### Post by The Cog on 2009-12-28
Rename can change the entire filename to lower case if that's any help. I'm not sure if it can change only the extension easily.

If it is just one extension such as .JPG, then this will do it:
> rename 's/\.JPG$/\.jpg/' *.JPG

Use **man rename** for details.

---

### Post by Rytron on 2009-12-28
> **The Cog said:**
> Rename can change the entire filename to lower case if that's any help. I'm not sure if it can change only the extension easily.

If it is just one extension such as .JPG, then this will do it:


Use **man rename** for details.

Thank you The Cog.

---

### Post by BenAshton24 on 2009-12-28
rename does not work recursively... If you want a recursive rename for file extensions then you can use the following:

```
find -name '*.BOB' | sed 's/\(.*\)\.BOB/mv "\1.BOB" "\1.bob"/' |sh
```

The above recursively renames files with the extension "BOB" to files with the extension "bob". So if you want to rename HTM to htm or whatever all you have to do is change all occurrences of BOB to HTM & bob to htm in the command.

```
find -name '*.HTM' | sed 's/\(.*\)\.HTM/mv "\1.HTM" "\1.htm"/' |sh
```

---

### Post by Rytron on 2009-12-28
> **BenAshton24 said:**
> rename does not work recursively... If you want a recursive rename for file extensions then you can use the following:

```
find -name '*.BOB' | sed 's/\(.*\)\.BOB/mv "\1.BOB" "\1.bob"/' |sh
```

The above recursively renames files with the extension "BOB" to files with the extension "bob". So if you want to rename HTM to htm or whatever all you have to do is change all occurrences of BOB to HTM & bob to htm in the command.

```
find -name '*.HTM' | sed 's/\(.*\)\.HTM/mv "\1.HTM" "\1.htm"/' |sh
```

Great. Cheers BenAshton24.

---

### Post by andrew.46 on 2009-12-29
Hi The Cog,

> **The Cog said:**
> Rename can change the entire filename to lower case if that's any help. I'm not sure if it can change only the extension easily.

I have been bashing away (pun intended) at a for loop that in a similar way changes the entire file from upper to lower case:

```

for f in `ls`
   do
ftr=`echo $f  | tr '[A-Z]' '[a-z]' `
   if [ $ftr != $f ]; then
   mv -i $f $ftr
   fi
done

```

There are a bunch of variations of this scattered around the internet...

Andrew

**Edit:** Hmmmm.... not recursive though....

---

### Post by BenAshton24 on 2009-12-29
> **andrew.46 said:**
> Hi The Cog,



I have been bashing away (pun intended) at a for loop that in a similar way changes the entire file from upper to lower case:

```

for f in `ls`
   do
ftr=`echo $f  | tr '[A-Z]' '[a-z]' `
   if [ $ftr != $f ]; then
   mv -i $f $ftr
   fi
done

```

There are a bunch of variations of this scattered around the internet...

Andrew

**Edit:** Hmmmm.... not recursive though....

Hey, you can do it like this if you need it to be recursive:
```
find . -type f | sed 's/\(.*\/\)\(.*\)/mv "\1\2" "\1\L\2"/' |sh
```

---

