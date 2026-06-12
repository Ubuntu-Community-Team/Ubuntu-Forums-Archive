---
title: "Bash and white spaces"
date: 2010-11-12
forum: General Help
---

### Post by thegodfaza on 2010-11-12
I've been googling for a while and can't get this script to work. I'm trying to search a directory for specific file types then print a list of all matching files, one per line. But the script is interpreting white space as a new line.

```
#!/bin/bash

REGEX_EXT=".*[.]+(mpg|avi)"
CDIR="/some/dir/"

for FILE in `find "$CDIR" | grep -P $REGEX_EXT`
do
        echo "$FILE"
done

```

It should look like:
```
/some/dir/file1.mpg
/some/dir/file 2.avi
/some/dir/dir/file1.mpg
/some/dir/dir/file 2.avi
/some/dir/dir 2/file1.mpg
/some/dir/dir 2/file 2.avi
```

But instead I'm getting:
```
/some/dir/file1.mpg
/some/dir/file
2.avi
/some/dir/dir/file1.mpg
/some/dir/dir/file
2.avi
/some/dir/dir
2/file1.mpg
/some/dir/dir
2/file
2.avi
```

---

### Post by dcstar on 2010-11-12
> **thegodfaza said:**
> I've been googling for a while and can't get this script to work. I'm trying to search a directory for specific file types then print a list of all matching files, one per line. But the script is interpreting white space as a new line.

```
#!/bin/bash

REGEX_EXT=".*[.]+(mpg|avi)"
CDIR="/some/dir/"

for FILE in `find "$CDIR" | **grep -P** $REGEX_EXT`

```
.......
man grep:
```
       -P, --perl-regexp
              Interpret  PATTERN as a Perl regular expression.  **This is highly experimental** and grep -P may warn of unimplemented features.
```
Anything "highly experimental" has no guarantee of working how you may anticipate it should.

---

### Post by thegodfaza on 2010-11-12
> **dcstar said:**
> man grep:
```
       -P, --perl-regexp
              Interpret  PATTERN as a Perl regular expression.  **This is highly experimental** and grep -P may warn of unimplemented features.
```
Anything "highly experimental" has no guarantee of working how you may anticipate it should.

Even if I remove grep from the search and display ALL files using 'find "$CDIR"', I still get the spaces in file paths being interpreted as new lines.

---

### Post by Girya on 2010-11-12
don't know if this is what you want but this works for me. Searching for ogg and mp3 

```
find . -name "*.mp3" -o -name "*.ogg"
```

quote the regex to escape shell expansion, use -o (or) to find mp3 or ogg

returns: 

> ... ./Jesus_Jones/Doubt/07_-_Real,_Real,_Real.ogg
./Jesus_Jones/Doubt/06_-_Nothing_to_Hold_Me.ogg
./Jesus_Jones/Doubt/12_-_Blissed.ogg
./Jesus_Jones/Doubt/03_-_International_Bright_Young_Thing.ogg
./Jay-Z_and_Linkin_Park.mp3
./Jay-Z_and_Linkin_Park.mp3/Collision_Course/04_-_Numb-Encore.mp3
./Jay-Z_and_Linkin_Park.mp3/Collision_Course/02_-_Big_Pimpin'-Papercut.mp3
./Jay-Z_and_Linkin_Park.mp3/Collision_Course/01_-_Dirt_Off_Your_Shoulder-Lying_From_You.mp3...


no white spaces in my files though as I removed them a while ago

---

### Post by Girya on 2010-11-12
i added white spaces to a file and the command i used worked for that file too.

---

### Post by thegodfaza on 2010-11-12
> **Girya said:**
> don't know if this is what you want but this works for me. Searching for ogg and mp3 

```
find . -name "*.mp3" -o -name "*.ogg"
```

quote the regex to escape shell expansion, use -o (or) to find mp3 or ogg

returns: 



no white spaces in my files though as I removed them a while ago

For some reason that doesn't work either. This script is just a segment from a larger script. I debugged the problem down to this section so while using that command by it's self works, for some reason when I try to execute it in a script, it acts odd.

Script:
```
#!/bin/bash

CDIR="/some/dir/"

for FILE in `find "$CDIR" -name "*.avi" -o -name "*.mpg"`
do
        echo "$FILE"
done
```

Output:
```
$ sudo ./renamer
/some/dir/dir/file
2.avi
/some/dir/dir/file1.mpg
/some/dir/file
2.avi
/some/dir/file1.mpg
/some/dir/dir
2/file
2.avi
/some/dir/dir
2/file1.mpg

```

```
$ sudo find "/some/dir/" -name "*.avi" -o -name "*.mpg"
/some/dir/dir/file 2.avi
/some/dir/dir/file1.mpg
/some/dir/file 2.avi
/some/dir/file1.mpg
/some/dir/dir 2/file 2.avi
/some/dir/dir 2/file1.mpg
```

---

### Post by thegodfaza on 2010-11-14
So anyone have any idea why a bash script would treat spaces as new lines?

---

### Post by SeijiSensei on 2010-11-14
This is a common problem, and a quick Google search brought up many answers.  I've encountered this problem myself in the past but forgot how I fixed it.  The simplest method is to use the IFS environment variable to make the field separator be a newline rather than a space.  See [this article](http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html) for a good presentation of this method.

---

### Post by thegodfaza on 2010-11-14
> **SeijiSensei said:**
> This is a common problem, and a quick Google search brought up many answers.  I've encountered this problem myself in the past but forgot how I fixed it.  The simplest method is to use the IFS environment variable to make the field separator be a newline rather than a space.  See [this article](http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html) for a good presentation of this method.

Thanks for the help. I don't understand though why BASH decides to think of spaces as new lines instead of a space.

---

### Post by SeijiSensei on 2010-11-14
It doesn't "think" of them as new lines.  It treats spaces as field delimiters.  So when you iterate over the contents of a string with embedded spaces, it considers each non-blank item a separate object.  The fact that they appeared on separate lines in your output was the result of using echo, which appends a newline to the end of each string it displays (unless you use the -n switch).

---

