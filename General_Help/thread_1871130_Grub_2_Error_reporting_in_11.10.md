---
title: "Grub 2 Error reporting in 11.10"
date: 2011-10-28
forum: General Help
---

### Post by EPLesPaul on 2011-10-28
I can't seem to get Windows 7 to work with Ubuntu. Using 11.04, grub gave me an error. Under 11.10, grub just gives me a blinking cursor. Does anybody know how to enable the error reporting? I would like to trouble shoot my issue.

---

### Post by oldfred on 2011-10-28
Welcome to the forums.

Blinking cursor may mean grub has booted and it is an Ubuntu issue. Often video issues leave you at the blinking cursor.

If your install does not see the Windows install it thinks it has only one install and grub menu is not shown. Try holding shift key down from BIOS until menu appears.

If a grub issue:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If a video issue:
Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

