---
title: "Mass file renaming"
date: 2006-04-04
forum: General Help
---

### Post by mrogers on 2006-04-04
I've been trying to figure this problem out for ages. I'm fairly certain the key here is regular expressions, but I'm only familiar with the basics. I've read regex tutorials, I've looked for file renaming utilities, but I haven't been able to find anything that meets my needs.

Say I have a folder full of files names like this:

nameofshow.2x01.the_37s.ac3.junkidontwant.avi
nameofshow.2x02.initiations.ac3.junk.avi ...etc

I want them to be named like this:

[2x01] The 37s
[2x02] Initiations

and so on. I know there's got to be some regex magic that can make this happen with a single command, but I can't figure it out. I can match stuff in the original filename, but I'm not sure how to transform it into the format that I want. Or find a good file renamer program that can help me. If someone can help out I'd really appreciate it. Thanks!

---

### Post by Pragmatist on 2006-04-04
There are lots of things you can do by writing scripts.  The only problem is that you won't always get what you need.  So for example, if you always want to take long filenames like this:
 
 thisisalongfilename.ext
 
 And you want to keep the extension (.ext) and the last 3 letters before the extension (here that would be *ame*) Then you can write a script with a simple loop that reads each filename, finds the length of the string of characters that precede the extension, and then retain only the last 3 of those characters along with the extension.  In this scenario, your guideposts are the period (.) and the length of the string.
 
 However, in your example, 
 >  nameofshow.2x01.**the_37s**.ac3.junkidontwant.avi
  nameofshow.2x02.**initiations**.ac3.junk.avi ...etc
 
 If you wanted to keep whatever precedes .ac3 and prepend it to .avi. That is easy.  The same concepts as my example apply.  However, how are you going to automate weird stuff like "when there is a hyphen I want a shorter name!".  You want **37s** you don't want **the_37s **So, again you COULD write rules for that too.  However, it is going to be more complicated and you'll need to know your different scenarios/forms in advance.
 
 The general procedure would be:
 1.) make a **shell script**
 2.) make a **loop** that reads in the current filename
 3.) trim off the main **string** we need to analyze (the one preceding .ac3)
 4.) use a case construct to deal with particular scenarios (i.e. when reading thru each character of the string, if you find an underscore, you shift to the part of the **case construct** that deals with underscores. That code then says to keep everything after the underscore and discard what is before the underscore etc...etc...)
 
 As you can see, you would need to know certain things in advance such as:
 
 1.) What form do these files take?  Is it always string1.string2.stringN.ac3.junk.avi   Or can there be some other extension between the last string and ac3 such as  string1.string2.stringN.foo.ac3.junk.avi  Is the final extension always .avi or do we need to find and record that?
 
 2.) What forms to the 'bad' filenames take (do they have underscores? If they do, how do I want to handle that?  Will taking the portion after the underscore always be what I want? etc...
 
 If you know the answers to those, then what you want to do will take some programming, but shouldn't be that hard.  If you don't know the answers to those questions, then I don't think you can do it.  There are programs that will handle this sort of thing for you (like with mp3s for example).  However, even here, the program is using meta data such as "this part of the file is the artist name, this part is the album name, this is the track number etc...etc..." Then you say which parts you want to keep.

---

### Post by mrogers on 2006-04-04
Thanks for the great reply. I've never done shell scripts, but I'm a programmer so it shouldn't be too hard to pick up. I think a combination of shell scripting with regular expressions might get me where I need to go. I do know all the parameters of how I want the files -- capitalize titles, change underscores to spaces, etc. I guess I'm off to learn shell scripting.

---

### Post by stuporglue on 2006-04-04
You can also use find and rename to do it. rename takes a perl regular expression. It would go something like this:


find . -name filename-or-expression > rename s/oldexpression/newexpression/g

The dot after find means start finding in the current directory, the filename-or-expression is what the filename must match. 

Make a backup copy of the files before renaming, incase something goes bad!

For these
nameofshow.2x01.the_37s.ac3.junkidontwant.avi
nameofshow.2x02.initiations.ac3.junk.avi

This would (I think) remove the NUMBERxNUMBERNUMBER. part of the name

find . -name nameofshow*avi > rename s/\dx\d\d\.//g

\d == a digit
\. == escape the period

Anyways, might be helpfull in your scripit

---

### Post by IYY on 2006-04-04
Here you go:

#!/bin/sh
for name in *.avi
do
        newname="[`echo $name | cut -d\. -f2`] `echo $name | cut -d\. -f3`"
        newname=`echo "$newname" | sed "s/_/ /" | perl -p -e 's/(\w+)/\u\L$1/g'`".avi"
        mv "$name" "$newname"
done

This will do exactly what you want: change the format (that's the 'cut' part), add spaces (that's the 'sed' part) and change the capitalization (the 'perl' part).

---

### Post by jrib on 2006-04-04
[QUOTE=mrogers]I've been trying to figure this problem out for ages. I'm fairly certain the key here is regular expressions, but I'm only familiar with the basics. I've read regex tutorials, I've looked for file renaming utilities, but I haven't been able to find anything that meets my needs.

Say I have a folder full of files names like this:

nameofshow.2x01.the_37s.ac3.junkidontwant.avi
nameofshow.2x02.initiations.ac3.junk.avi ...etc

I want them to be named like this:

[2x01] The 37s
[2x02] Initiations

and so on. I know there's got to be some regex magic that can make this happen with a single command, but I can't figure it out. I can match stuff in the original filename, but I'm not sure how to transform it into the format that I want. Or find a good file renamer program that can help me. If someone can help out I'd really appreciate it. Thanks![/QUOTE]

Since you asked for regex magic, I'll get you started with:

```
rename -n 's/.*\.(.*)\.(.*)\.ac3\..*\.avi/[$1]-$2.avi/' *.avi
```

and that will seem to do what you want with the exception that I am not putting any spaces in the final file since I don't think that is a good idea and the name is going in as it was originally.  I also kept the .avi extension.

Then -n just shows you what it would do, it doesn't actually rename.  If you run it and it says what you want, then just get rid of the -n

here is what happened when I tried it by the way:
```
jasonr@luso:~/temp$ rename -n 's/.*\.(.*)\.(.*)\.ac3\..*\.avi/[$1]-$2.avi/' *.avi
nameofshow.2x01.the_37s.ac3.junkidontwant.avi renamed as [2x01]-the_37s.avi
nameofshow.2x02.initiations.ac3.junk.avi renamed as [2x02]-initiations.avi

```

[edit] I like IYY's solution, maybe it's time to learn some more perl ;)  What I did is basically equivalent to newname="[`echo $name | cut -d\. -f2`] `echo $name | cut -d\. -f3`"

I found a little bug in IYY's solution though, you should change ```
sed "s/_/ /"
``` to ```
sed "y/_/ /"
``` otherwise only the first underscore gets converted to a space

---

### Post by mrogers on 2006-04-05
IYY, thanks so much! That's perfect. I looked up the man pages to those tools too, so I understand how they work and I can apply this to other files! Thanks a lot! (And thanks for the correction, _jason)

---

### Post by Xell on 2006-05-02
Hey, I have been trying to get this rename with regex to work but I have a few problems. It seems that any example I find is either to simple or to complex ;)

Like the threadstarter I want to rename som avi's and I tried to get _jason's rename example to work for my problem but to no avail. My first problem is I dont know what part of the original file the different ./\*()-caracters refer to. My second problem is handeling space. 

To be more concreete: I have alot of files that have capital letters and spaces. I want all non-capital and I want to replace spaces with .  

I dont mind to break down the renaming in several steps as long as I understand the regexp and can convert it to any other rename :)

example:
Name Of Show nxnn someextratext.avi -> name.of.show.nxnn.someextratext.avi

or preferably (but I want to try this my self as second/third step):
Name Of Show nxnn someextratext.avi -> name.of.show.s0nenn.someextratext.avi

thanx for any hints on how this would look

---

### Post by Pragmatist on 2006-05-03
You could install "krename" from synaptic.  I just used it to convert this example filename:
 
 File WITH SpAcEs and Mixed Case.test
 
 to this:
 
 file.with.spaces.and.mixed.case.test
 
 This was very easy.  I did a find/replace " " to "."  (i.e. from space to period)
 
 I used the builtin functions (available in a drop-down window) and selected % to convert to lowercase.  So the template box just had a % in it.
 
 I could have applied this simultaneously to however many files and/or directories that I added.
 
 The only weird thing was the dialog box for adding files.  It was way to small so I couldn't pick files.  However, you can just put it at the command line like this:
 
 krename filename1 filename2 filename3  
 
 or
 
 krename directory1 directory2 directory3
 
 The other suggestions in this thread are good for educating yourself in shell scripting, perl, sed, regular expressions.  However, I would go with this if you want something fast and easy.
 
 Make sure you BACKUP your files and directories that your changing BEFORE experimenting.

---

### Post by Xell on 2006-05-03
thanks. I had acctually installed krename just to try it. I found the upper-to-lower-case funtion, but haden't noticed the "find-replase" function. Thanks for pointing me in the right direction.

---

