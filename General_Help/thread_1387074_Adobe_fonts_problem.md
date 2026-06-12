---
title: "Adobe fonts problem"
date: 2010-01-21
forum: General Help
---

### Post by hwttdz on 2010-01-21
I'm having some trouble with some adobe fonts (at least I think that's it).  Anyways the errors received are 

```
Warning: Cannot convert string "-adobe-courier-medium-r-*--14-*-*-*-m-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-courier-bold-r-*--14-*-*-*-m-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-courier-medium-r-*--12-*-*-*-m-*-*-*" to type FontStruct
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  45 (X_OpenFont)
  Serial number of failed request:  643
  Current serial number in output stream:  654
```

xlsfonts|grep adobe|grep courier
```
-adobe-courier-bold-i-normal--0-0-0-0-p-0-iso8859-1
-adobe-courier-bold-i-normal--0-0-0-0-p-0-iso8859-15
-adobe-courier-bold-i-normal--0-0-0-0-p-0-iso8859-2
-adobe-courier-bold-o-normal--0-0-0-0-p-0-iso8859-1
-adobe-courier-bold-o-normal--0-0-0-0-p-0-iso8859-15
-adobe-courier-bold-o-normal--0-0-0-0-p-0-iso8859-2
-adobe-courier-bold-r-normal--0-0-0-0-p-0-iso8859-1
-adobe-courier-bold-r-normal--0-0-0-0-p-0-iso8859-15
-adobe-courier-bold-r-normal--0-0-0-0-p-0-iso8859-2
-adobe-courier-medium-i-normal--0-0-0-0-p-0-iso8859-1
-adobe-courier-medium-i-normal--0-0-0-0-p-0-iso8859-15
-adobe-courier-medium-i-normal--0-0-0-0-p-0-iso8859-2
-adobe-courier-medium-o-normal--0-0-0-0-p-0-iso8859-1
-adobe-courier-medium-o-normal--0-0-0-0-p-0-iso8859-15
-adobe-courier-medium-o-normal--0-0-0-0-p-0-iso8859-2
-adobe-courier-medium-r-normal--0-0-0-0-p-0-iso8859-1
-adobe-courier-medium-r-normal--0-0-0-0-p-0-iso8859-15
-adobe-courier-medium-r-normal--0-0-0-0-p-0-iso8859-2
```

I went looking for those files to see if I could symlink a 14 one to either the 15 one or the other ones, but I couldn't find the files anyways.  I get this when attempting to run an X windowed program (qmon) and it crashes out while printing the first set of errors.

---

### Post by hwttdz on 2010-01-21
I believe it was xfonts-75dpi and xfonts-100dpi that were missing which was causing the problem.  I'll test that theory later on another box that has a similar config to this one.  Marking as solved in any case.

---

### Post by thk on 2011-09-07
I just installed xfonts-75dpi and xfonts-100dpi and still get the same error. (Running natty in vbox machine.)

---

