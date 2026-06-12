---
title: "No thesaurus and hyphenation in LibreOffice"
date: 2011-07-10
forum: General Help
---

### Post by michopop on 2011-07-10
I use Ubuntu 10.04 and freshly installed LiberOffice. The issue is the following:
The thesaurus and hyphenation packages are missing from the LibreOffice packages: libreoffice-thesaurus-* and libreoffice-hyphenation-*. Do you have an idea how can I install them?

---

### Post by Toz on 2011-07-10
Well, I got the thesaurus installed and working. It was a bit convoluted for me. I live in Canada and the language specified in LibreOffice is "English (Canada)" (Tools->Options->Language Settings->Languages).

The thesaurus package is called mythes and you have to install the appropriate one to your language as per the setting above. Since **mythes-en-CA** doesn't exist, I have to install **mythes-en-US** then rename the files in /usr/share/mythes by changing US to CA, restarted libreoffice and viola - thesaurus.

If you go to Tools->Options->Language Settings->Writing Aids and click on the first "Edit" button, you will see the different language aid groupings (Spelling, Grammar, Hyphenation, Thesaurus) and the associated modules that are installed. I also added the Grammar module by clicking on the "Get more dictionaries online" and installing "LanguageTools". 

Now I'm off to find out about hyphenation.

---

### Post by Toz on 2011-07-10
Okay - I got hyphenation installed using a similar process. I installed **hyphen-en-US** then renamed the file in /usr/share/hyphen to its CA counterpart.

---

### Post by michopop on 2011-07-11
Thanks for the reply, Toz, but unfortunately it doesn't help me a lot. I use multiple Languages - English, German, Macedonian, Bulgarian, Serbian - and I need all the thesauri and hyphenations in order to make LibreOffice work properly for me. This worked smoothly for OOO, but here simply the packages in the Ubuntu repositories are missing! On the other hand, in Synaptic Package Manager, in the info field of the different language packages, the following message is written: 

Spelling dictionaries, hyphenation patterns, thesauri and help are not
included in this package. There are some available in separate packages
(myspell-*, libreoffice-hyphenation-*, libreoffice-thesaurus-*,
libreoffice-help-*)

This means that LibreOffice has created these packages, but they are for some reason not in the Ubuntu repositories!

PS. In January 2011, this problem was reported as a bug - and that is the last time it is mentioned! There are six months since then and I cannot believe it is not yet solved, or that any alternative solution has been found!

---

### Post by michopop on 2011-07-12
I found a sollution: 

1. First install "language-support-writing-*"
2. Then install "openofficeo.org-thesaurus-*"

And it works! 

PS. Before I have tried to install the ooo thesaurus, but it didn't function withot the first step.

---

### Post by Hagar Delest on 2011-07-12
Or install the vanilla version from the LibO site. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) the same applies to LibO.

Then check that one: [[Troubleshooting] Spell check in OOo 3.x](http://user.services.openoffice.org/en/forum/viewtopic.php?t=16512)

---

### Post by Fourcultures on 2011-10-20
#5 worked for me. Thanks!

---

### Post by frytek on 2012-05-19
Another method that worked for me:

Go to 
[http://extensions.libreoffice.org/extension-center?getCategories=Dictionary](http://extensions.libreoffice.org/extension-center?getCategories=Dictionary)

I downloaded spelling + thesaurus as an oxt file. It's an extension file to be installed via Tools / Extension manager - and it worked.

---

