---
title: "Remove Characters from File and Folders Recursively"
date: 2011-02-03
forum: General Help
---

### Post by JEmlay on 2011-02-03
After two days I give up.  I hope someone here can help me.
 
Here's the project I'm working on.  We are moving our storage server  from an AFP capable box to a SMB only box.  So obviously moving files  that contain SMB nonoes will just scramble the files.
 
I need to replace:   \  /  *  ?  <  >  |
 
From all FILES and all FOLDERS on the AFP share.  The entire AFP share boils down to one folder on root so that makes it easier.
 
I've tried 20 different million versions of playing with various:
 
 
for i in `find . -type f`
do
echo $i
mv $i `echo $i |tr ? _`
done
 
The problem with this is:
1. It wont do files with spaces.
2. If a file shares the same name of the folder it's in, it fails on  that file.  The fix I found was to do the folders first then go through  and do the files.
3. The above will only do "?", if I extend it out to do all of the  characters or just replace the "?" with other characters it scrambles  the file.  For example, when it renames a image (.jpg), it's renamed  correctly but that file is now garbage.  It's no longer an image file.   It's the same size at it was, but no longer readable.
 
This must be a pretty common issue.  Moving from AFP to SMB.  Can  someone please help me out with something reliable that will rename my  files and not DESTROY them all?
 
Or, worse case scenario, just strip everything but alphanumeric.  At this point I would happy with even that.
 
Thanks to whomever can help me out!

---

### Post by sisco311 on 2011-02-03
Hi, 

Assuming that you are using bash, try something like:
```
while IFS= read -r -d '' file; do 
  **echo** mv -b -- "$file" "${file//[\\\*\?\<\>\|]/_}"
done < <(find **/path/to/dir** -depth -print0)
```

---

### Post by JEmlay on 2011-02-04
Thank you so much for your reply!  I truly appreciate it.

I'm on the linux box as su.

I'm not familiar with the way you formatted the third line.  When I run it I get:

sh: syntax error near unexpected token `<'

Thanks again, for your time!

---

### Post by asmoore82 on 2011-02-04
There's a ton of **broken** shell script fragments out there
dealing with processing lists of files.

None of the "workarounds" are good enough, even manipulating IFS.

The best way is to do it right from the start -
Only generate lists of files with the shell's natural wildcard `*` ability!

The problem gets even more complex if you are going to be renaming files and
particularly folders. You need a method that ensures the list of files to be
renamed doesn't become stale because the containing folders have already been renamed!

My solution is a recursive function that does a depth-first traversal
(I noticed your error message says "sh: ...",
You need to use the full bash shell for this):
```
function deepfind () 
{
    if [ -d "$1" ]
    then
        echo "entering $1 ..."
        cd "$1"
        for dir in */
        do
            deepfind "$dir"
        done
        for file in *
        do
            echo "rename $file"
        done
        echo "leaving $1 ..."
        cd -
    fi
}
```

To make recursion easiest, the function has to receive a directory name
as it's first argument, or it does nothing.

Note the use of a `for file in *` construct to get a viable list of filenames.
The shell's `*` wildcard is rock solid, capable of properly handling
all special characters in filenames - even *newlines*!
The only thing the wildcard misses is intentional - hidden "dot" files.
To catch these, you need to specify the leading dot like `.*`
The problem with this is that it will catch both the single dot (this folder)
and the double dot (parent folder). To avoid this, use some single
character wildcards `?` to add some substance: `.??*`
Now the only problem is that we won't catch any dot files with
only a single letter name. I can live with this "bug", but
we could even catch this too with an anti-wildcard: `.[!.]`

Also note the use of a `*/` wildcard to catch only directories -
this is quite a handy trick for everyday use, like: `ls -d */`

And finally, the actual renaming. The `rename` command does file renaming based
on a given perl expression. Maybe someday this command will also recurse on its own :D!
This command can replace our entire 2nd for loop.

So, the end product looks like:
```
function deepfind () 
{ 
    if [ -d "$1" ]
    then
        echo "entering $1 ..."
        cd "$1"
        for dir in */ .??*/
        do
            deepfind "$dir"
        done;
        rename -v 'y/\\?<>!@#$%^&*{}[]|/_/' * .??*
        echo "leaving $1 ..."
        cd -
    fi
}
```

Aim and Fire!: ```
deepfind */some/expendable/folder*
```

---

### Post by JEmlay on 2011-02-04
Thanks to you as well for your write up!  No wonder I've been bashing my head against a wall on this.

What do you mean by use the "full" bash shell?

If it traverses first, is this going to finish on a folder structure with over a million files?

---

### Post by sisco311 on 2011-02-04
> **JEmlay said:**
> Thank you so much for your reply!  I truly appreciate it.

I'm on the linux box as su.

I'm not familiar with the way you formatted the third line.  When I run it I get:

sh: syntax error near unexpected token `<'

Thanks again, for your time!

That's a [bashism]("http://mywiki.wooledge.org/Bashism").

Here is a script which should work in a Bourne shell or dash:
```
#!/bin/sh

FILE="$1"
NEWF=`echo "$FILE" | tr '\|?*<>' '_'`
if [ "$FILE" != "$NEWF" ]; then
  mv -b -- "$FILE" "$NEWF"
fi

```

You have to use it with find:
```
find /path/to/dir -depth -execdir /path/to/script '{}' \;
```

---

### Post by JEmlay on 2011-02-04
> **sisco311 said:**
> That's a [bashism]("http://mywiki.wooledge.org/Bashism").

Here is a script which should work in a Bourne shell or dash:
```
#!/bin/sh

FILE="$1"
NEWF=`echo "$FILE" | tr '\|?*<>' '_'`
if [ "$FILE" != "$NEWF" ]; then
  mv -b -- "$FILE" "$NEWF"
fi

```You have to use it with find:
```
find /path/to/dir -depth -execdir /path/to/script '{}' \;
```

When I run it:

find /shares/Graphics/test -depth -execdir /shares/Graphics/test2/rename '{}' \;

I get a whole bunch of (I'm guessing one per object found):

find: /shares/Graphics/test2/rename: Permission denied

Full access on the file.  Another test script runs fine.

---

### Post by JEmlay on 2011-02-04
Nevermind, I botched my conversion from windows->unix.

Ran the script, it removed a ton of stuff.  Files with spaces, no problem.

The only thing I see that's left are....   /   \   "

It didn't remove those.

Thank you so much!!!!

---

### Post by JEmlay on 2011-02-06
I should note, all the "/" show up as ":2f".

How can I specify to replace ":2f" with "_"?

I tried adding them to your script and no matter what I do, it replace every : and every 2 and every f.  Not just the groupings of :2f.

As an interesting note, every time I run the script on my share it takes almost 5 and a half hours to complete.  Yicks!  :p

./15055pps1:2f12:2f11/Blue:2fwhite
./09224tm8:2f6:2f10.jpg

Obviously that's 

Folder - 15055pps1/12/11
Folder - Blue/white
File - 09224tm8/6/10.jpg

It looks like if I can tackle this one last character I can fix over 99% of my files.  I can trash the rest if I have to.

---

### Post by firebird_1979 on 2011-02-06
Instead of using Bash or something else----> pyRenamer does EXACTLY what you want!

I used it to strip "?" from over 20000 files in the past, and convert "[" to "(" etc.
It can use regular expressions, wildcards, patterns, etc. etc.

A wonderful piece of software!

It's in the Ubuntu repositories as well...

---

### Post by JEmlay on 2011-02-06
> **firebird_1979 said:**
> Instead of using Bash or something else----> pyRenamer does EXACTLY what you want!

I used it to strip "?" from over 20000 files in the past, and convert "[" to "(" etc.
It can use regular expressions, wildcards, patterns, etc. etc.

A wonderful piece of software!

It's in the Ubuntu repositories as well...

Thanks for the pointer.  But I don't have any environment (KDE, XFCE...). This is a turnkey linux application server.  I'm lucky to even have the freedom/access that I have.  As for windows, all I see from SMB is the 8.2 filename which just looks like garbage.

---

### Post by asmoore82 on 2011-02-06
pyrenamer is nice...

To catch the :2f's with the script, you'd need a 2nd `rename` line:
```
rename 's/:2f/_/g' *
```

---

### Post by madmarx on 2011-02-06
A sample script that worked out well for me for batch name changes:
find . -name "*" -exec rename 'y/ /_/' {} \;

You will need to replace the 'y/_/ /' with the right regexp.
I suppose the 'y/\\?<>!@#$%^&*{}[]|/_/' cited above will do.

Rename is actually a perl script, so you will need this installed first.

---

### Post by asmoore82 on 2011-02-06
> **madmarx said:**
> A sample script that worked out well for me for batch name changes:
find . -name "*" -exec rename 'y/ /_/' {} \;
As explained earlier, for all but the simplest cases this breaks ... quickly.

You can't rename subdirectories as find is still finding within them.
Even the `-depth` first option to find can't help, because rename can't
rename a full path all at once.

Here's the tests, easy breakage:
```
**$** x='? # %'
**$** spacer=""
**$** for char in $x #intentional unquoted $x
> do
>     mkdir "test$spacer$char.dir"
>     touch "test$spacer$char.file"
>     spacer="$spacer "
> done
**$** for dir in */
> do
>     cd "$dir"
>     spacer=""
>     for char in $x #intentional unquoted $x
>     do
>         touch "test$spacer$char.file"
>         spacer="$spacer "
>     done
>     cd ..
> done
**$** ls -R
.:
test  %.dir  test #.dir  test?.dir  test  %.file  test #.file  test?.file

./test  %.dir:
test  %.file  test #.file  test?.file

./test #.dir:
test  %.file  test #.file  test?.file

./test?.dir:
test  %.file  test #.file  test?.file

**$** find . -name "*" -exec rename 'y/\\?><!@#$%^&*}{][:|/_/' {} \;
[B][COLOR="Red"]find: `./test?.dir': No such file or directory
find: `./test #.dir': No such file or directory
find: `./test  %.dir': No such file or directory[/COLOR][/B]
**$** ls -R
.:
test  _.dir  test _.dir  test_.dir  test  _.file  test _.file  test_.file

./test  _.dir:
test  %.file  test #.file  test?.file

./test _.dir:
test  %.file  test #.file  test?.file

./test_.dir:
test  %.file  test #.file  test?.file

```
Same setup as above, but with `-depth`:
```
**$** find . **-depth** -name "*" -exec rename 'y/\\?><!@#$%^&*}{][:|/_/' {} \;
[B][COLOR="Red"]Can't rename ./test?.dir/test?.file ./test_.dir/test_.file: No such file or directory
Can't rename ./test?.dir/test  %.file ./test_.dir/test  _.file: No such file or directory
Can't rename ./test?.dir/test #.file ./test_.dir/test _.file: No such file or directory
Can't rename ./test #.dir/test?.file ./test _.dir/test_.file: No such file or directory
Can't rename ./test #.dir/test  %.file ./test _.dir/test  _.file: No such file or directory
Can't rename ./test #.dir/test #.file ./test _.dir/test _.file: No such file or directory
Can't rename ./test  %.dir/test?.file ./test  _.dir/test_.file: No such file or directory
Can't rename ./test  %.dir/test  %.file ./test  _.dir/test  _.file: No such file or directory
Can't rename ./test  %.dir/test #.file ./test  _.dir/test _.file: No such file or directory[/COLOR][/B]
**$** ls -R
.:
test  _.dir  test _.dir  test_.dir  test  _.file  test _.file  test_.file

./test  _.dir:
test  %.file  test #.file  test?.file

./test _.dir:
test  %.file  test #.file  test?.file

./test_.dir:
test  %.file  test #.file  test?.file
```

---

### Post by asmoore82 on 2011-02-06
I found out the previous deepfind was **broken**!
...After it got 2 levels deep it didn't come back up properly.

I've fixed it, but [B]now it assumes that it is run
from where you want to start cleaning![/B]

So, the final, *tested*, *working* product is this:
```
function deepfind () 
{ 
    for dir in */ .??*/
    do
        if [ -d "$dir" ]
        then
            echo "entering $dir ..."
            cd "$dir"
            deepfind
            echo "leaving $dir ..."
            cd ..
        fi
    done
    rename -v 's/:2f/_/g' * .??*
    rename -v 'y/\\"?<>!@#$%^&*{}[]:|/_/' * .??*
}
```

Here it is in *deep* action:
```
**$** ls -R
.:
test    :2f.dir  test    :2f.file  test   |.dir  test   |.file

./test    :2f.dir:
test :2f.dir  test :2f.file  test|.dir  test|.file

./test    :2f.dir/test :2f.dir:
test :2f.file  test|.file

./test    :2f.dir/test|.dir:
test :2f.file  test|.file

./test   |.dir:
test :2f.dir  test :2f.file  test|.dir  test|.file

./test   |.dir/test :2f.dir:
test :2f.file  test|.file

./test   |.dir/test|.dir:
test :2f.file  test|.file
**$** deepfind
#lots of output ...
**$** ls -R
.:
test    _.dir  test   _.dir  test    _.file  test   _.file

./test    _.dir:
test _.dir  test_.dir  test _.file  test_.file

./test    _.dir/test _.dir:
test _.file  test_.file

./test    _.dir/test_.dir:
test _.file  test_.file

./test   _.dir:
test _.dir  test_.dir  test _.file  test_.file

./test   _.dir/test _.dir:
test _.file  test_.file

./test   _.dir/test_.dir:
test _.file  test_.file
```

---

### Post by JEmlay on 2011-02-07
> **asmoore82 said:**
> I found out the previous deepfind was **broken**!
...After it got 2 levels deep it didn't come back up properly.

I've fixed it, but [B]now it assumes that it is run
from where you want to start cleaning![/B]

So, the final, *tested*, *working* product is this:


When I tried to run your previous example it failed on me.  When I try to run your last example it's also giving me the same errors:

entering ---\:2f____-----12345ABCDE (HELLO!!!!!)/ ...
./deepfind: line 8: cd: --: invalid option
cd: usage: cd [-L|-P] [dir]

Maybe I'm running wrong?  I dumped it in a file and executed deepfind after the function then just ran the script.

Thanks again for the help!

---

### Post by sisco311 on 2011-02-07
I can't test it on files with slashes in their name but, in theory this should work:
```
#!/bin/sh

FILE="$1"
NEWF="./`echo "$FILE" | sed -e 's/^\.\///' -e 's/[\/*?|<>]/_/g'`"

if [ "$FILE" != "$NEWF" ]; then
  mv -b -- "$FILE" "$NEWF"
fi

```

```
find /path/to/dir -mindepth 1 -depth -execdir /path/to/script '{}' \;
```

---

### Post by JEmlay on 2011-02-07
> **sisco311 said:**
> I can't test it on files with slashes in their name but, in theory this should work:


Since your first script took care of everything but /  \  ", now my test files only have those characters.  I ran your updated script and it didn't do anything to those files.

The files with a backslash where so few that was able to manually rename them in a couple hours.  So those are done.

I changed your tr command to awk '{sub(":2f","_")}1' and that took care of the forward slashes except it only replaced ONE slash per file and folder.  If the file had 2 or more slashes in it then it still has some slashes.  So I'll have to run it multiple times until they are all gone.  I'm on my second run now.  At 5.5 hours per run this will take some time!

So, that ultimately leaves only "

Come to find out I have more then a few.  I had looked at only folders.  There are hundreds and hundreds of files with quotes so I'll have to address those as well.

I'll play around with the awk command and see where I get.

I can't thank you all enough for your time in helping me.  I'm almost there!!!

Edit:
Well, I'm not sure if I formatting it properly but this is replacing the quotes:

sed 's/\(.*\)"\(.*\)/\1\2/'`

With the quotes I don't have to replace it with anything (no need for "_") so replacing it with nothing kind of works out better.  However this is also only replacing one instance of it in each file and folder.  But it's getting the job done and I'm super happy about that.

---

### Post by sisco311 on 2011-02-07
In awk use gsub instead of sub:
```
awk '{gsub(":2f","_"); print}'
```

To remove the double quotes you can use:
```
tr -d '"'
```
or
```
sed -e 's/"//g'
```

---

### Post by JEmlay on 2011-02-08
A million thanks [sisco311]("http://ubuntuforums.org/member.php?u=244665")!  You are my linux hero!!!

---

