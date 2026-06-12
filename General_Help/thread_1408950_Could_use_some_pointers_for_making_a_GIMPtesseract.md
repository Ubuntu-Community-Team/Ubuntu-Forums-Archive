---
title: "Could use some pointers for making a GIMP/tesseract script"
date: 2010-02-17
forum: General Help
---

### Post by kudzu on 2010-02-17
Hey guys, 

I'm currently undertaking the ridiculously stupid task of using tesseract ocr to convert a scanned 1,000 page .pdf document into .txt documents (I volunteered to do it for a girl - I'm pathetic, I know).  I import one page of the .pdf at time in GIMP, convert it to indexed colors, save it as an uncompressed .tif, and then run tesseract in a terminal on the saved .tif, after which it spits out a .txt file (which I instruct tesseract to name after the page number of the .tif, for example 537.tif becomes 537.txt).    

This process takes about a minute per page, so at 1,000 pages we're looking at 1,000 minutes.  That's a lot of minutes.    

I've looked into scripts some and I understand the very basics, but I don't know how to make a program, like GIMP, perform several specific functions in succession (import, convert to indexed colors, save as uncompressed .tif), and then have another program, like tesseract, perform its function after the completion of the prior program's function.  I'm not trying to ask anyone to do my work for me, but could someone give me some advice regarding this, or point me in the direction of a newbie-friendly how-to that might help me out?  I haven't found any.  I'd like to finish this thing quickly, so as to maximize girl-impressing potential. 

Thanks.

---

### Post by kudzu on 2010-02-18
If it helps, I found [this]("http://www.groklaw.net/articlebasic.php?story=20061210115516438") link with some sort of script for tesseract, but I don't understand the instructions:


**"Fred Smith's scripts** 
 Here are Fred's scripts as he sent them to me, for those who don't need a how to:
 I've been hacking at some scripts and wanted to pass on to you my latest versions. I think they will work better and also be easier to use.  Instead of viewing the online PDF and printing to file, with these scripts you will need to have a local copy of the PDF, because we now use a new script named "pdf2tif" to turn the pdf directly into a tif file without any intermediate ps file. It seems to give considerably better resolution on the text (the tif file sure looks a lot better). It's not clear how much better the OCR'd result is, but I'd think it would be at least a little better (after all, these documents are pretty poor quality to start with.)
  You'll want to put this in your path somewhere (I put mine in /usr/local/bin) and make sure to give it execute permission.
  Here's pdf2tif:
  -----------------------------
 #!/bin/sh
# Derived from pdf2ps.
# $Id: pdf2tif,v 1.0 2006/11/03  Fred Smith
# Convert PDF to TIFF file.
  OPTIONS=""
while true
do
  case "$1" in
  -?*) OPTIONS="$OPTIONS $1" ;;
  *)  break ;;
  esac
  shift
done
  if [ $# -eq 2 ]
then[INDENT]      outfile=$2[/INDENT]elif [ $# -eq 1 ]
then[INDENT]      outfile=`basename "$1" .pdf`-%02d.tif [/INDENT]else[INDENT]      echo "Usage: `basename $0` [-dASCII85EncodePages=false][/INDENT][-dLanguageLevel=1|2|3] input.pdf [output.ps]" 1>&2[INDENT]      exit 1[/INDENT]fi
  # Doing an initial 'save' helps keep fonts from being flushed between pages.
# We have to include the options twice because -I only takes effect if it
# appears before other options.
exec gs $OPTIONS -q -dNOPAUSE -dBATCH -dSAFER -r300x300 -sDEVICE=tiffg3
"-sOutputFile=$outfile" $OPTIONS -c save pop -f "$1"
 --------------------------
  and here's the latest version of ocr.sh. To use this, edit the value for the variable "progdir" to point to wherever your tesseract binary is located. also, put it somewhere convenient and give it execute permission. It leaves the resulting .txt files (one per page) in your current directory.
  -------------------------------
 #!/bin/sh
  # takes one parameter, the path to a pdf file to be processed.
# uses custom script 'pdf2tif' to generate the tif files,
#   generates them at 300x300 dpi.
# drops them in our current directory
# then runs $progdir/tesseract on them, deleting the .raw
# and .map files that tesseract drops.
  pdf2tif $1
  # edit this to point to wherever you've got your tesseract binary
progdir=..
  for j in *.tif[INDENT]          do
         x=`basename $j .tif`
         ${progdir}/tesseract ${j} ${x}
         rm ${x}.raw
         rm ${x}.map[/INDENT]#un-comment next line if you want to remove the .tif files when done.
#       rm ${j}
done"

Can anyone tell me if this script does what I need it to do, and how I can implement it?

---

### Post by kudzu on 2010-02-18
No tips?

---

