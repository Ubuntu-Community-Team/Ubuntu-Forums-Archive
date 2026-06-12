---
title: "Bash Shell Scripting + sed + gawk"
date: 2010-07-11
forum: General Help
---

### Post by vttay03 on 2010-07-11
I'm trying to write a script that renames all of my mp3 files in a particular directory to my default naming convention.  When I rip them using abcde (command line CD ripping utility), the names aren't what I'd like them to be.  Now I know I could probably change the .conf file for abcde to get rid of the problem, but I took it as an opportunity to practice shell scripting.  Anyways, what I've got so far is below:

```


# find all .mp3 files in working directory
for FN in *.mp3
do
  # following command pipes the filename into sed which then replaces
  # the period and underscore(s) with a single whitespace;
  # g option means operate globally (i.e. replace all occurrences, not 
  # just the first one)
  NEW_FN=`echo "${FN}" | sed -e 's/[.]/ /' -e 's/[_]/ /g'`
  mv "${FN}" "${NEW_FN}" # rename file using mv
done


```

This will transform:

```


1.My_Iron_Lung.mp3


```

into:

```


1 My Iron Lung.mp3


```

Let's say I ultimately want the filename to be "01 My Iron Lung.mp3" instead of "1 My Iron Lung.mp3".  Can this be done using sed?  Or do I need to use something like gawk instead?  I didn't know if sed could make any type of logic decisions.  This also gets trickier because if one of the files is named "10 Song.mp3", you wouldn't want to make the leading 0 substitution.  I've reduced it to the fact that if there is only 1 character in the filename until the first whitespace, then substitute a leading 0.  Otherwise, don't.  If someone could help me incorporate this into a script, it'd be greatly appreciated.  Whew...I know that was a lot and understand if you didn't actually feel like reading it...

---

### Post by DaithiF on 2010-07-11
Hi,
this should do it:
```
echo $fn | sed -r 's/^([0-9])\./0\1 /;s/^([0-9][0-9]+)\./\1 /;s/_/ /g'
```

you might also want to look into **rename**, which would allow you to use a search/replace like this in a single line.

---

### Post by vttay03 on 2010-07-11
Thanks for your help!  Do you mind explaining the sed arguments you used?  I just started exploring sed this weekend so I'm a bit new to the whole thing...

I'm going to looking into rename as well.

---

### Post by geirha on 2010-07-11
Here's one using bash to change the name. The for-loop should only iterate "wrongly" named files, so it can be used in dirs where parts of the files have already been renamed.

```

#!/bin/bash
shopt -s extglob   # Turns on extended globs.
shopt -s nullglob  # Makes globs expand to nothing if no files matched.

for file in +([0-9]).*.mp3; do
    # split filename into track, title and extension.
    track=${file%%.*} ext=${file##*.}
    title=${file#$track.} title=${title%.$ext}
    
    newfile=$(printf "%02d %s.%s" "$track" "${title//_/ }" "$ext")
    mv -iv "$file" "$newfile"
done

```

See [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob) for an explanation of the extended glob *+([0-9])*
See [http://mywiki.wooledge.org/NullGlob](http://mywiki.wooledge.org/NullGlob) for an explanation of the *shopt -s nullglob*
See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073) for an explanation of the parameter expansions *${file##*.}*, *${title//_/ }* etc...

```

$ ./script
«1.My_Iron_Lung.mp3» -> «01 My Iron Lung.mp3»
$ touch 13.Some_other_song....mp3
$ ./script
«13.Some_other_song....mp3» -> «13 Some other song....mp3»

```

---

### Post by DaithiF on 2010-07-12
> **vttay03 said:**
> Thanks for your help!  Do you mind explaining the sed arguments you used? 

sure:
-r = regex mode, avoids the need to escape parentheses, {} brackets, + , etc

s/^([0-9])\./0\1 /;     => ^anchors at beginning of line, searches for a single digit followed by a period, captures the digit (enclosed in parentheses), then replaces with a leading 0, the digit (as represented by \1, meaning the 1st captured term), and a space

s/^([0-9][0-9]+)\./\1 /;  => ^again anchors at beginning of line, this time searches for a single digit, followed by one or more digits (the '+' modifier meaning match one or more), (ie. in effect searching for 2 or more digits together, this could also have been done by: [0-9]{2,), followed by a period, and replaces by the captured term and a space.  

s/_/ /g   => replace all underscores with spaces

---

### Post by vttay03 on 2010-07-12
This has all been very informative, thanks for everyone's help and taking the time to explain things.  I've been getting into bash shell scripting for automating a bunch of tasks and it's turning out to be a lot of fun.

---

