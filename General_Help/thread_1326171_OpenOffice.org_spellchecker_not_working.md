---
title: "OpenOffice.org spellchecker not working"
date: 2009-11-14
forum: General Help
---

### Post by blazemore on 2009-11-14
In OpenOffice Writer (The version that comes with Karmic) the spell checker doesn't work. The language is set to English (UK). No spelling mistakes are highlighted, and when you open the manual spellchecker it says no errors are found.
Spellchecking is turned on.

---

### Post by Hagar Delest on 2009-11-14
See [[Troubleshooting] Spell check in OOo 3.x](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=16512) Make sure there is blue checkmark in front of the language.

Have you installed the corresponding OOo package in Synaptic? As the Ubuntu version of OOo is bundled in a lot of packages, it may have been split from main build.

---

### Post by blazemore on 2009-11-14
Which OOo package is this?

---

### Post by kjohri on 2009-11-14
Have you selected the language? 

Try Tools -> Language -> For Selection. Click on the language you wish to choose.

---

### Post by Hagar Delest on 2009-11-14
> **blazemore said:**
> Which OOo package is this?
Hmm, I checked in Synaptic and there doesn't seem to be any package for en-UK so I guess it's in the default en-US one also. So no idea. Do you see the dictionary in the extension manager?

@ kjohri: beware: first this is a direct formatting and second, that checkmark doesn't mean that the dictionary is installed.

---

### Post by Michael577 on 2009-12-08
Well this is weired, I'm having the same problem too untill I loaded up a file that I saved in the windows ver. of OpenOffice and the spell checker worked! I'm no Ubuntu Expert but here's the file that has the working spell check, I hope this helps. ;)

---

### Post by troll1602 on 2009-12-15
I had the same problem and I did the following to fix it: Right-click on an open document, go to "Edit Paragraph Style...". And then under the "Font" tab, you can choose English as the language.

---

### Post by Michael577 on 2010-01-19
Hey guy's me again ;).  I just downloaded Ubuntu 10.04 and started the live cd on my "Dummy" computer and I opened open office and guess what? The spell checker WORKS :KS. So it seems like Canonical and sun systems solved this problem so hope some people can survive till April:lolflag:. Oh and [troll1602]("http://ubuntuforums.org/member.php?u=608794") your right! I did what you said and it now works on my 9.10 computer... I think I'll make a quick video about this. See ya!

---

### Post by iknik on 2010-03-03
Hi everyone,

I'm new to Ubuntu (and loving it). A web search led me to this topic because I'm having the exact same problem as blazemore: apparently, I don't have the English (UK) dictionary installed in OpenOffice (it's OOo 3.1, as included by default in Ubuntu 9.10). When I set the language to English (UK) (there's no blue checkmark to the left of it) the spellcheck says that no errors were found, even if there clearly are errors in the text. When I go to Tools -> Language -> More Dictionaries Online I go to a web page that offers dozens of diciotnaries... but not English (UK). None of the solutions offered in this thread work for me. Can anyone help me?

---

### Post by tractor on 2010-06-12
Hi,

I'm having the exact same problem. If you are installing from the software center individual packages such as writer, spreadsheet, etc, or if you install the entire open office package at one time, there isn't any auto check of the spelling, and if you run the spell checker with obviously misspelled words, it doesn't find any!!!!!!!!! 

I also tried adding several uninstalled language/dictionary packages from Synaptic. That didn't help either. English is selected as the language.

Maybe the only solution is to try to install the open office version directly from Opneoffice.org.

---

### Post by tractor on 2010-06-12
While it is best to download from the repositories, this spell checker issue is a bug. If you follow the instructions here:
[http://ubuntuforums.org/showthread.php?p=9410791](http://ubuntuforums.org/showthread.php?p=9410791)
you can download Opneoffice 3.2.1 and install it and the spell checker works perfectly!!!!!!!!!

---

