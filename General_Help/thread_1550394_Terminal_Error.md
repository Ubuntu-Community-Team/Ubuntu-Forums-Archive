---
title: "Terminal Error?"
date: 2010-08-11
forum: General Help
---

### Post by seanarickymurphy on 2010-08-11
Upon Opening synaptic, this error occurs.
"An Error Occurred."
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
---
Terminal -
sudo dpkg --configure -a
[sudo] password for sean: 
dpkg: parse error, in file '/var/lib/dpkg/updates/0081' near line 0:
 field name `' must be followed by colon
---
As of opening /var/lib/dpkg/updates/0081
"Could not open the file /var/lib/dpkg/updates/0081."
gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.
Character Encoding  - Automatically Detected

As of other character encodings there are:
-Current Local (UTF -8)
-Western (ISO-8859-15)
Add or Remove...
.
Help would be granted? Please. :(

---

### Post by bergfly on 2010-08-11
This is speculation, so you may want to hang off for a more competent reply, but if you are feeling adventerous, this is what I would do. I'd simply move the file out of that folder but keep it incase it may be needed. My system is up to date and that folder is empty.

I would then run the configure command again.

---

### Post by seanarickymurphy on 2010-08-11
Solved my problem thanks anyway.

---

