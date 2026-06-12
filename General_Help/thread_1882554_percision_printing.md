---
title: "percision printing?"
date: 2011-11-17
forum: General Help
---

### Post by jeff.sadowski on 2011-11-17
I need to manipulate print jobs so that it lines up with a sticker. The input is from two sources.
One source is from what ever driver I can choose for a windows xp machine to send to my samba server. I am trying the [HP Color LaserJet PS] print driver as I was told it sends a clean postscript document. If I use the tool ps2pdf on these documents the output pdf looks good. The problem is when I print the pdf or postscript it is about a quarter of an inch high on the page. I looked at trying to manipulate the cups driver but with no luck. I tried modifying the ImageableArea in the printer ppd file
the original entry was
*ImageableArea Letter/Letter: "12 08 600 784"
I changed it to
*ImageableArea Letter/Letter: "40 08 600 784"
No change.
I also tried using the command line option page-top
lpr -o page-top=40 -P myprinter mypostscriptfile.ps
Those options are just flat out ignored. No change in the output from the printer.
So I'm thinking there is maybe a tool to move the items down on the page, just a bit, so that the part I need lines up with the sticker I need it to line up with. I tried converting it to a jpg which I can align using image manipulation command line tools but the output text looks horrible. There is both text and a small image that needs moved down on the page. If someone knows of a tool that I could use that modifies a postscript document for such a purpose I'd like to know what it is. I'd like to use something with a syntax as follows
> 
postscriptmanipulator -movedown xx pixles


The other source sends raw text data. Which is relatively easy to deal with. convert from imagemagick works like a champ.
I created the following script to deal with the text
> 
#!/bin/bash
#this is the mvg file created to tell convert what to do.
drawing="${1}.mvg"
#output name
output="${2}"
#spacing between lines
modifyer="${3}"
#font point size
pointsize="${4}"
#space between letters
kerning="${5}"
#jpg image of form
background="${6}"
#starting vertical position
y="${7}"
#starting horizontal position
x="${8}"

cat $1 |
(
IFS=
echo -n > ${drawing}
while read line;do
 if [ "`echo -e "${line}" | awk '{print $1}'`" != "" ];then
  echo -e "text ${x},${y} '$line'" >> ${drawing}
 fi
 y=`echo ${y} ${modifyer}|awk '{print $1+$2}'`
done
)

convert ${background} -font Courier-Bold -pointsize ${pointsize} -kerning ${kerning} -draw @${drawing} ${output}
rm -rf ${drawing}


---

### Post by efflandt on 2011-11-17
I don't know if Linux (or your printer) defaults to try to print the entire page within the printable area (like Windows does by default for pdf files).  If so, maybe that shrinks/moves something when you try to print a full page PS file.

How are you actually creating the text with graphics for the labels and have you tried either opening the original document in LibreOffice (or OpenOffice) Writer (instead of generating PS) and getting it to line up like you want on plain paper before printing to labels?

---

