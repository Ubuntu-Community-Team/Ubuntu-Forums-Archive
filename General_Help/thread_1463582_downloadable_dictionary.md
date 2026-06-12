---
title: "downloadable dictionary"
date: 2010-04-27
forum: General Help
---

### Post by tonythemushroom on 2010-04-27
[SIZE=2][B]hello all and good moring to you. im just wondering if anyone knows of a good english  dictionary i could download on to ubuntu to use with open office. . thank you for your time and have a good day :P:P

tony
[/B][/SIZE]

---

### Post by colorlessprism on 2010-04-27
**IMPORTANT NOTE:  From OpenOffice.org 3.0 on the dictionary wizard is no longer available -- Dictionaries are now available via [the extensions repository]("http://extensions.services.openoffice.org/dictionary")**. 

See [Extension Dictionaries]("http://wiki.services.openoffice.org/wiki/Extension_Dictionaries") for how to create dictionary extensions. As an end-user this page is now only useful for those using OpenOffice.org < 3.0, though it still has a role for aiding Linux distribution packagers in collecting what un-bundled linguistic extensions are available. 
To install a new dictionary in Vanilla OpenOffice.org 2.x, call "File -> Wizards -> Install new dictionaries" in OpenOffice.org. Then exit and re-start OpenOffice.org, including the Quickstarter (if used). Most of the files on this page are available for installation via the wizard. If not, download the Pack file, and use the "off-line language installation" option of [DicOOo wizard]("http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw").

---

### Post by Linuxforall on 2010-04-27
Stardict is in then repos and supports multiple of dictionaries as well as pronounciation.

---

### Post by tonythemushroom on 2010-04-27
> **colorlessprism said:**
> **IMPORTANT NOTE:  From OpenOffice.org 3.0 on the dictionary wizard is no longer available -- Dictionaries are now available via [the extensions repository]("http://extensions.services.openoffice.org/dictionary")**. 

See [Extension Dictionaries]("http://wiki.services.openoffice.org/wiki/Extension_Dictionaries") for how to create dictionary extensions. As an end-user this page is now only useful for those using OpenOffice.org < 3.0, though it still has a role for aiding Linux distribution packagers in collecting what un-bundled linguistic extensions are available. 
To install a new dictionary in Vanilla OpenOffice.org 2.x, call "File -> Wizards -> Install new dictionaries" in OpenOffice.org. Then exit and re-start OpenOffice.org, including the Quickstarter (if used). Most of the files on this page are available for installation via the wizard. If not, download the Pack file, and use the "off-line language installation" option of [DicOOo wizard]("http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw").


thank you :P

---

### Post by tonythemushroom on 2010-04-27
> **Linuxforall said:**
> Stardict is in then repos and supports multiple of dictionaries as well as pronounciation.


thank you :P

---

### Post by brallan on 2010-04-27
Because you are asking for a dictionary for open office, its not completely clear to me whether you want a spellchecker or a dictionary. Perhaps you asking for a dictionary that integrates into all open applications, not just open office?

if you are looking for a spellchecker, make sure you have the language support for english installed. Open office will already include an english spellchecker if you do so.

if you want a dictionary that will work on oo as well as firefox and other applications, try artha or qstardict.

the best english dictionary i have ever seen in paper OR offline is wordnet, to get it , go to the software center and install artha. (It can be found in the repos - it is the equivalent of WordWeb Pro in window$.) During install, artha will download the wordnet archive automatically. When you want to look up a word, just click CTRL - ALT - W with the word selected, and it will come up.

Another good option is to install qstardict and install an english language dictionary from the xdxf website:

[http://xdxf.revdanica.com/down/](http://xdxf.revdanica.com/down/)

the collaborative one looks nice:

[http://sourceforge.net/projects/xdxf/files/dicts-stardict-form-xdxf/002a/stardict-comn_dictd04_gcide-2.4.2.tar.bz2/download](http://sourceforge.net/projects/xdxf/files/dicts-stardict-form-xdxf/002a/stardict-comn_dictd04_gcide-2.4.2.tar.bz2/download)

Download the stardict file, unzip it and put it in the proper folder for stardict, which should be  /usr/share/stardict/dic

if im not mistaken, you should be root to do so.

But I do not have much experience with stardict, since artha has served my needs so well.

best of luck!

---

### Post by tonythemushroom on 2010-04-28
> **brallan said:**
> Because you are asking for a dictionary for open office, its not completely clear to me whether you want a spellchecker or a dictionary. Perhaps you asking for a dictionary that integrates into all open applications, not just open office?

if you are looking for a spellchecker, make sure you have the language support for english installed. Open office will already include an english spellchecker if you do so.

if you want a dictionary that will work on oo as well as firefox and other applications, try artha or qstardict.

the best english dictionary i have ever seen in paper OR offline is wordnet, to get it , go to the software center and install artha. (It can be found in the repos - it is the equivalent of WordWeb Pro in window$.) During install, artha will download the wordnet archive automatically. When you want to look up a word, just click CTRL - ALT - W with the word selected, and it will come up.

Another good option is to install qstardict and install an english language dictionary from the xdxf website:

[http://xdxf.revdanica.com/down/](http://xdxf.revdanica.com/down/)

the collaborative one looks nice:

[http://sourceforge.net/projects/xdxf/files/dicts-stardict-form-xdxf/002a/stardict-comn_dictd04_gcide-2.4.2.tar.bz2/download](http://sourceforge.net/projects/xdxf/files/dicts-stardict-form-xdxf/002a/stardict-comn_dictd04_gcide-2.4.2.tar.bz2/download)

Download the stardict file, unzip it and put it in the proper folder for stardict, which should be  /usr/share/stardict/dic

if im not mistaken, you should be root to do so.

But I do not have much experience with stardict, since artha has served my needs so well.

best of luck!

its a dictonary im after , im going for wordnet it do's seem to do everything it says on tin cheers:popcorn:

---

