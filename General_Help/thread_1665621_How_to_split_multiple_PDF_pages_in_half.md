---
title: "How to split multiple PDF pages in half?"
date: 2011-01-12
forum: General Help
---

### Post by svetiev on 2011-01-12
Hi everyone.

I wish to do something and please tell me if it's even possible and if yes, how can it be achieved.

I have a PDF file of scanned book of which every PDF page contains two pages from the scanned book. The PDF file is unlocked.

So is there a way that I can split those pages in half and then compile them back into a single PDF file?

What program can I use to do that, do I need to make some kind of a script for it and how?

The split parameters for all the pages are the same.

It's a fairly logical concept so I guess that a computer should be able to perform this kind of operation.

Any kind of help would be appreciated, thanks.

---

### Post by howefield on 2011-01-12
The application I use for splitting/merging pdf pages is pdfchain, there are several others all available for download using the Ubuntu Software Centre.

Hang off for a little while, you'll get plenty of suggestions.

---

### Post by svetiev on 2011-01-12
> **howefield said:**
> The application I use for splitting/merging pdf pages is pdfchain, there are several others all available for download using the Ubuntu Software Centre.

Hang off for a little while, you'll get plenty of suggestions.
Thanks for this program it will be very useful when I have to put the file back together. But still my main problem is splitting each individual page into two symmetrical halves. 

Is there a way to do this?

---

### Post by svetiev on 2011-01-12
I tried PDFedit in the mean time and i'm trying to make things work, but i'm a bit confused with the interface.

I used the Edit Page Metrics option, but all it does is hide parts of the page. I thought it would work more like a crop function but that is not the case.

Does anybody actually understand what I want to do? 

I have a 60 page pdf of which every page needs to be CUT in half so I end up with a 120 page pdf.

That's as simply as I know how to put it. Now the question remains - How do I do it?

anybody?

---

### Post by PoseidonOSU on 2011-04-01
I know this is an old thread but maybe the solution will help someone else like myself who is searching.

While searching I thought of the answer and it is SUPER easy.

I opened it with my viewer and then told it to print and selected print to pdf file and selected pages 1-6 and did the same thing with pages 7-12 and I quickly had my 12 page monster pdf split in to two smaller pdfs.

---

### Post by howefield on 2011-04-01
> **PoseidonOSU said:**
> While searching I thought of the answer and it is SUPER easy.

Not quite so SUPER easy. 

Not sure if the OP ever solved the issue, but he wanted to cut each of 60 pages in half.

---

### Post by dingodog on 2011-04-02
> **svetiev said:**
> 
I wish to do something and please tell me if it's even possible and if yes, how can it be achieved.

I have a PDF file of scanned book of which every PDF page contains two pages from the scanned book. The PDF file is unlocked.

So is there a way that I can split those pages in half and then join them back into a single PDF file?

I also had in past this needs and I wrote a little script (named **splitinhalf**):

but first you need to extract images from pdf

```
pdfimages -j file.pdf 0
```

then run this **[COLOR=Red]script[/COLOR]** **[COLOR=SeaGreen](if images have extensions different than jpg, modify conveniently) [/COLOR]**
```
#!/bin/sh
if [ ! -e even-odd ]; then mkdir even-odd; fi
first="`ls -1 *.jpg | head -n1`"
let "halfwidth=`gm identify -format '%w \n' $first`/2" 
width="`gm identify -format '%w \n' $first`"
height="`gm identify -format '%h \n' $first`"
for FILE in *.jpg ; do convert -crop "$halfwidth"x"$height"+0+0 "$FILE" "$FILE-A.jpg" ; mv `ls *.jpg | grep A` even-odd ; convert -crop "$width"x"$height"+"$halfwidth"+0 "$FILE" "$FILE-B.jpg" && mv `ls *.jpg | grep B` even-odd
 done ; 
```

it uses imagemagick. It creates a new directory, then calculates automatically height and width from first picture of series, and split images at half, then move in directory created

once we have all splitted single images, there are several ways to putting inside a new multipage pdf

**podofoimg2pdf**
**sam2p with this [COLOR=Red]script[/COLOR] [COLOR=SeaGreen](change extension if different from png)[/COLOR]**
```
#!/bin/bash

directory=`pwd`

for file in $directory/*.png
do
   filename=${file%.png}
   sam2p $filename.png $filename.pdf
done
```
then use **pdftk**
```
pdftk *.pdf cat output file.pdf
```

---

### Post by l0tusmonk on 2011-04-07
Hi, 
you probably have the answers by now, but I came across this thread while trying to find the answer to the exact same question. 
In another thread, I´ve found a link to this application which does the exact thing I needed it to do. 

```
http://sourceforge.net/projects/briss/
```

It scans the .pdf file, shows a "merged" preview of the whole file on which you can set (draw) the boarders of the new pages. Then it cuts the pages up according to your borders and saves a new .pdf file with the defined sections of old pages in the correct order.

---

### Post by keng02 on 2011-04-07
Ive decided to remove Ubuntu from my laptop as i am going to install it on to my Desktop, but i'm [unable]("http://www.hermesbagsseller.com") to boot from discs. I only have Ubuntu installed on my laptop and no dual booting and i want to install windows on to it and remove ubuntu. Not even the official window discs work when booting. Any ideas? :sad:

---

### Post by HermanAB on 2011-04-07
When all else fails, you can use The Gimp.

---

### Post by dingodog on 2011-04-07
> **l0tusmonk said:**
> Hi, 
```
http://sourceforge.net/projects/briss/
```It scans the .pdf file, shows a "merged" preview of the whole file on which you can set (draw) the boarders of the new pages. Then it cuts the pages up according to your borders and saves a new .pdf file with the defined sections of old pages in the correct order.
**Briss,** does nor really **cut** the pdf page, but sets the **cropbox** in pdf to a value conveniently in order to show only selected area

in fact, the whole facing scanned image remains in pdf

if you use **pdfimages** in a cropped pdf with **Briss**

you can see that it extracts the whole image representing two facing pages scanned at once

---

