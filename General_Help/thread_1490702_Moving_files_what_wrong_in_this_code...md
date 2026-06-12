---
title: "Moving files what wrong in this code..?"
date: 2010-05-22
forum: General Help
---

### Post by CatchItBaby on 2010-05-22
```
mkdir $PWD"/remaining"
       echo "Enter the textfile name which contain missng rar filename names"
       read missing

       index=0

       while read line ; do
	    MYARRAY[$index]="$line"
	    index=$(($index+1))
       done < $missing

       toLower() {
         echo $1 | tr "[:upper:]" "[:lower:]" 
       } 

      for dir in *.rar; do
         for name in ${MYARRAY[@]}; do
            if [[ `toLower $name` = `toLower $dir` ]]; then
              mv -v $PWD"/"$dir $PWD"/remaining/" 
            fi
         done
      done
```

I hv one text file which containing some rar filename like
myhomework.rar
mymovie.rar
subject.rar

and a folder contain several rar file if that folder contain above rar files then it will move those files into remaining folder 

But the problem is that it work very slow taking a lot of time in moving files 

Anyone have simple code which can do same task but fastly..

Thanks

---

### Post by Joe of loath on 2010-05-22
What kind of speeds are you getting? Unless there is a huge problem with the code (I can't tell you, I'm no expert) the speeds will simply be limited by your processor or hard drive.

---

### Post by CatchItBaby on 2010-05-22
it taking 1 hr in searching in 1000 files

---

### Post by jamesisin on 2010-05-22
I can't say about speed, but I see some things that I would not do in a script.

1. Is MYARRAY a built-in variable or one made by the system?  Variables in all caps are generally reserved for those created by the system and should not be created by users (even in scripts).  This isn't 'illegal' it's just a good practice.

2. I would prefer a construct like this [noparse]"$PWD/remaining"[/noparse] over one like this [noparse]$PWD"/remaining"[/noparse].

3. Same with this [noparse]"$PWD/$dir"[/noparse] over this [noparse]$PWD"/"$dir[/noparse].

Not sure this will change things as regards speed though.

---

### Post by jamesisin on 2010-05-22
For that matter, why are you using $PWD to define the directory when you could just use the directory name:

```
mkdir remaining
```

---

### Post by CatchItBaby on 2010-05-23
I did what u suggested but nothing happen...

---

### Post by jamesisin on 2010-05-23
Do you mean nothing as in the script did nothing at all or nothing as in nothing different?

---

### Post by CatchItBaby on 2010-05-23
> **jamesisin said:**
> Do you mean nothing as in the script did nothing at all or nothing as in nothing different?

means i changed in the script what u suggested but it performance is same as it was in past..

---

### Post by solwic on 2010-05-23
> **CatchItBaby said:**
> means i changed in the script what u suggested but it performance is same as it was in past..

Let's answer the important question:  what are your system specs?

---

### Post by CatchItBaby on 2010-05-23
> **solwic said:**
> Let's answer the important question:  what are your system specs?

1GB Ram

300 GB Space

Dual Core processor

---

### Post by jamesisin on 2010-05-23
One thing that might help is to add an echo statement to each loop.  This way you could see which loop was bogging down.

Also, could you post the new version of the code?

Oh, and are you moving the files to a different position on the same partition or are they being moved to a different partition all together?

---

### Post by CatchItBaby on 2010-05-23
they are moving to same partioned

---

### Post by jamesisin on 2010-05-23
That's good.  In theory the move operation should be relatively instantaneous.

---

### Post by geirha on 2010-05-24
Perhaps something like this will be faster
```

#!/bin/bash

read -ep "File with list: " missing

mkdir -p remaining || exit

shopt -s nocaseglob
while read -r; do 
  mv -v "./${REPLY%.*}".ra[r] remaining/
done < "$missing"

```

The "./${REPLY%.*}".ra[r] is a little hack to make the filename be treated as a glob. It assumes that all files listed in the file are rar files with .rar extensions. The [r] instead of r at the end turns it into a glob, and lastly the nocaseglob shell option makes the globs case-insensitive, which is apparently what you want, oddly enough.
```

$ shopt -s nocaseglob; touch Foo
$ ls foo
ls: cannot access foo: No such file or directory
$ ls fo[o]
Foo

```

Your initial script were missing quotes in every single place where quotes are important. I recommend you read up on that so you don't do those mistakes again. 

[http://wiki.bash-hackers.org/syntax/words](http://wiki.bash-hackers.org/syntax/words)
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by CatchItBaby on 2010-05-24
Thanks Thanks Thanks

:)

---

