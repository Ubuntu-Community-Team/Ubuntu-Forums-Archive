---
title: "Rename all files listed in a text file"
date: 2009-08-27
forum: General Help
---

### Post by infinitejones on 2009-08-27
I've used the Search GUI (Places->Search for files) to generate a text file called img.txt, containing the paths to about 250 .jpg files scattered throughout a set of directories and sub-directories. I'd like to rename all of those files to 'folder.jpg'. (There's never more than one .jpg file in any given sub-directory - I've manually checked!)

I'm sure there's a simple command line way of doing this, using the text file as the input list, but I can't quite get my head around it - any suggestions?

Thanks!

---

### Post by kaibob on 2009-08-27
> **infinitejones said:**
> I've used the Search GUI (Places->Search for files) to generate a text file called img.txt, containing the paths to about 250 .jpg files scattered throughout a set of directories and sub-directories. I'd like to rename all of those files to 'folder.jpg'. (There's never more than one .jpg file in any given sub-directory - I've manually checked!)

Based on some brief tests, the following shell script appears to do what you want. 

```
#!/bin/bash

while read line ; do
   path="${line%/*}"
   directory="${path##*/}"
   extension="${line##*.}"
   cp "$line" "${path}/${directory}.${extension}"
done < /path/to/img.txt
```

A few comments:

* You didn't indicate otherwise, so I assumed that you want to leave the files in their original directories. 

* I assumed that the file listings in img.txt are newline separated and are in the format /path/to/picture.jpg. I believe this is the format that results from the use of the "Save Results As..." option in the GUI search. 

* I used cp rather that mv as a precaution.

* As mentioned above, I tested this with a few files but be sure to have backups just in case.

* You mentioned that all the files have a jpg extension. That being the case, you could use that in the script and not extract the extension.

---

### Post by infinitejones on 2009-08-27
Brilliant - thanks for this. 

Before running it I'm going through it to make sure I understand what each line does (a problem is an opportunity to learn something, etc etc) and I can't work out how the script knows that it's actually supposed to change the filenames to folder.jpg. Can you explain?

To answer your comments:
[LIST]
[*]Yes, leave in original directories
[*]Yes, that's the format of img.txt
[/LIST]

Thanks!

---

### Post by infinitejones on 2009-08-27
A-ha. I've just run the script on a couple of files and realised what it does.

I actually want to rename all of the images "folder.jpg", not [the name of the folder that this image is in].jpg

So... knowing that, I think I can work out what to change in the script... let me see...

Nope, that didn't work. Can someone explain to me (or point me somewhere that explains) what's going on with the #, $ and % signs?

Once again - thanks!

---

### Post by DaithiF on 2009-08-27
then you don't need the directory and extension lines and can change the cp line to:
```
cp "$line" "${path}/folder.jpg"
```

the directory="${path##*/}" is an example of bash string replacement.  
This guide is a useful reference:
[http://devmanual.gentoo.org/tools-reference/bash/index.html](http://devmanual.gentoo.org/tools-reference/bash/index.html)
in particular if you scroll down to the String Replacements section you'll see some of what kaibob was doing explained.

---

### Post by kaibob on 2009-08-27
> **infinitejones said:**
> A-ha. I've just run the script on a couple of files and realised what it does. I actually want to rename all of the images "folder.jpg", not [the name of the folder that this image is in].jpg...
Sorry about that. It should have, but it didn't occur to me that you wanted to actually rename all of the files to folder.jpg. It was late, and I guess I wasn't thinking well. 

The changes suggested by DaithiF will correct the script. In addition to the reference suggested by DaithiF, you may want to review the following, which has a lot of useful information and examples:

[http://bash-hackers.org/wiki/doku.php/syntax/pe](http://bash-hackers.org/wiki/doku.php/syntax/pe)

---

### Post by infinitejones on 2009-08-29
Thanks Kaibob and DaithiF! Works perfectly.

---

