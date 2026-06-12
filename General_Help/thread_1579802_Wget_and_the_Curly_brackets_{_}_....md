---
title: "Wget and the Curly brackets { } ..."
date: 2010-09-22
forum: General Help
---

### Post by giaz753 on 2010-09-22
Hi everybody,

I'm Carlo from Italy, and, since I'm using Linux from 2002, this is my first post on the Ubuntu forum!

I need a help with wget.

The command:

wget www.abc.com/{001..005}/{1..3}.pdf

will result in:

URL of downloading file         => downloaded file

wget [www.abc.com/001/1.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/001/1.pdf&embedded=true&chrome=true")        => 1.pdf
wget [www.abc.com/001/2.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/001/2.pdf&embedded=true&chrome=true")        => 2.pdf
wget [www.abc.com/001/3.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/001/3.pdf&embedded=true&chrome=true")        => 3.pdf
wget [www.abc.com/002/1.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/002/1.pdf&embedded=true&chrome=true")        => 1.pdf.1
wget [www.abc.com/002/2.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/002/2.pdf&embedded=true&chrome=true")        => 2.pdf.1
wget [www.abc.com/002/3.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/002/3.pdf&embedded=true&chrome=true")        => 3.pdf.1
wget [www.abc.com/003/1.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/003/1.pdf&embedded=true&chrome=true")        => 1.pdf.2
wget [www.abc.com/003/2.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/003/2.pdf&embedded=true&chrome=true")        => 2.pdf.2
wget [www.abc.com/003/3.pdf]("https://docs.google.com/viewer?url=http://www.abc.com/003/3.pdf&embedded=true&chrome=true")        => 3.pdf.2
and so on ...

but what I want in my download directory is:

1.pdf 2.pdf 3.pdf 4.pdf 5.pdf etc etc

and not:

1.pdf 2.pdf 3.pdf 1.pdf.1 2.pdf.1 3.pdf.1 1.pdf.2 etc etc

How could I resolve that?
I know that the -O option will not work (I will have only one big file resulting from the concatenation of all the downloaded files).
Probably I need a bach script but ... I'm not able to write a bash script, someone could help me?
Thank for attention.

---

### Post by SlugSlug on 2010-09-22
wget -r [www.abc.com](www.abc.com)

should grab the folder structure..

---

### Post by giaz753 on 2010-09-22
Yes, but so I will have, in download directory:
directory/folder 001 with inside 1.pdf 2.pdf 3.pdf
directory/folder 002 with inside 1.pdf 2.pdf 3.pdf
directory/folder 003 with inside 1.pdf 2.pdf 3.pdf 
in other words the folder structure (as you suggest)
when I don't want the folder structure ... I want all the files in a directory with a new numeration.
Thank for the attention

---

### Post by SlugSlug on 2010-09-22
try thunrar that has a built in file renamer..  or pyrenamer

---

### Post by giaz753 on 2010-09-22
OK, they will work ... I have to install one of them and, after the download is complete, start the renaming, but wget and bash are powerful tools ... I believe that with little code ...
Sure, if no other solutions will be avaible, yours are good, thank you!

---

### Post by SlugSlug on 2010-09-22
yer it can be done via bash with a litle script -- I just dnt know it :)

---

