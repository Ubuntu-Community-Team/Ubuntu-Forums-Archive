---
title: "Font rendering issue in OpenOffice"
date: 2011-12-05
forum: General Help
---

### Post by pratikk on 2011-12-05
I use Win TTF fonts in OOo (have to, my printer insists). Quite often, it looks like there's an invisible strikethrough in a line of text. Edit a character and the 'strikethrough' vanishes. Screenshots attached, since it's difficult to convey. It's not a font issue, since the fonts print fine and look OK in PDFs. But it's an aesthetic problem when you're doing a layout. Any idea how to resolve it?

Thanks

Pratik


OpenOffice.org 3.2.1 
OOO320m19 (Build:9505)
ooo-build 3.2.1.4, Ubuntu package 1:3.2.1-7ubuntu1.1

---

### Post by BC59 on 2011-12-05
I found these on OOffice website:

Bad quality of screen font rasterization
Symptom
TrueType fonts look chiseled and angular on screen and/or have bad spacing while the same font looks quite nice in Mozilla, Gnome or KDE applications.
Problem description
OpenOffice.org uses the FreeType library for font rasterization. The FreeType library has been compiled with auto-hinting enabled and byte-hinting disabled. While auto-hinting does a reasonable job for grid fitting it's result is still inferior to byte-hinting for many fonts. Please have a look at [http://freetype.sourceforge.net/patents.html](http://freetype.sourceforge.net/patents.html) for a discussion of that issue.
Trouble shooting
Currently there is no workaround for this issue. It is recommended to use an XServer that supports the antialiased graphical representation of glyphs for improved readability.


And 

User interface font looks garbled
Symptom
Some RedHat users complained that the menu and user interface elements of OpenOffice are almost unreadable or that no font at all is visible.
Background
RedHat 7.2 ships with ulT1mo latin2 fonts. One of the fonts is installed as "Arial" typeface. There is a fair chance that OpenOffice.org chooses this font as the UI font.
Trouble shooting
It is worth a try to remove the fonts from the fontpath since this fixed the problem for many users.
Check if your fontpath settings include this path. Issue the command "xset -q" in a shell. Check if "/usr/X11R6/lib/X11/fonts/latin2/Type1" is contained in the list that belongs to the "Font Path:" section.
If it is please remove it from your fontpath using the "xset -fp "path_element" " command, restart OpenOffice.org and see if your problem's solved. To permanently remove this directory from the fontpath you need to edit your XServers configuration, usually found in the directory /etc/X11/XF86Config-4.
If you are using a font server please run the command "chkfontpath" or if that fails the command "/usr/sbin/chkfontpath". Again check the output for the occurrence of the above mentioned path. To remove the path you need to edit the font server configuration. Usually you'll find it in the file /etc/X11/xfs/config. After changing the configuration you need to restart the font server (run the command "/etc/rc.d/init.d/xfs restart" with root permissions). Please double check with your system administrator before changing system configuration files. Make a backup of the file before you are going to change it.

---

### Post by pratikk on 2011-12-06
Thanks a lot for a very detailed reply. I have the screen font problem described in the first para. Pity there's no solution, since I have found OOo to be much more useful and versatile than Word. Anyway, I guess I can always ignore those funny-looking lines! Thanks again for taking the trouble.

---

### Post by DapperMe17 on 2011-12-06
Couldn't you just use the "free" style fonts by default in Ubuntu? They should open just fine in Word.

---

### Post by pratikk on 2011-12-06
Dapperme, that's not an option for purely illogical reasons. The press I use is comfortable only with Win fonts. If they replace the fonts in my documents, the text would move slightly.

---

