---
title: "list files by creation date"
date: 2010-08-19
forum: General Help
---

### Post by Eraemaajaervi on 2010-08-19
hi,

I'm looking for a terminal command that gives me the latest created folder in a directory tree.

```
ls -lR --sort=time --reverse
```

this i almost good, but a) it gives me files (rather than folders only), b) it sorts the files by folder (rather than just giving me a plain list of everything) and c) it takes way to long.

what i want:
```

2010-08-01 ./path/to/folder/a
2010-08-03 ./path/to/folder/b
2010-08-06 ./another/folder/c
2010-08-14 ./directory/d
2010-08-17 ./yet/another/folder/e
2010-08-19 ./f

```

any ideas?
.eraemaajaervi

---

### Post by Vaphell on 2010-08-19
in such situation writing a script is a way to go. Maybe this situation can be solved with a one-liner but it would be a hardcore one.

In scripts you can combine all the nifty tools available to manipulate data any way you want.

edit:

```

#!/bin/sh

IFS='
'

timestamp=0
latestdir=""
for dir in `find "$1" -type d`
do
  tmpts=$(stat "$dir" --format=%Y)
  if [ $timestamp -lt $tmpts ]; then
    latestdir="$dir"
    timestamp=$tmpts
  fi
done

echo `stat $latestdir`
unset IFS

```
script takes dir as a parameter and searches recursively for all dirs (find <dir> -type d), then on every single one it checks its timestamp and if its greater than previously saved one that means that from all tested already it's the newest and we need to test following dirs against it. When the set ends you get the result.

it should work, but it only returns one dir as finding max in a given set is of linear complexity. Sorting it in actual order would take ages in case of any but smallest sets of data, i'd hate to sort all dirs in /. Also there is no creation time but modification time (at least not in filesystems i suspect you use)

---

### Post by Eraemaajaervi on 2010-08-19
big thanks for the effort, looks good so far.
first the script always gave back whatever you typed for $2, but after i changed it i saw it gotta be a list (kept getting the .Trash folder)

but this i could live with
```

touch -t 201008170000 tmp && find -type d -cnewer tmp | xargs stat --format="%Y -- %n" | sort -n

```

and it's even a one liner =)
problem is, xargs doesnt go well with spaces and special characters in folder names.

---

### Post by zakb on 2010-08-19
Try this: 

ls * -d -l -t

That will give you the last access time for directories.  If you are looking for creation time, you can't get there from here.   From what I can find on the web, creation times are not stored anywhere...

By the way, could you tell me how you get the nice box labeled 'Code' in your post?

---

### Post by Vaphell on 2010-08-19
[ code ] [ /code ] without spaces, just like [ b ] to bold, [ u ] to underline or [ i ] for italic or [ quote ]

yup, find with its exec/print/omg-what-not sections is very powerful and spaces in names indeed suck :)

---

### Post by Eraemaajaervi on 2010-08-19
> ls * -d -l -t

how can i make this recursive?

ps: always thought "ctime" would be creation time

pss: does the access time change when a application accesses it?

---

### Post by Vaphell on 2010-08-19
[http://www.qa.com/about-qa/blogs/2010/july/creation-time-in-unix-yes---in-ext4](http://www.qa.com/about-qa/blogs/2010/july/creation-time-in-unix-yes---in-ext4)
apparently ext4 has creation time but i think it's not to easy to get your hands on

i'd guess yes - i don't think that the file system cares who/what opens the file. Besides you always open files via some app.

---

### Post by zakb on 2010-08-19
"-R" should make the list command recursive, but I haven't been able to get it to do what I think it should do...

I think the 'find' command would be more flexible, but I don't know enough to give a real example.

I don't know if a program accessing a file changes the access time, but it shouldn't be too hard to do an experiment and find out...

---

### Post by zakb on 2010-08-19
PS: Check out 'Tree'.  You can get it through the Synaptic Package Manager...

'DESCRIPTION
       Tree is a recursive directory listing program  that  produces  a  depth
       indented  listing  of  files,  which  is colorized ala dircolors if the
       LS_COLORS environment variable is set and output is to  tty.   With  no
       arguments,  tree lists the files in the current directory.  When direc&#8208;
       tory arguments are given, tree lists all the files  and/or  directories
       found  in the given directories each in turn.  Upon completion of list&#8208;
       ing all files/directories found, tree returns the total number of files
       and/or directories listed.'
Quoted from the man page....

---

### Post by Eraemaajaervi on 2010-08-20
hmm, tree also sorts each directory by itself so isn't much of any help here.

also ```
ls * -d -l -t -R
```somehow isn't really recursive.

I'm gonna go with
```

touch -t 201008170000 tmp && find -type d -cnewer tmp | xargs -I {} stat {} --format="%Y -- %n" | sort -n
```

which is pretty close to what i need. it gives me all directorie modified after a specific date (here 201008170000, which is 2010/08/17 at 00:00) and sorts them by the modification time (last entry is newest).
this also gives me back .Trash and root folders but since it's a list i can look for an entry that makes sense. if there is none i just lower the modified date

thanks for helping

---

### Post by Vaphell on 2010-08-20
you can try filtering out selected names with **! -name** or some regexp in find though it may increase time

---

