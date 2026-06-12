---
title: "Rename broken?"
date: 2005-01-25
forum: General Help
---

### Post by martijntje on 2005-01-25
For some reason, i cannot use the rename script in ubuntu.
    
    > $ rename "_broken" "" *
    Bareword "_broken" not allowed while "strict subs" in use at (eval 1) line 1.
    
    This has always worked well for me...
 Oh, and i already tried to comment out the use strict;' line. This stops the error from appearing, however, nothing happens, and no files are renamed then.
    
  >  $ ls -l
  totaal 8
  drwxr-xr-x    2 martijntje martijntje     4096 2005-01-25 18:13 AUDIO_TS
  drwxr-xr-x    2 martijntje martijntje     4096 2005-01-25 18:06 VIDEO_TS
  $ mkisofs -dvdvideo -o 24S3D5.iso .
  mkisofs: -i option no longer supported.
 
 I don't see any -i here [img]http://www.ubuntuforums.org/images/smilies/icon_confused.gif[/img]
  
    Can anyone tell me why this happens, and what i can do to solve it?

---

### Post by mendicant on 2005-01-25
For the second question, it's interpreting -dvdvideo as a bunch of different options, -d -v -d -v -i ...
I think you want -dvd-video.

---

### Post by martijntje on 2005-01-25
My god, that was stupid! I've used mkisofs like a thousand times, and i couldn't even remember that it was -dvd-video...
 
 * makes a mental note to cut back on the white powder *
 
 Anyways, thanks a bunch.

---

### Post by mendicant on 2005-01-25
For the first question--what exactly is that supposed to be renaming?  It looks like it's supposed to be doing something with a file with no name ("") plus all the files in the directory.  I'm not sure exactly what it's supposed to be doing with those files, though.

---

### Post by martijntje on 2005-01-26
It's supposed to remove _broken from all files in the current directory.

The rename command work like this:
$ rename *searchforthis replacewiththis tothesefiles*

Because i want to replace _broken with nothing (thus removing it), the second argument would be empty, therefor, i used quotes to pass an empty argument.

And, as you can see, i ended it with a third argument *, so it works on every file in the directory. I don't see anything being done to files with no names. I don't have files like that (i don't even believe that that is possible!)

---

### Post by mendicant on 2005-01-26
I think you're used to a different version of rename.  Take a look at the manpage for rename, or perldoc rename.  It actually works like this:

rename <perlexpr> [files]

where <perlexpr> "...is a Perl expression which is expected to modify the $_ string in Perl for at least some of the filenames specified..."

which is why I said your command looked a little odd.  And if you want to remove a file called _broken, why don't you just use rm?  I'm fairly sure that rename won't rename a file to the empty string.

---

### Post by matid on 2005-01-26
You want to remove all files which name begins with _broken:
```
rm -rf _broken*
```
You want to remove "_broken" string from filename in all files in the directory:
```
rename "s/_broken//" *
```

---

### Post by martijntje on 2005-01-26
Thanks matid. That did the trick.
I'm still a bit unsure as to why rename is different on ubuntu though, at least i can use it again.

---

### Post by matid on 2005-01-26
This rename is much more flexible thanks to PERL Regular expressions.

---

### Post by rickyrockrat on 2007-10-14
So does anybody know how to remove this 'perl' rename and give me back the rename I've used for years?  Why did they replace rename with an incompatible replacement??  Sometimes I feel like Microsoft build Ubuntu...

---

### Post by kdw on 2008-04-14
> **rickyrockrat said:**
> So does anybody know how to remove this 'perl' rename and give me back the rename I've used for years?  Why did they replace rename with an incompatible replacement??  Sometimes I feel like Microsoft build Ubuntu...

Use the util-linux version, the executable is "rename.ul" and it is part of the default install.

Hope that helps, have a nice day. :)

---

### Post by rickyrockrat on 2008-04-15
> **kdw said:**
> Use the util-linux version, the executable is "rename.ul" and it is part of the default install.

Hope that helps, have a nice day. :)

Well, thanks, but remane.ul is not on my path, and util-linux is installed. Sometimes I just want to break out the tarball and install it the ol' fasioned way - but I now resort to this:
for f in $(ls *.ext); do n=$(echo $f|sed 's!search!replace!'); mv $f $n; done

I should just set up an alias to do this in the shell variables, but I don't use it often enough to remember. *Sigh*

---

