---
title: "Make folders Windows compatible"
date: 2010-09-19
forum: General Help
---

### Post by realizee on 2010-09-19
Hi!

I have an folder with different websites saved on it but when I'm about to extract it to an .zip and unextract it on Windows it says something like wrong name.

What to do?
Thanks

EDIT: Would it work if I installed VMware Workstation on my PC?

---

### Post by Vaphell on 2010-09-19
does this zip file get some unusual name with non-standard characters? and what about website files that are inside?

btw, it's 'compress to zip' and 'extract from zip' :-)

---

### Post by realizee on 2010-09-19
> **Vaphell said:**
> does this zip file get some unusual name with non-standard characters? and what about website files that are inside?

btw, it's 'compress to zip' and 'extract from zip' :-)

Yes, the folders get names that are not supported by Windows. I would like to change them in "one click" if that's possible, if you get what i mean?

ok. thanks :)

---

### Post by Vaphell on 2010-09-19
what language are we talking about? ubuntu uses utf8 encoding, windows uses variety of encodings depending on the language ([http://en.wikipedia.org/wiki/Windows_code_page](http://en.wikipedia.org/wiki/Windows_code_page)).

[http://ubuntuforums.org/showthread.php?t=1487076](http://ubuntuforums.org/showthread.php?t=1487076)
poster had the opposite problem - windows encoded files didn't work in ubuntu.

fix should be the same, with the difference that 'from' and 'to' encodings will be switched. Get to the directory with those webpages, run the convmv command with proper -f/-t encodings, compress to zip, open on windows

---

