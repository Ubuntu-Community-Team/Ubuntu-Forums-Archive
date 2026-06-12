---
title: "Did I completly install Tesseract  3?"
date: 2011-10-21
forum: General Help
---

### Post by Advice Pro on 2011-10-21
I'm installing Tesseract 3 using the following code:

```
sudo apt-get install autoconf automake libtool
sudo apt-get install libpng12-dev
sudo apt-get install libjpeg62-dev
sudo apt-get install libtiff4-dev
sudo apt-get install zlib1g-dev

wget [http://www.leptonica.org/source/leptonlib-1.67.tar.gz](http://www.leptonica.org/source/leptonlib-1.67.tar.gz)
tar -zxvf leptonlib-1.67.tar.gz
cd leptonlib-1.67
./configure
make
sudo checkinstall (follow the prompts and type "y" to create documentation directory. Enter a brief description then press enter twice)
sudo ldconfig

wget [http://tesseract-ocr.googlecode.com/files/tesseract-3.00.tar.gz](http://tesseract-ocr.googlecode.com/files/tesseract-3.00.tar.gz)
tar -zxvf tesseract-3.00.tar.gz
cd tesseract-3.00
./runautoconf
./configure
make
sudo checkinstall (follow the prompts and type "y" to create documentation directory. Enter a brief description then press enter twice)
sudo ldconfig
```

However I couldn't run these at either instance:

```
make
sudo checkinstall
sudo ldconfig
```

I've not tested Tesseract yet, but want to know if you think the software should be OK.

---

### Post by ajgreeny on 2011-10-21
There is a ppa for tersseract 3 which allows you to install it with apt-get or synaptic, the latter of which is how I install most applications.  Do a search to find the exact address for it as it seems to vary depending on your current ubuntu version.

I use it in Lucid and it is many times better than the normal repository version, producing a much better and accurate text output.
```
deb http://ppa.launchpad.net/alex-p/notesalexp/ubuntu lucid main
``` is the ppa I use, so search with ```
ppa.launchpad.net/alex-p/notesalexp
``` as your search term and you may find just what you need.

---

### Post by Paddy Landau on 2011-11-11
@ajgreeny: This PPA is incredibly useful, and it has helped me. Thank you. How did you learn about it?

---

### Post by Advice Pro on 2011-11-19
Sorry, I don't know anything about PPA's:

[LIST=1]
[*]Where do I get them?
[*]How do I install them?
[*]Would I have any trouble like a wrote about in my original post?
[/LIST]

My Ubuntu version is 10.10.

---

### Post by Paddy Landau on 2011-11-19
A PPA is a repository where programs are kept. When you "add a PPA", in fact you are not adding a PPA but rather adding the name of the PPA to the list held by your package manager.

When Update Manager checks for updates, it checks all the PPAs in the list, and lets you update anything that has changed. Synaptic Package Manager and Ubuntu Software Centre also refer to the PPAs.

Ubuntu comes by default with a few PPAs (otherwise you would have no software or updates available). You can manually add new PPAs to the list.

To add this PPA:

[LIST=1]
[*]Open *Software Sources* (you can do this directly, or from either Synaptic Manager or Ubuntu Software Centre) > *Other Software* > *Add*.
[*]In the line, type (or, better, copy and paste):```
 deb [http://ppa.launchpad.net/alex-p/notesalexp/ubuntu](http://ppa.launchpad.net/alex-p/notesalexp/ubuntu) maverick main
```
[*]Press *Add Source*.
[*]Press *Close*.
[*]You will receive a warning about reloading. Press *Reload*.
[/LIST]
Finally, go to either Synaptic Package Manager or Ubuntu Software Centre (whichever you feel more comfortable with), uninstall the old Tesseract, and install the new one. Thereafter, Update Manager will take care of updates in the same way as it takes care of all your other updates.

EDIT: You won't get the trouble you mentioned in the last post, because your package manager handles everything for you when you use PPAs.

---

### Post by Advice Pro on 2011-12-20
Would I need to separately install:

leptonica
autoconf automake libtool
libpng12-dev
libjpeg62-dev
libtiff4-dev
zlib1g-dev

---

### Post by Paddy Landau on 2011-12-21
The Package Manager is supposed to handle all dependencies for you, so no, you shouldn't have to install those manually.

As far as I recall, I simply followed the [post=11471110]instructions that I gave you[/post] to install it successfully on my machine.

---

### Post by Advice Pro on 2012-01-16
How would I convert TIFF images to text?

---

### Post by Paddy Landau on 2012-01-16
> **Advice Pro said:**
> How would I convert TIFF images to text?
Open a terminal, go to where your TIFF file is, and enter the following. Tesseract will automatically add ".txt" to the name of the output file.
```
 tesseract *inputfile*.tiff *outputfile*
```I do not know of a GUI to do this; you need to do it from a terminal. If anyone knows of a GUI, please let us know.

---

### Post by Advice Pro on 2012-01-16
I did a search on [Google](https://www.google.com/search?q="linux"+tesseract+graphical+user+interface&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a) and it rendered many results starting with a Wikipedia article section with a number of tess GUI's!

would you know how to convert many TIFF files into one text file?

If not, then to use ImageMagick to convert PNG's or JPEG's into a TIFF file?

---

### Post by Paddy Landau on 2012-01-17
> **Advice Pro said:**
> I did a search on [Google]("https://www.google.com/search?q=%22linux%22+tesseract+graphical+user+interface&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") and it rendered many results starting with a Wikipedia article section with a number of tess GUI's!
Cool. Last time I looked (a long time ago), I found nothing that worked properly.

> **Advice Pro said:**
>  would you know how to convert many TIFF files into one text file?
To the best of my knowledge, only with a script. See below...

> **Advice Pro said:**
> If not, then to use ImageMagick to convert PNG's or JPEG's into a TIFF file?
It's not necessary to use a TIFF file. The latest Tesseract will take PNG and JPG as input. I don't know offhand how to concatenate image files.

I wrote a script some time ago to take multiple input images and concatenate them into a single output file. If you would like a copy of the script, let me know and I'll post it here.

---

### Post by Advice Pro on 2012-01-17
> **Paddy Landau said:**
> If you would like a copy of the script, let me know and I'll post it here.

Yes please.

---

### Post by EgoGratis on 2012-01-17
This thread helped me:

[http://ubuntuforums.org/showthread.php?t=1647350](http://ubuntuforums.org/showthread.php?t=1647350)

---

### Post by Paddy Landau on 2012-01-17
> **Advice Pro said:**
> Yes please.
Script attached.

Save it somewhere in your path, for example in /usr/local/sbin. Ensure that the execute flag is set.

Then open a terminal and enter:
```
ocr --help
```To run, change directory to where your pictures are; for example
```
 cd ~/Pictures/scanned
ocr page*.jpg interpreted.txt
```Let me know if you hit any problems.

**EDIT:** The attachment is compressed because of Ubuntu forum restrictions. Uncompress it first.

---

