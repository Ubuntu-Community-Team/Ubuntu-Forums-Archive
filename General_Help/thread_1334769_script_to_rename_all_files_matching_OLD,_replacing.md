---
title: "script to rename all files matching OLD, replacing that with NEW"
date: 2009-11-22
forum: General Help
---

### Post by senor_smile on 2009-11-22
I have been tinkering, trying my own scripts and googling without success.  I seek a script that would:

take all files in the current directory that have the text $OLD(as an example variable of course)  and change that portion of the text file name to $NEW.   I can get it done fairly easily, except that there are spaces and other characters, (e.g. ( ) ) in the file names.  Does any one have a good script to accomplish this?  The closest I got was converting all spaces to _'s:

```
for x in *\ *;

do 

y=$(echo "$x"| sed y/\ \/_/)

mv "$x" "$y" 

done
```

and then doing regular text replacement with:

```
for i in $(ls *$ORIGINAL*)
do
	mv -f $i ${i/$ORIGINAL/$NEW}
done
```

where 


```
ORIGINAL="some_text"
NEW="new_text"
```

That leaves my file names not matching the rest(i.e. all spaces have underscores now), and as much as I know it's recommended to not use spaces, sometimes people just really want things that way.

---

### Post by kaibob on 2009-11-22
It's not clear to me if you want to replace the text in a text file or simply rename files. Assuming the latter, the rename utility is probably the easiest approach. Just change to the target directory and enter the following: 

rename -n 's/some_text/new_text/' *.ext

You will need to change old_text, new_text, and ext to whatever applies. The -n option directs rename to do a dry run and report proposed changes. Change -n to -v to actually rename the files. This works fine with file names that contain spaces and parentheses.

---

### Post by senor_smile on 2009-11-22
That was way too easy.  I learn something new every day.  Thanks a million. 

Too bad I renamed a few hundred files manually in nautilus before I figured this out!

---

### Post by mo.reina on 2009-11-22
another way to do it would be to use double quotes to catch the spaces:

ex. 
```
oldname="file.txt"
newname="this is a test"

mv $oldname "$newname"

```
this doesn't work without the double quotes as the field separators in bash are spaces, new lines, and tabs by default.

---

