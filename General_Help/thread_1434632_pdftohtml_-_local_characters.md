---
title: "pdftohtml - local characters"
date: 2010-03-20
forum: General Help
---

### Post by LuciusMare on 2010-03-20
Hi, I wanted to convert a few .pdf files to .epub. I use ebook-convert (from calibre), which converts it to html first, with pdftohtml. However, pdftohtml doesn't exactly work as expected - some of local characters (language-specific) are there, but some of them are completely gone. There is just blank space instead.I googled, and found i should do it manually, with parameter "-enc Latin" . Then pdftohtml says: ```
Error: Couldn't find unicodeMap file for the 'Latin2' encoding
```I googled more, but found nothing useful. Just that I should install package  {They do not allow me to post links, so google for "xpdf latin2" and the first link} - i did so, but it keeps throwing the same error. Some relevant files follow:"
/etc/xpdf/xpdfrc-latin2:

```
#----- begin Latin2 support package (2002-oct-22)
unicodeMap Latin2 /usr/share/xpdf/latin2/Latin2.unicodeMap
#----- end Latin2 support package
```/etc/xpdf/xpdfrc
```
#========================================================================                                                                                                             
#                                                                                                                                                                                     
# System-wide xpdfrc file                                                                                                                                                             
#                                                                                                                                                                                     
# The Xpdf tools look for a config file in two places:                                                                                                                                
# 1. ~/.xpdfrc                                                                                                                                                                        
# 2. /etc/xpdf/xpdfrc                                                                                                                                                                 
#                                                                                                                                                                                     
# Note that if ~/.xpdfrc exists, Xpdf will NOT read the system                                                                                                                        
# configuration file /etc/xpdf/xpdfrc. You may wish to include it                                                                                                                     
# from your ~/.xpdfrc using:                                                                                                                                                          
#    include /etc/xpdf/xpdfrc                                                                                                                                                         
# and then add additional settings.                                                                                                                                                   
#                                                                                                                                                                                     
# For complete details on config file syntax and available options,                                                                                                                   
# please see the xpdfrc(5) man page.                                                                                                                                                  
#                                                                                                                                                                                     
#                                                                                                                                                         
#                                                                                                                                                                                     
#========================================================================                                                                                                             

#----- display fonts

# These map the Base-14 fonts to the Type 1 fonts that ship with
# ghostscript (gsfonts package).                                

displayFontT1 Times-Roman               /usr/share/fonts/type1/gsfonts/n021003l.pfb
displayFontT1 Times-Italic              /usr/share/fonts/type1/gsfonts/n021023l.pfb
displayFontT1 Times-Bold                /usr/share/fonts/type1/gsfonts/n021004l.pfb
displayFontT1 Times-BoldItalic          /usr/share/fonts/type1/gsfonts/n021024l.pfb
displayFontT1 Helvetica                 /usr/share/fonts/type1/gsfonts/n019003l.pfb
displayFontT1 Helvetica-Oblique         /usr/share/fonts/type1/gsfonts/n019023l.pfb
displayFontT1 Helvetica-Bold            /usr/share/fonts/type1/gsfonts/n019004l.pfb
displayFontT1 Helvetica-BoldOblique     /usr/share/fonts/type1/gsfonts/n019024l.pfb
displayFontT1 Courier                   /usr/share/fonts/type1/gsfonts/n022003l.pfb
displayFontT1 Courier-Oblique           /usr/share/fonts/type1/gsfonts/n022023l.pfb
displayFontT1 Courier-Bold              /usr/share/fonts/type1/gsfonts/n022004l.pfb
displayFontT1 Courier-BoldOblique       /usr/share/fonts/type1/gsfonts/n022024l.pfb
displayFontT1 Symbol                    /usr/share/fonts/type1/gsfonts/s050000l.pfb
displayFontT1 ZapfDingbats              /usr/share/fonts/type1/gsfonts/d050000l.pfb

# If you need to display PDF files that refer to non-embedded fonts,
# you should add one or more fontDir options to point to the        
# directories containing the font files.  Xpdf will only look at .pfa,
# .pfb, and .ttf files in those directories (other files will simply  
# be ignored).                                                        

#fontDir                /usr/local/fonts/bakoma

#----- PostScript output control

# Set the default PostScript file or command.

psFile                  "|lpr"

# Set the default PostScript paper size -- this can be letter, legal,
# A4, or A3.  You can also specify a paper size as width and height  
# (in points). Xpdf uses the paper size in /etc/papersize by default.

#psPaperSize            letter

#----- text output control

# Choose a text encoding for copy-and-paste and for pdftotext output.
# The Latin1, ASCII7, and UTF-8 encodings are built into Xpdf.  Other
# encodings are available in the language support packages.          

#textEncoding           UTF-8

# Choose the end-of-line convention for multi-line copy-and-past and
# for pdftotext output.  The available options are unix, mac, and dos.

#textEOL                unix

#----- misc settings

# Enable Type 1 font rasterizing with t1lib. Default "yes".

#enableT1lib            no

# Enable TrueType and Type 1 font rasterizing with FreeType. Default "yes".

#enableFreeType         no

# Enable anti-aliasing of fonts. Default "yes".

#antialias              no

# Set the command used to run a web browser when a URL hyperlink is
# clicked.

urlCommand      "sensible-browser '%s'"

# Include the language configuration file list generated by update-xpdfrc
include /etc/xpdf/includes
```/etc/xpdf/includes
```
# This file was automatically generated by /usr/sbin/update-xpdfrc.
# Instead, add or remove files in /etc/xpdf/ then run
# /usr/sbin/update-xpdfrc to regenerate this file.

include /etc/xpdf/xpdfrc-arabic
include /etc/xpdf/xpdfrc-turkish
include /etc/xpdf/xpdfrc-cyrillic
include /etc/xpdf/xpdfrc-greek
include /etc/xpdf/xpdfrc-hebrew
include /etc/xpdf/xpdfrc-latin2
include /etc/xpdf/xpdfrc-thai
``````
0ebb395634bd1e23113dcf69f19930f7  /usr/share/xpdf/latin2/Latin2.unicodeMap
```edit:The README said that the "add-to-xpdfrc" should be added to the system-wide configuration file, which is /etc/xpdf/xpdfrc, (instead of what was said in README), but even after adding it there, it does not works, still the same error.

---

### Post by luigi_mb on 2010-03-20
> **LuciusMare said:**
> Hi, I wanted to convert a few .pdf files to .epub. I use ebook-convert (from calibre), which converts it to html first, with pdftohtml. However, pdftohtml doesn't exactly work as expected - some of local characters (language-specific) are there, but some of them are completely gone. There is just blank space instead.I googled, and found i should do it manually, with parameter "-enc Latin" . Then pdftohtml says: ```
Error: Couldn't find unicodeMap file for the 'Latin2' encoding
```I googled more, but found nothing useful. Just that I should install package  {They do not allow me to post links, so google for "xpdf latin2" and the first link} - i did so, but it keeps throwing the same error. Some relevant files follow:"
/etc/xpdf/xpdfrc-latin2:

```
#----- begin Latin2 support package (2002-oct-22)
unicodeMap Latin2 /usr/share/xpdf/latin2/Latin2.unicodeMap
#----- end Latin2 support package
```/etc/xpdf/xpdfrc
[CODE]

I think there may be some conflict between xpdf/xpdf-utils and poppler-utils.  pdftohtml may be part of poppler, not of xpdf. It may be that pdftohtml does not read .xpdfrc .

Incidentally, as far as I know, the Latin2 support in xpdf is installed with xpdf.

/luigi

---

### Post by luigi_mb on 2010-03-21
Just to clarify. 

1) If .xpdfrc exists in the home folder, it will take precedence over /etc/xpdf/.xpdfrc .
2) Both pdftohtml (Poppler) and pdftotext etc. (xpdf) do read ~/.xpdfrc, and can use the "-enc Latin2" (**not** "-enc Latin") switch, provided the following line is appended to ~/.xpdfrc

```

unicodeMap      Latin2  /usr/share/xpdf/latin2/Latin2.unicodeMap

```

That's the setup I use, and it works--at least in Ubuntu v9.04. 

/luigi

---

### Post by LuciusMare on 2010-03-21
Huh. Something seems to be seriously wrong with my system...
```
lucius@blackrock:~$ cat .xpdfrc
unicodeMap      Latin2  /usr/share/xpdf/latin2/Latin2.unicodeMap
lucius@blackrock:~$ ls /usr/share/xpdf/latin2/Latin2.unicodeMap 
/usr/share/xpdf/latin2/Latin2.unicodeMap                              
lucius@blackrock:~$ pdftotext -enc Latin2 sample.pdf 
Error: Couldn't find unicodeMap file for the 'Latin2' encoding
Error: Couldn't get text encoding                             
lucius@blackrock:~$ cat /etc/xpdf/xpdfrc-*                                                                                                               
#----- begin Arabic support package (2003-feb-16)                                                                                                        
unicodeMap      ISO-8859-6      /usr/share/xpdf/arabic/ISO-8859-6.unicodeMap                                                                             
#----- end Arabic support package                                                                                                                        
#----- begin Cyrillic support package (2003-jun-28)                                                                                                      
nameToUnicode                   /usr/share/xpdf/cyrillic/Bulgarian.nameToUnicode                                                                         
unicodeMap      KOI8-R          /usr/share/xpdf/cyrillic/KOI8-R.unicodeMap                                                                               
#----- end Cyrillic support package                                                                                                                      
#----- begin Greek support package (2002-feb-13)                                                                                                         
nameToUnicode                   /usr/share/xpdf/greek/Greek.nameToUnicode                                                                                
unicodeMap      ISO-8859-7      /usr/share/xpdf/greek/ISO-8859-7.unicodeMap                                                                              
#----- end Greek support package                                                                                                                         
#----- begin Hebrew support package (2003-feb-16)                                                                                                        
unicodeMap      ISO-8859-8      /usr/share/xpdf/hebrew/ISO-8859-8.unicodeMap                                                                             
unicodeMap      Windows-1255    /usr/share/xpdf/hebrew/Windows-1255.unicodeMap                                                                           
#----- end Hebrew support package                                                                                                                        
#----- begin Latin2 support package (2002-oct-22)                                                                                                        
unicodeMap Latin2 /usr/share/xpdf/latin2/Latin2.unicodeMap                                                                                               
#----- end Latin2 support package                                                                                                                        
#----- begin Thai support package (2002-jan-16)
nameToUnicode                   /usr/share/xpdf/thai/Thai.nameToUnicode
unicodeMap      TIS-620         /usr/share/xpdf/thai/TIS-620.unicodeMap
#----- end Thai support package
#----- begin Turkish support package (2002-apr-10)
unicodeMap      ISO-8859-9      /usr/share/xpdf/turkish/ISO-8859-9.unicodeMap
#----- end Turkish support package
lucius@blackrock:~$ pdftotext -enc ISO-8859-9 sample.pdf
Error: Couldn't find unicodeMap file for the 'ISO-8859-9' encoding
Error: Couldn't get text encoding
lucius@blackrock:~$ pdftotext -enc TIS-620 sample.pdf
Error: Couldn't find unicodeMap file for the 'TIS-620' encoding
Error: Couldn't get text encoding
```And so on, no matter what encoding i try...

---

