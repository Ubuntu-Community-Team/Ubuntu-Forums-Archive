---
title: "script supposed to check if there's a folder, create if it's not there"
date: 2010-07-09
forum: General Help
---

### Post by shortridge11 on 2010-07-09
I have a script that takes a location and does something to them then creates new files in the supplied location.  I was trying to get the script to create the location if it didn't exist, but i can't figure out why it won't work.  Here's what i've got right now

```
#!/bin/bash
destdir=$1
[[ -z "$destdir" ]] && { echo "No destination parameter supplied, exiting"; exit 1; }
[[ ! -e "$destdir" ]] && { echo "$destdir does not exist, exiting"; exit 1; }
destdir=${destdir%/}      # strip off any trailling / as we will add one ourselves
for file in *.ext
do
  file magic that works fine
done

```

```
#!/bin/bash
destdir=$1
[[ -z "$destdir" ]] && { echo "No destination parameter supplied, exiting"; exit 1; }
[[ ! -e "$destdir" ]] && { echo "creating $destdir"; mkdir -p $destdir; }
destdir=${destdir%/}      # strip off any trailling / as we will add one ourselves
for file in *.ext
do
  file magic that works fine
done

```

when i run the first one, it works if the supplied folder exists. If i try with my modification with a name such as /media/place/Foo\ bar, it creates a folder called Foo in the supplied dir, and bar in the dir i'm in when i run the script.  the -p flag on mkdir creates parent directories btw.  Any ideas on what i'm doing wrong?

---

### Post by blur xc on 2010-07-09
> **shortridge11 said:**
> I have a script that takes a location and does something to them then creates new files in the supplied location.  I was trying to get the script to create the location if it didn't exist, but i can't figure out why it won't work.  Here's what i've got right now

```
#!/bin/bash
destdir=$1
[[ -z "$destdir" ]] && { echo "No destination parameter supplied, exiting"; exit 1; }
[[ ! -e "$destdir" ]] && { echo "$destdir does not exist, exiting"; exit 1; }
destdir=${destdir%/}      # strip off any trailling / as we will add one ourselves
for file in *.ext
do
  file magic that works fine
done

``````
#!/bin/bash
destdir=$1
[[ -z "$destdir" ]] && { echo "No destination parameter supplied, exiting"; exit 1; }
[[ ! -e "$destdir" ]] && { echo "creating $destdir"; mkdir -p $destdir; }
destdir=${destdir%/}      # strip off any trailling / as we will add one ourselves
for file in *.ext
do
  file magic that works fine
done

```when i run the first one, it works if the supplied folder exists. If i try with my modification with a name such as /media/place/Foo\ bar, it creates a folder called Foo in the supplied dir, and bar in the dir i'm in when i run the script.  the -p flag on mkdir creates parent directories btw.  Any ideas on what i'm doing wrong?

I think what you want is 
```
if [[ ! -d ~/bin/testdir ]]; then
    echo directory does not exist
    mkdir -v testdir
fi
```IIRC the -d checks to see if the directory exists...

works on my system

```
./testdir.sh 
directory does not exist
mkdir: created directory `testdir'
```BM

---

### Post by shortridge11 on 2010-07-09
Well now i'm getting a syntax error: unexpected end of file.  Here's what i've got, with a little more shown
```
#!/bin/bash
destdir=$1
[[ -z "$destdir" ]] && { echo "No destination parameter supplied, exiting"; exit 1; }
if [ -d $destdir];
destdir=${destdir%/}      # strip off any trailling / as we will add one ourselves
for file in *.ext1
do
  newfilename="${file%.ext1}.ext2"
  fileProcess -o "$destdir/$newfilename" "$file"
done

```
It's telling me there's a syntax error in line 11, so maybe i'm forgetting a " somehwere? but i can't see one missing...

---

### Post by blur xc on 2010-07-09
> **shortridge11 said:**
> Well now i'm getting a syntax error: unexpected end of file.  Here's what i've got, with a little more shown
```
#!/bin/bash
destdir=$1
[[ -z "$destdir" ]] && { echo "No destination parameter supplied, exiting"; exit 1; }
if [ -d $destdir];
destdir=${destdir%/}      # strip off any trailling / as we will add one ourselves
for file in *.ext1
do
  newfilename="${file%.ext1}.ext2"
  fileProcess -o "$destdir/$newfilename" "$file"
done

```It's telling me there's a syntax error in line 11, so maybe i'm forgetting a " somehwere? but i can't see one missing...

Are you missing the "fi" to close up your if statement?  Also, recheck my post, I edited it a bit...

And for the record, I write out my conditional statements long hand.  I think it makes the code more readable than that all that fancy bash shorthand.

BM

---

### Post by shortridge11 on 2010-07-09
ok i finally got it ^_^ i needed to put $destdir in "" so it wouldn't get read incorrectly later in the file.  Your way of testing for/creating the new folder is much better than what i was trying to do. Thanks a lot!

---

