---
title: "PDFTK burst task in a Nautilus Script"
date: 2009-08-06
forum: General Help
---

### Post by histographik on 2009-08-06
----------------------------------------------------------
SOLVED!
----------------------------------------------------------
```
apt-get install pdftk
```

> #/bin/bash
name=$(echo $1 | cut -d '.' -f 1)
pdftk $1 burst output ${name}-%03d.pdf

-----------------------------------------------------------
I manage PDFs with pdfjam and pdftk via a collection of Nautilus scripts (One recent revelation was [COLOR=Green]**pdf-shuffler**[/COLOR] which is a great little little GUI to enable joining, reshuffling and exporting pdfs), however, I am unable to create a Nautilus script to do a pdftk *burst *on a number of pdfs with whitespace in their names:

Command Line: *example of tasks require*d (all done on desktop)

1. Create a directory with the name of the pdf and copy the pdf in to it
2. run pdftk burst on the pdf in the newly created directory
3. remove doc_data.txt and any.pdf from the newly created directory
4. all done via a nautilus script. (able to run on multiple pdfs)

_PDFTK Burst: Basic function of splitting a pdf into separate pdf pages_
```
pdftk *.pdf burst
```[I]
**I have tried to modify the pdfjoin script from** [http://g-scripts.sourceforge.net]("http://g-scripts.sourceforge.net/") **to accomplish a pdftk burst task but I get nowhere! Could anyone help me out?**

pdfjoin original script example using pdfjam:
[/I]```
#!/bin/bash
IFS='
'
PDFARGUMENTS=""
fpaths=`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | sort`
for file in $fpaths
do
  if [ -f "$file" ]; then
    base=${file%.*}
    ext=${file##*.}
    if [ "$ext" == "pdf" ]; then
        PDFARGUMENTS="$PDFARGUMENTS \"$file\""
        pdfdir=`dirname "$file"`
    fi
  fi
done
if [ -n "$PDFARGUMENTS" ]; then
    cd "$pdfdir"
    eval /usr/bin/pdfjoin $PDFARGUMENTS
fi
```[I]
[COLOR=Green]**PDF-Shuffler** [/COLOR](See GTK-Apps Web Site)[/I]
[http://www.gtk-apps.org/content/show.php/PDF-Shuffler?content=90610](http://www.gtk-apps.org/content/show.php/PDF-Shuffler?content=90610)


[COLOR=Red]**UPDATES:**[/COLOR]

Tried the following _**without**_ success:

[U][B][COLOR=Blue][How to join together multiple pdfs or seperate a single pdf into multiple pages using pdftk in Ubuntu]("http://www.arsgeek.com/2007/01/11/878/")[/COLOR]
[/B][/U]

---

