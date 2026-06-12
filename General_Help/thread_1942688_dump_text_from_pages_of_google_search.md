---
title: "dump text from pages of google search"
date: 2012-03-18
forum: General Help
---

### Post by edfromballarat on 2012-03-18
hi all,

i am studying for a medical exam and I frequently need to consult multiple pages to find obscure facts.  I am looking for a way to do a google search, go to each of the top 5-10 sites, dump the text from these sites to a file, and hi-light the search term within the dumped text.

I figure you can dump text directly from a lynx search, but I can't work out how to get lynx to go into each of the google links without doing it manually.

Ideally, I would like to write a script that would prompt for the search terms and then the dump file name and then create the file.

Any ideas? Thanks

---

### Post by dragonfly41 on 2012-03-18
If you're researching a corpus of medical references I would recommend installing 

TextSTAT
[http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

You need to install python-tk .. through Synaptic Package Manager

Then, run the command "python TextSTAT.pyw" in the TEXTStat folder.

I just run the command ..

**cd /home/myusername/Applications/TextSTAT/    &&  python TextSTAT.pyw**

You can then add either web sites or local files to your corpus to search for key phrases.


also try ..

AntConc3.2 and AntWord Profiler
[http://www.antlab.sci.waseda.ac.jp/software.html](http://www.antlab.sci.waseda.ac.jp/software.html)

...

another tip is to install zotero add-on for firefox

this is a citation manager

---

### Post by edfromballarat on 2012-03-18
thanks, i'll give those a try.

still looking for a scripted command line option, if somebody is willing to help out

---

### Post by HiImTye on 2012-03-18
You can use wget to do this, but you need to specify a user agent
```
wget -U “Firefox/3.0.15&#8243; http://www.google.com/search?q=wget+google+query+to+file -O file.html
```

otherwise you get a 403/forbidden

[http://isaksen.biz/blog/?p=470](http://isaksen.biz/blog/?p=470)

---

### Post by HiImTye on 2012-03-18
use the --mirror option to follow links such as:
```
 wget -U &#8220;Firefox/3.0.15&#8243; --mirror http://www.google.com/search?q=wget+google+query+to+file -O file.html
```it actually seems that using the -O option prevents it from getting multiple pages, so do it without it, like:
```
 wget -U &#8220;Firefox/3.0.15&#8243; --mirror http://www.google.com/search?q=wget+google+query+to+file
```
after 300 or so results you will start getting service unavailable

---

### Post by edfromballarat on 2012-03-18
thanks, looks very promising.
1.  At the moment it just seems to be getting the google search page rather than opening the links and saving these pages
2. is there a way to limit or define the number of responses?  at the moment the command just keeps adding pages until i kill the process.
3. is there a way to dump to a text file rather than html? I guess I could just pipe the output to an html to text converter

---

