---
title: "Need to change the location for matlab license file"
date: 2009-07-20
forum: General Help
---

### Post by Volume on 2009-07-20
Hello,

I finally managed to install MATLAB 2009a on 9.04, but in my excitement, I pointed to the license file saved on my desktop.  How can I change the location MATLAB looks for the file?  I just don't want to always have to look at the license file on my desktop.

Thanks all.

---

### Post by Volume on 2009-07-28
Bump?  Any help out there?

---

### Post by XCan on 2009-07-29
I've no idea, on my computers I could always save the license to wherever I want, upon installation Matlab would copy it into its own dir anyway. Do a
```
locate license.dat
```
to see if it copied the license file.

---

### Post by vette427 on 2009-08-20
I did the **exact** same thing just now. I don't wanna look at license.dat on my desktop either. I tried ```
locate license.dat
``` and the desktop is the only place that file is, however the installer did make a license.txt file in the matlab directory. I then moved the license.dat file into my matlab directory using this code:
```
 
sudo mv -t <directory_to_move_license.dat_into> <path_to_where_license.dat_currently_is>

```
, replacing the <> brackets with the correct paths of course, and matlab seems to work just fine. It would probably work even if you delete license.dat since it most likely just uses the license.txt file, but I wanted to keep the original one to be safe.

---

