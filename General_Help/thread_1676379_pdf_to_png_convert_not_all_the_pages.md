---
title: "pdf to png convert not all the pages"
date: 2011-01-27
forum: General Help
---

### Post by Cowboybebop79 on 2011-01-27
At the moment I regularly use Image Magick convert command to convert PDF's to images which is great but I would like to only convert some of the pages in the PDF instead of them all. Im sure the function must be available I just haven't been able to find it even after bashing google for a few days.

```
convert *full.pdf test%d.jpg
```

this is the command I use at the moment.

Any help would be appreciated

---

### Post by lykeion on 2011-01-27
I don't think you can do that with ImageMagick/convert.
You can use poppler-utils/pdftohtml to convert the pdf to html where you can set from and to pages.
Install poppler-utils:
```
sudo apt-get install poppler-utils
```
Example convert pages 1-5 to html:
```
pdftohtml -f 1 -l 5 -c input.pdf output.html
```

---

### Post by anglican on 2011-01-27
> **Cowboybebop79 said:**
> At the moment I regularly use Image Magick convert command to convert PDF's to images which is great but I would like to only convert some of the pages in the PDF instead of them all. Im sure the function must be available I just haven't been able to find it even after bashing google for a few days.

```
convert *full.pdf test%d.jpg
```

this is the command I use at the moment.

Any help would be appreciatedHow about using ghostscript, something like:

```
gs -dFirstPage=2 -dLastPage=3 -q -dNOPAUSE -dSAFER -dBATCH -sDEVICE=png256 -sOutputFile=output.png -f input.pdf
```


H

---

### Post by Cowboybebop79 on 2011-01-28
Thanks for the suggestions

in the end I found a blog by [Sandeep Sidhu]("http://sandeepsidhu.wordpress.com/2010/12/11/extract-pages-from-a-pdf-file-in-ubuntu-10-10/") where he had a similar problem of extracting individual pages from a pdf in his solution he created a function in bashrc to shorten the command.


```
function pdf-extract()
{
# this function uses 3 arguments:
# $1 is the first page of the range to extract
# $2 is the last page of the range to extract
# $3 is the input file
# output file will be named "inputfile_pXX-pYY.pdf"
gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH -dSAFER \
-dFirstPage=${1} \
-dLastPage=${2} \
-sOutputFile=${3%.pdf}_page${1}_to_page${2}.pdf \
${3}
}
```


@anglican thanks for pointing out that ghostscript can output to image so I combined your suggestion with Sandeep's function and I get this


```
function pdf-extract()
{
# this function uses 3 arguments:
# $1 is the first page of the range to extract
# $2 is the last page of the range to extract
# $3 is the input file
gs -sDEVICE=jpeg -dNOPAUSE -dBATCH -dSAFER -dJPEGQ=100 \
-dFirstPage=${1} \
-dLastPage=${2} \
-sOutputFile=doc-%02d.jpg \
${3}
}
```

after adding this to bashrc the command to produce images is this
```

pdf-extract 2 5 *.pdf
```


Sweet :guitar:

---

