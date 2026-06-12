---
title: "extracting text?"
date: 2009-12-02
forum: General Help
---

### Post by othiena on 2009-12-02
I have several .jpg images with text in them and I was wondering if their is any way to get the text out of them without having to retype it?

---

### Post by mikewhatever on 2009-12-02
There might be a way with OCR recognition software.
[http://www.free-ocr.com/](http://www.free-ocr.com/)

---

### Post by othiena on 2009-12-03
Thanks they did an ok job on the first page but it is going to take a looooooooooog time when I have over 5000 images.

---

### Post by jegerjensen on 2009-12-03
There are a handful of OCR packages in the repos.  Don't know how good they are, though...

```
[...]$ dpkg -l '*ocr*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Navn                                 Versjon                              Beskrivelse
+++-====================================-====================================-========================================================================================
pn  democracyplayer                      <ingen>                              (ingen beskrivelse tilgjengelig)
ii  gocr                                 0.41-1ubuntu2                        A command line OCR
ii  gocr-doc                             0.41-1ubuntu2                        gocr documentation
ii  ocrad                                0.17-2                               Optical Character Recognition program
ii  tesseract-ocr                        2.01-3                               Command line OCR tool
un  tesseract-ocr-data                   <ingen>                              (ingen beskrivelse tilgjengelig)
ii  tesseract-ocr-deu                    2.00-1                               tesseract-ocr language files for German text
ii  tesseract-ocr-eng                    2.00-1                               tesseract-ocr language files for English text
un  tesseract-ocr-language               <ingen>                              (ingen beskrivelse tilgjengelig)

```

---

### Post by othiena on 2009-12-03
Thanks! Going to try them when I have More time.

---

