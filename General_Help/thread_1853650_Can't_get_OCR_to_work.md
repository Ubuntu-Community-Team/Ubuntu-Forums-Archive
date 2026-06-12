---
title: "Can't get OCR to work"
date: 2011-10-02
forum: General Help
---

### Post by MarjaE on 2011-10-02
I have installed two OCR programs -

OCRFeeder, which won't open anything, it just freezes up.

And ocrodjvu, which started going wrong with the installation. I installed it, twice, specifically clicking to include the multi-language system, but I ended up without the multi-language support. @#$%. And when I try to use it, I get nothing but error messages and I can't read the manual.

- is there anything I can do to get OCR to work?

P.S. I also installed XSANE, but it's useless w/o a scanner attached. So apparently it only does OCR during scans, and doesn't support OCR on my djvu files. And removed XSANE.

---

### Post by MarjaE on 2011-10-02
I tested OCRFeeder on a 1-page .gif, but I couldn't find any way to set the language, and it came up with gibberish.

---

### Post by MarjaE on 2011-10-03
gscan2pdf might work.

But so far, Tesseract 2.0 has inadequate language support; Tesseract 3.0 has mediocre language support but I can't figure out how to upgrade from 2.0 to 3.0 here.

Cuneiform seems to have better language support, but gscan2pdf isn't compatible with cuneiform.

And I'm having trouble finding out about whether Ocropus has much language support.

---

### Post by MarjaE on 2011-10-03
gscan2pdf isn't compatible with Tesseract 3.0.

I tried using gscan2pdf to convert some sample pages to .png, and then use OCRFeeder on the sample pages, but OCRFeeder still doesn't work.

---

### Post by robert shearer on 2011-10-04
Just a quick drive by before I head off to work and I see that **peyre** has beaten me to a suggested fix for your install YAGF troubles ...
[http://ubuntuforums.org/showpost.php?p=11308566&postcount=2112](http://ubuntuforums.org/showpost.php?p=11308566&postcount=2112)

Let us know how that goes.

Just looking at a few threads you have posted to recently I can't help wondering if there is a resource problem with your machine ?

Would you mind opening a terminal and running..
```
sudo lshw
```

then posting the output here wrapped in code tags(ie copy and paste to your reply then highlight the pasted text and then click on the # icon in the formatting area at the top of the reply window) to manage the large size of the output.
What version of Ubuntu are you running.?
Cheers, Bob.

---

### Post by robert shearer on 2011-10-04
O.K I have just done a fresh install of YAGF and cuneiform and **tested all o.k.**

So here is the step by step guide to get you going...

1)open software centre and search for, then install, the following...
**cuneiform** (this should bring with it **cuneiform-common** and **libcuneiform0** if it doesn't then install them as well) 

**gdebi** (this should bring with it **gdebi-core** if it doesn't then install it as well)

2)log out and back in. (or reboot).

3)open your browser and go to....
[http://84.233.242.93/mirror/getdeb/ubuntu/pool/apps/y/yagf/](http://84.233.242.93/mirror/getdeb/ubuntu/pool/apps/y/yagf/)

click on the 3rd to bottom entry..
yagf_0.8.7-1~getdeb1_i386.deb	29-Aug-2011 

(if you are using a **64 bit machine and Ubuntu 64bit version** then click on the 5th to bottom 
yagf_0.8.7-1~getdeb1_amd64.deb  29-Aug-2011 )

 download the selected .deb file to your downloads folder.
 (Ffox or chromium should do this automatically).

4) Go to the downloads folder and find the deb file..
this should be called something like yagf_0.8.7-1~getdeb1_i386.deb

Right click on it and select 'open with gdebi package installer' from the right click menu.

gdebi will open and check for dependencies (post if any errors are noted at this stage) and if all is well  install YAGF.
 Once it has then close gdebi.

5)YAGF will now be available in your menus or search-able from the Unity dash.

6)open YAGF and go to Settings>ocr settings and select cuneiform. 
(Also check top right on the main window that the language it is using is English or change to your preferred)

7) all set to go ! 
 (you should install **fotoxx** as well for some extra processing options for scanned image files. See post #3 in this thread...[http://ubuntuforums.org/showthread.php?t=1714831](http://ubuntuforums.org/showthread.php?t=1714831))

I use Fotoxx as most of my inputs are from photographs of documents and not scans.It is more convenient for me to process them with an image viewer, nevertheless the contrast boosting using fotoxx is superb for improving contrast for both formats.

Another processing tool that may be useful for you is **scantailor** (from software centre or open a terminal and run ```
sudo apt-get install scantailor
```
Scantailor has deskewing function as well that may be easier to run if you are processing **clean, clear** scans.

all the best, Bob.

---

### Post by MarjaE on 2011-10-05
Okay I got it installed. But I'm not dealing with clean, clear scans - some of these are from the Internet Archive, although it nominally includes plain text downloads, the plain text versions are so corrupt as to be unusable and they are missing any maps, charts, etc.

---

### Post by robert shearer on 2011-10-05
Yeah, OCR is so dependent on having good input.
Give it garbage and get gibberish, so prepping the input can make a huge difference.

Two things are most important, having the text contrasted as strongly as possibly from the background and having the lines of text as horizontal as can be.

Dark grey text on a grey background won't work.

This is why I use **fotoxx** and it's  'Art effects > simulate drawing' tab to enhance the contrast and sharpness.
It converts your greyscale image to black and white and allows adjustment to get maximum contrast without losing clarity.
Adjust the 'threshold' slider for strongest black text without introducing speckles into the background and adjust the 'outlines' slider untill the background is white, no grey is present and the text outlines are clear.

 I use the 'Transform - rotate' option to get text lines as horizontal as possible. Fotoxx allows rotates of points of a degree in real time.

If images still show some localised aberrations (bowing,bending etc) I use the 'Warp area' option to drag areas and apply some 'un-warp'. Try it and you will see what I mean.

Try saving the results as different file types to see if that helps. I import jpegs, process them and save as tiffs then open those with YAGF.

Scantailor has a despeckle option in its final window.
Just toggle through the others and experiment with the despeckle options if your images won't come clean in fotoxx.

It is a matter of sorting a workflow for your images to maximise the ocr returns and may take some experimentation.
Once you have that sorted then you will know to apply it to all images like that in the future.

Practice and experiment, experiment, experiment. With ocr its not 'it works or it doesn't' rather its 'how well can you make it work'
Investing enough time sorting out a workflow will save hours of correcting duff output. 

I would suggest you despeckle first then move to fotoxx if you have poor backgrounds such as from photocopies.

It is worth trying several workflows and saving each result then running them through YAGF/cuneiform and comparing the results to find the one that works for you.

YAGF works best if you select several blocks of text , working down any columns then to the next column, untill the document is all covered **then** processing rather than selecting the whole document at once and processing.

Little things like that can improve accuracy a lot.(Your output will still be in one page but having YAGF work through it sequentially gives better recognition and layout.)

Hope that helps,
Cheers Bob.

---

### Post by MarjaE on 2011-10-07
Unfortunately, yagf can't open djvu or pdf files.

---

### Post by robert shearer on 2011-10-08
> **MarjaE said:**
> Unfortunately, yagf can't open djvu or pdf files.

And there are only about a zillion apps for converting from those to jpg,tiff,etc etc.
Google is your friend...:)

or try searching in your favourite browser using this as a preceding phrase...
```
site:ubuntuforums.org
```

as in ....
```
site:ubuntuforums.org convert pdf to tiff
```
for about 166 hits....:)

or...```
site:ubuntuforums.org convert pdf to jpeg
```
for 444 hits...:)

Hint... open your pdf with The Gimp and then save it as another format...jpg, tiff....whatever, then open the new file with YAGF.

Even easier if you just want your pdf output to text then follow this tutorial...
[http://ubuntup.blogspot.com/2010/08/pdf-to-text-pdf-to-jpg-png-etc.html](http://ubuntup.blogspot.com/2010/08/pdf-to-text-pdf-to-jpg-png-etc.html)
(just note that the first use of the command should be..
 ```
pdftotext filename.pdf filename.txt
```
somehow the 'e' in pdftotext was omitted in the tutorial)

Doing some research is not that hard and will be more useful to you in the long run than posting 'can't' every time something doesn't work the way you think it should. :)

---

### Post by MarjaE on 2011-10-08
Well the problem is that tiffs, jpgs, etc. come out as separate pages instead of whole documents. I'm not sure document viewer can read the whole series at once - my experience is that it insists on only opening one page in each viewer with those formats - and there's no point indexing/searching individual pages w/o the whole.

---

### Post by MarjaE on 2011-10-08
Also, I had been struggling with the problem far days before going here. I had finished, the hard way, the work this would have helped with by the time I got any responses. So if I seem less-than-appreciative, it's not your fault, and if I seem too eager to ask about these problems, I am learning to ask sooner, not later.

---

### Post by MarjaE on 2011-12-07
Well, once again I'm looking for good easy-to-use ocr software that can read djvus and pdfs, without crashing.

---

