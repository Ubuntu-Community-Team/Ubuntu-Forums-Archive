---
title: "Programm for book scanning / OCR"
date: 2011-04-15
forum: General Help
---

### Post by ELMIT on 2011-04-15
I want to scan in a book and convert it to a pdf AND make an OCR text of it.

I am looking for somebody who can help me to gie me some BASH helps to combine the pieces I have already got:

Workflow:

1. scan in the book pages:
coverpage (=1), page 3, page 5, page 7 .... n
(At this point the book is upside down)

2. scan in the book pages 
turn the book and scan from the back to the front:
back coverpage (= n-1), page n-3, page n-5 .... 2

3. run the program (thats where I need the help)

All scanned images are in directory scannedimages

#!/bin/bash
mkdir temppic
for i in `find scannedimages/*.png`
	do
		if [ "$i" = "." ]; then
			echo "We do not work in the root directory"
		elseif [ "$i" <= n ]; then 
			do
			b=`echo $i|cut -f2 -d "/";
			convert -rotate 180 $b/image_i temppic/image-(2i - 1)
			done
		elseif [ n < "$i" <= 2n ]; then
			do
			cp image_i temppic/image-(2n - 2i +2)
			done
		fi
done

convert temppic/*.png mybook.pdf
rm -rf temppic

---

For the ocr I found that part:

#!/bin/sh
PAGES=100 # set to the number of pages in the PDF
SOURCE=book.pdf # set to the file name of the PDF
OUTPUT=book.txt # set to the final output file
RESOLUTION=600 # set to the resolution the scanner used (the higher, the better)

touch $OUTPUT
for i in `seq 1 $PAGES`; do
    convert -monochrome -density $RESOLUTION $SOURCE\[$(($i - 1 ))\] page$i.tif
    tesseract page$i.tif page$i
    cat $OUTPUT page$i.txt > temp.txt
    rm $OUTPUT
    rm page$i.tif
    rm page$i.txt
    mv temp.txt $OUTPUT
done


I have the idea how to make it, but I have no knowledge how to program it.

Maybe something like that exists already and I can save the programming effort.

---

### Post by rpalyvoda on 2011-05-04
Hi,

You may give a try to gscan2pdf, it's a nice and simple tool **with GUI** :), and works fast. It's also got tesseract ocr, but I haven't tried it.

---

