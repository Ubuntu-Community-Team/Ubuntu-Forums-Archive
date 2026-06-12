---
title: "Gedit dictionary resets to blank"
date: 2009-11-09
forum: General Help
---

### Post by gstuart on 2009-11-09
Hi: After upgrading from Ubuntu 9.04 > 9.10, my Gedit dictionary (1000's of saved spellings) is missing.

For whatever reason (despite having "aspell" installed via Synaptic, etc.) the Gedit dictionary is located at 

/home/victoria/.config/enchant/en.dic

i.e. ~/.config/enchant/en.dic

I replaced it with a rsnapshot (rsync) backup copy that preceded the date of my upgrade, but every time I run the Gedit spell check, it overwrites this file (en.dic) with a new, blank file.

Suggestions? Thx, Victoria  :-)

(Gripe: Why does every friggin' upgrade have to be so problematic - missing config settings, ... - it never ends?)

---

### Post by gstuart on 2009-11-13
RESOLVED:  My system is updated (Synaptic) with the new file (libenchant1c2a version 1.5.0-0ubuntu3) mentioned below.  I replaced my ~/.config/enchant dictionaries (en.dic; en_US.dic) with my rsnapshot (Rsync) backups, and so far, they have not been overwritten!  This is a huge relief!

Victoria  :-)

 ---------------------------------------

[http://old.nabble.com/Gedit-dictionary-keeps-getting-overwitten-%28set-to-blank%29---Ubuntu-9.10-to26325563.html](http://old.nabble.com/Gedit-dictionary-keeps-getting-overwitten-%28set-to-blank%29---Ubuntu-9.10-to26325563.html)

On November 12, 2009 Victoria wrote:

My Gedit dictionary keeps getting over-written (set to blank) - Ubuntu 9.10

"Hello: I posted this two days ago to the Ubuntu Forums,

[http://ubuntuforums.org/showthread.php?t=1321097](http://ubuntuforums.org/showthread.php?t=1321097)

but I have had no replies; I am re-posting here, with some additional information: After upgrading from Ubuntu 9.04 > 9.10 a few days ago, my Gedit dictionary (1000's of saved spellings) is missing. ..."

Response:

This is not a gedit issue. Enchant was fixed a while ago. Ubuntu patched its version and released it two days ago. The fix is in libenchant1c2a version 1.5.0-0ubuntu3. Update your system to get the fixed package. BTW. I found a copy of my old personal .aspell dictionary. I moved it to .config/enchant.en.dic to get most of my spellings back.

---

