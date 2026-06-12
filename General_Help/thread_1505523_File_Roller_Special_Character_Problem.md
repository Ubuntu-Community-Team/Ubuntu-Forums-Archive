---
title: "File Roller Special Character Problem"
date: 2010-06-09
forum: General Help
---

### Post by devehf on 2010-06-09
I am trying to extract files from a .ZIP archive with File Roller 2.28.1. The filenames have special characters. Also there is a folder with a special character. "Ö" = or the letter O with umlaut.

When I try to extract I get the error:
caution: filename not matched:  Lindstr\?\?m ....

Where the folder is named "Lindström ..." if the encoding was displayed correctly. 

How can I either enable proper encoding for this application so it doesn't produce this error or rename the folder/files?

When I try to rename the folder I get the error:
An error occurred while adding files to the archive.

Thanks,
Dave

---

### Post by fugowie42 on 2011-01-17
There's likely a more sophisticated way to do this, but I just use the unzip command from the terminal. In Lucid you can actually just open up the terminal, type 'unzip' and then drag the file directly into the terminal after the command (rather than navigating there through cd). 

Hit enter once and it may open up file roller; close that, and hit enter again and it will extract the files to wherever your default extract location is (mine is in my home folder).

Hope that helps

---

### Post by devehf on 2011-02-02
Thanks for the suggestion fugowie42, but when I do this, the archive is not unzipped on the 2nd enter key entry. Instead the File Roller GUI opens again and again.

---

### Post by ragnaroek-hh on 2011-02-08
i tried out in 10.4LTS this way:

please install the package p7zip-full.

now, in file roller you will find a strange different character for umlaute: ""

with this character, you can extract or open as expected. However, you will still miss the desired one.

not SOLVED but fine enough for most users...

---

