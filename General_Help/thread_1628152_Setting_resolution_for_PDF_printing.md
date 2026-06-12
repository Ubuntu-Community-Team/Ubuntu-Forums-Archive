---
title: "Setting resolution for PDF printing"
date: 2010-11-22
forum: General Help
---

### Post by gshresth on 2010-11-22
Someone has sent me a PDF file created by scanning a document at unnecessarily high resolution, resulting in a large sized file. I thought I would just print the file again to a PDF printer, this time setting a lower resolution, and thus get a smaller sized PDF file.  I have CUPS-PDF printer installed, which has a tab where one can set resolution (anything from 150 to 2400 dpi).  However, no matter what resolution I choose here, the resulting PDF remains the same size.  Is the resolution setting 'broken', or am I doing something wrong?  Any help would be appreciated.  (I am using Ubuntu 10.04.)

---

### Post by anglican on 2010-11-22
> **gshresth said:**
> Someone has sent me a PDF file created by scanning a document at unnecessarily high resolution, resulting in a large sized file. I thought I would just print the file again to a PDF printer, this time setting a lower resolution, and thus get a smaller sized PDF file.  I have CUPS-PDF printer installed, which has a tab where one can set resolution (anything from 150 to 2400 dpi).  However, no matter what resolution I choose here, the resulting PDF remains the same size.  Is the resolution setting 'broken', or am I doing something wrong?  Any help would be appreciated.  (I am using Ubuntu 10.04.)I'd just use ghostscript for this. To make it easier you can put the following into a file called e.g. /usr/local/bin/pdf2pdf:
```
#!/bin/sh
#
# Convert a PDF to another PDF. This effectively strips out a lot of
# bogus stuff from most PDF files.

gs=`which gs 2>/dev/null`
if [ ! -x "$gs" ]; then
    echo "Error: install ghostscript first" >&2
    exit 1
fi

OPTS=""
pdfver="1.2"
while true; do
    case "$1" in
    --pdf-version)
        shift
        pdfver="$1"
        ;;
    -?*) OPTS="$OPTS $1";;
    *) break;;
    esac
    shift
done

if [ $# -eq 2 ]; then
    outfile="$2"
elif [ $# -eq 1 ]; then
    outfile="`basename \"$1\" .pdf`.new.pdf"
else
    cat <<EOF >&2
Usage: pdf2pdf [--pdf-version (1.2|1.3|1.4)] [gs-options ...] <input.pdf|-> [output.pdf|-]

Converts a PDF from whatever PDF specification version it currently
exists as to the one specified by \`--pdf-version'. Default: 1.2

One side-effect of this conversion is the resulting document will have
the no-printing and no-copying flags removed in the output document if
they are set in the input document.
EOF
    exit 1
fi

exec "$gs" $OPTIONS -q -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite \
    -dCompatibilityLevel="$pdfver" -sOutputFile="$outfile" -f "$1"
```Then ```
chmod 755 /usr/local/bin/pdf2pdf
```and you can then use it as a command to change the resolution of your pdf file:
```
pdf2pdf -r150 original.pdf newfile.pdf
```which would output 150dpi pdf.

H

---

### Post by gshresth on 2010-11-23
Many thanks for your help Anglican, but I'm completely unfamiliar with the command line!  When I navigate to the usr/local/bin folder on the computer, there are no files or folders in it.  I tried creating a file in gedit editor (with the code you have provided) and saving it in the usr/local/bin folder, but the system says I don't have permission to save it there.  I presume I need to be 'root' or something, but am not clear how to do that.  Do I just open the terminal and type 'sudo'?  

Also, shouldn't there be a simpler GUI-based way to reprint a pdf at a lower resolution?  Why doesn't setting a lower resolution in the 'print' dialogue box do the trick?

---

### Post by stoneage on 2010-11-23
You can also use Gimp.

Open the .pdf, set the print size / resolution, and print it to a file.

---

### Post by anglican on 2010-11-24
> **gshresth said:**
> Many thanks for your help Anglican, but I'm completely unfamiliar with the command line!  When I navigate to the usr/local/bin folder on the computer, there are no files or folders in it.  I tried creating a file in gedit editor (with the code you have provided) and saving it in the usr/local/bin folder, but the system says I don't have permission to save it there.  I presume I need to be 'root' or something, but am not clear how to do that.  Do I just open the terminal and type 'sudo'?  
Yes, just type "sudo gedit /usr/local/bin/pdf2pdf" and copy and paste the text into it.
> **gshresth said:**
> Also, shouldn't there be a simpler GUI-based way to reprint a pdf at a lower resolution?  Why doesn't setting a lower resolution in the 'print' dialogue box do the trick?Maybe there should be (maybe there is) a simpler gui way. ;)

H

---

### Post by gshresth on 2010-11-25
Thanks, Anglican!  Figured it out with your help, and it works very well!  

Stoneage - Thanks, but with GIMP it is difficult to handle multiple-page PDFs, isn't it?  It seems to treat each page separately...

---

### Post by stoneage on 2010-11-26
Yes. You would have to collate them afterwards. I don't know what to recommend for that. I know PDFedit can do it, but there might be something better.

---

