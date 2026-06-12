---
title: "How to search in many PDF files?"
date: 2005-02-02
forum: General Help
---

### Post by Shambler on 2005-02-02
I have a lot of PDF files, which I want to search in a whole. Is there any possibiliy/software solution?

Does simply CATting together the files work? Or is there any SQL-Software available that stores all the information in the PDFs?

---

### Post by ubuntu_fan on 2005-02-02
[QUOTE=Shambler]I have a lot of PDF files, which I want to search in a whole. Is there any possibiliy/software solution?

Does simply CATting together the files work? Or is there any SQL-Software available that stores all the information in the PDFs?[/QUOTE]

Being a Linux-based site, I'm guessing you're talking about the MySQL equivalent for Adobe's IFilter as used by the Microsoft Indexing Service (allows freetext searching of PDFs on Windows platforms).

Not sure if such a thing exists, but I'd be *really* surprised if there wasn't a way to do it.

---

### Post by john_c on 2005-02-02
Hello:

If I understand the question correctly this should work for you.  Go to a terminal and try:

grep "phrase to search" -r /directory1/

This is a case sensitive search for "phrase to search" and will look in directory1 and any past it (recursively).  I tried it and it worked well for .pdf files.  It will give error messages so if you want to you can redirect the out put to a file like this:

grep "phrase to search" -r /directory1/ > pdf_search.fil

Then you can use grep again:

grep ".pdf matches" pdf_search.fil

I would redirect this search into a final file, again with > and this file will have the file locations and name, one per line, of each ocurrance of your "phrase to search".

You can use the "cat" command or an editor to view the files you have created.

Hope this is of some help.

John_c

---

### Post by wulf on 2005-02-02
I **haven't** tried the particular type of searching in question but you can avoid creating unnecessary files by piping the output of one command into the input of another - it's one of the tricks that makes command line tools incredibly powerful. Try:

```
grep -r "phrase to search" ./directory1 | grep ".pdf matches" | less
```
That will recursively search, starting in the specified directory, for the string you've provided. The pipeline character (|) then sends the results to the next grep command, which searches for any file containing the string ".pdf matches". Finally, it gets piped again to the less command for easy perusal of the results, although this could also be sent to a file instead.

Wulf

---

### Post by Shambler on 2005-02-02
That's really great! Thanks!

---

### Post by john_c on 2005-02-02
Wulf:

Thanks for that.  I have been working away at these commands and didn't think of that.  A "better way to skin a cat".

Speaking of cats, ours just loves the screen savers with Ubuntu.  She spends quite a bit of time swatting at it and then lies on the monitor and swats at the screen from above.

Bye for now,

John_c

---

### Post by Wim Sturkenboom on 2005-02-03
*grep* does not work on PDF; or at least will not give you all the results that you expected.

May be that [PdfSearch](http://sourceforge.net/projects/pdfsearch) is of help. Did not try it.

A possible workaround is to use *pdftotext* to convert all pdf-files of interest and search through them. Example code below will look for pdf files in a directory and perform a grep (after the PDF is converted to text)```
#!/bin.bash
if [ -z $2 ]
then
  echo "Usage: mypdfsearch path what_you_look_for"
  exit
fi

FILES="$1/*.pdf"
for file in $FILES
do
  echo $file
  pdf2text $file |grep $2
  echo
done
```Save this code as mypdfsearch and make it executable (chmod 755 mypdfsearch).
It's only an example. Modify to suite your needs.

How to run it:```
./mypdfsearch /media/sda/newsletters Wim
```

---

