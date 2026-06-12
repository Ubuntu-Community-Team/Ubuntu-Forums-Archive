---
title: "wgeting japanese pages"
date: 2010-10-26
forum: General Help
---

### Post by damogran on 2010-10-26
Hi there, 

sorry if this is not the correct forum category. 

I'm trying to use a wget saved html page within a bash script. if i browse to a certain url all the japanese signs shows up correctly. i can also open vi inside the gnome terminal and can copy and paste japanese signs. i can also grep japanese signs out of files. but, whenever i try do something like 

  wget -O file.html [http://japanese.homepage](http://japanese.homepage)

i ending up with a file full of useless ascii clutter, inbetween some regular html tags and readable stuff. 

do i need to add something to the wget call? some loacle stuff or something? 

would be nice if someone could help me out.

thanks in advance

damo

---

### Post by kumaryu on 2010-10-26
It's likely that the text on the web page is encoded using Shift-JIS and not UTF8.

You can use iconv to convert from one encoding to another.

iconv <original.file> -f SHIFT-JIS -t UTF8 -c -o <converted.file>

---

### Post by damogran on 2010-10-26
perfect ! works for me but have to use the EUC-JP encoding. 

awesome, thanks a lot! 

> **kumaryu said:**
> It's likely that the text on the web page is encoded using Shift-JIS and not UTF8.

You can use iconv to convert from one encoding to another.

iconv <original.file> -f SHIFT-JIS -t UTF8 -c -o <converted.file>

---

