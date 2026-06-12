---
title: "Adding page numbers to PDF from terminal"
date: 2012-07-08
forum: General Help
---

### Post by donkyhotay on 2012-07-08
Does anyone know of a way to automatically generate page numbers in a PDF with the terminal? I have been working on a book with a few hundred pages in it that for practical reasons has been broken down into smaller source files. Because this book includes images, charts, diagrams in addition to standard text, my source files for it are in a couple different formats (mostly dia and libreoffice) and I have over 100 different files. To make things easier I wrote a script that takes all these files in all the different formats and 'compiles' them into one big PDF for distribution to my friends and family who have been advising me on it. I would like to be able to modify my script so that it will automatically add page numbers down at the bottom so when I'm done I can just run my script and have them added to the distribution copies. Because of the different formats I can't do it automatically with the source files and I *really* don't want to add all the page numbers by hand, especially because I'm still adding/removing pages which would throw of manual page numbers. I've done some research online and it looks like it might be done with imagemagick but I haven't been able to find a good howto (or better yet a script I can copy/paste into mine) so I'm not certain if it actually can.

---

### Post by kimda on 2012-07-08
Hi. I think you can do this with pdftk. I found this tread talking about how to do it. 

[http://forums.debian.net/viewtopic.php?t=30598](http://forums.debian.net/viewtopic.php?t=30598)

---

### Post by donkyhotay on 2012-07-27
Thanks, that post was exactly what I needed. Using the information there I was able to modify the script I had written to convert multiple libre office files into one big PDF to also add page numbers for me as well. For those that may be interested here is the source code:

```

#!/bin/bash

: '
Copyright 2012:
      Donkyhotay

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA


This script will convert all .odt and .odg files located in ~/book/source
and convert it into one complete PDF document in ~/book folder. I wrote
this script to help me convert multiple individual open office files into one complete
book and add page numbers to the final file automatically. Please note since it uses 
the cups-pdf printer to run it *will* delete all files stored within ~/PDF folder to 
avoid conflicts with other files. Once done it will clear out the ~/PDF folder again 
for cleanup purposes. The script assumes that the individual source file names are numbered 
or at least in alphabetical order for how they will be placed in the final book.
'


echo "Welcome to the Book Creation script"
sleep 2

echo "Checking for dependencies"
OS=$(lsb_release -si)
if ! which pdftk > /dev/null; then
    echo "Dependencies not met: pdftk not found"
    if [ "$OS" = "Ubuntu" ] || [ "$OS" = "Debian" ]; then
        echo "You appear to be running ubuntu or debian do you want me to attempt to install automatically? (y/n)"
        read ANSWER
        if [ "$ANSWER" = "y" ] || [ "$ANSWER" = "Y" ] || [ $ANSWER = "yes" ]; then
            sudo apt-get install pdftk
            if ! which pdftk > /dev/null; then
                echo "Problem with automatic installation, please install manually and try again"
                exit
            else
                echo "pdftk successfully installed"
            fi
        else
            echo "Please install pdftk and try again"
            exit
        fi
    else
        echo "Please install pdftk and try again"
        exit
    fi
fi

OPEN=False
if ! which libreoffice > /dev/null; then
    if ! which openoffice > /dev/null; then
        echo "Dependencies not met: libreoffice not found"
        if [ "$OS" = "Ubuntu" ] || [ "$OS" = "Debian" ]; then
            echo "You appear to be running ubuntu or debian do you want me to attempt to install automatically? (y/n)"
            read ANSWER
            if [ "$ANSWER" = "y" ] || [ "$ANSWER" = "Y" ] || [ $ANSWER = "yes" ]; then
                sudo apt-get install libreoffice
                if ! which libreoffice > /dev/null; then
                    echo "Problem with automatic installation, please install manually and try again"
                    exit
                else
                    echo "libreoffice successfully installed"
                fi
            else
                echo "Please install libreoffice and try again"
                exit
            fi
        else
            echo "Please install libreoffice and try again"
            exit
        fi
    else
        OPEN=True
    fi
fi

if ! which pdflatex > /dev/null; then
    echo "Dependencies not met: pdflatex not found"
    if [ "$OS" = "Ubuntu" ] || [ "$OS" = "Debian" ]; then
        echo "You appear to be running ubuntu or debian do you want me to attempt to install automatically? (y/n)"
        read ANSWER
        if [ "$ANSWER" = "y" ] || [ "$ANSWER" = "Y" ] || [ $ANSWER = "yes" ]; then
            sudo apt-get install texlive
            if ! which pdflatex > /dev/null; then
                echo "Problem with automatic installation, please install manually and try again"
                exit
            else
                echo "pdftk successfully installed"
            fi
        else
            echo "Please install pdflatex and try again"
            exit
        fi
    else
        echo "Please install pdflatex and try again"
        exit
    fi
fi

PDFCHK=$(lpstat -a | grep -c "PDF")
if [ $PDFCHK = 0 ]; then
    echo "Dependencies not met: cups-pdf not found"
    if [ "$OS" = "Ubuntu" ] || [ "$OS" = "Debian" ]; then
        echo "You appear to be running ubuntu or debian do you want me to attempt to install automatically? (y/n)"
        read ANSWER
        if [ "$ANSWER" = "y" ] || [ "$ANSWER" = "Y" ] || [ $ANSWER = "yes" ]; then
            sudo apt-get install cups-pdf
            PDFCHK=$(lpstat -a | grep -c "PDF")
            if [ $PDFCHK = 0 ]; then
                echo "Problem with automatic installation, please install manually and try again"
                exit
            else
                echo "cups-pdf successfully installed"
            fi
        else
            echo "Please install cups-pdf and try again"
            exit
        fi
    else
        echo "Please install cups-pdf and try again"
        exit
    fi
fi

echo "Preparing System"

SPOOLCOUNT=$(lpq -a | grep -c "untitled")
if [ $SPOOLCOUNT != 0 ]; then
    echo "You have print jobs running that may conflict which this script"
    echo "Please wait until print spooler is clear and then try again"
    exit
fi

cd ~/PDF
rm -fr ./*
mkdir ./temp
cd ~/book/source

echo "Converting Files (this may take some time)"
if [ "$OPEN" = "True" ]; then
    openoffice --invisible -pt PDF ./*.odg >/dev/null 2>&1
    openoffice --invisible -pt PDF ./*.odt >/dev/null 2>&1
else
    libreoffice --invisible -pt PDF ./*.odg >/dev/null 2>&1
    libreoffice --invisible -pt PDF ./*.odt >/dev/null 2>&1
fi

#If you need to convert from other formats just add lines to print to PDF printer for the program in question
cd ~/PDF

echo "Clearing Spooler"
OLDSPOOLCOUNT=0
while : 
do
    SPOOLCOUNT=$(lpq -a | grep -c "untitled")
    if [ $SPOOLCOUNT = 0 ]; then
        echo "Spooler Cleared"
        break
    elif [ $SPOOLCOUNT != $OLDSPOOLCOUNT ]; then
        if [ $SPOOLCOUNT = 1 ]; then
            echo $SPOOLCOUNT "job remaining in spooler"
        else
            echo $SPOOLCOUNT "jobs remaining in spooler"
        fi
        OLDSPOOLCOUNT=$SPOOLCOUNT
    fi
done

echo "Calculating Page Numbers"
#If you want to have some pages to not be numbered simply have this script move them to ./temp at this point

pdftk ./*.pdf cat output ./prenumb.pdf

PAGE=$(pdfinfo ./prenumb.pdf | grep "Pages")
PAGE=$(echo $PAGE | cut -c 8-)

echo "Creating Page Number file for "$PAGE" pages"
(
printf '\\documentclass[12pt,letter]{article}\n'
printf '\\usepackage{multido}\n'
printf '\\usepackage[hmargin=.8cm,vmargin=1.5cm,nohead,nofoot]{geometry}\n'
printf '\\begin{document}\n'
printf '\\multido{}{'$PAGE'}{\\vphantom{x}\\newpage}\n'
printf '\\end{document}'
) >./numbers.tex

pdflatex -interaction=batchmode numbers.tex 1>/dev/null

echo "Bursting PDF's"
pdftk prenumb.pdf burst output prenumb_burst_%03d.pdf
pdftk numbers.pdf burst output number_burst_%03d.pdf

echo "Adding Page Numbers"

for i in $(seq -f %03g 1 $PAGE) ; do \
pdftk prenumb_burst_$i.pdf background number_burst_$i.pdf output ./temp/numbered-$i.pdf ; done

echo "Merging .pdf files"
cd ./temp

pdftk ./*.pdf cat output ./book_bloat.pdf

echo "Optimizing PDF file"
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dNOPAUSE \-dQUIET -dBATCH -sOutputFile=book.pdf book_bloat.pdf 2>/dev/null
mv ./book.pdf ~/book/book.pdf

echo "Cleaning Up"
cd ~/PDF
rm -fr ./*
echo "Book Created"

```

---

