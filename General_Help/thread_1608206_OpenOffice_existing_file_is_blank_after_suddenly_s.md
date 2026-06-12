---
title: "OpenOffice existing file is blank after suddenly shutdown"
date: 2010-10-28
forum: General Help
---

### Post by auchaunn on 2010-10-28
Hi. My friend was working on a text doc on openOffice and when suddenly his lappy went to hibernation mode. and he had to manually shutdown his lappy. The file his was working with is now blank. the file its self indicates that it is 0 kb.

Could anyone here help him please.

Thx Auchau N. Ngo

---

### Post by Hagar Delest on 2010-10-29
First check the backup folder in the profile (see [[Tutorial] The OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=12426)).

If no backup (.bak file), check the temporary folder (exact path in OOo Tools>Options>OOo>Paths) and if there is a folder similar to sfght.tmp with a file with the same name, make a copy of that file and change its extension to .odt.

Else, I fear there is nothing to do, especially if your file system is EXT4.

---

### Post by auchaunn on 2010-10-30
hi mate! Thx will tell my buddy about it. Let you know if it gets solved! 

Regards Auchau N. Ngo

---

### Post by Vaphell on 2010-10-30
go to options and enable backups in load/save section so you are covered in the future.

---

