---
title: "7zip not working"
date: 2011-03-02
forum: General Help
---

### Post by surfingonmusic on 2011-03-02
everytime i try to extract a rar file it gives me this error 


cannot find volume /home/filepath   CRC failed

neither unrar or 7zip work
help please!

---

### Post by surfingonmusic on 2011-03-02
64-bit ubuntu btw

---

### Post by ngrieb on 2011-03-02
I think there is a separate rar library in the repos. Try that out.

---

### Post by Telengard C64 on 2011-03-02
Some Rar archives cannot be extracted by 7-Zip. Try the **unrar** package which is described as *non-free*.

---

### Post by surfingonmusic on 2011-03-02
i've tried unrar aswell and tested loads of zip files and none are extracting=/

---

### Post by wiggly81 on 2011-03-02
have you installed the rar and 7zip extensions ? search in the software center if not

---

### Post by Telengard C64 on 2011-03-02
:confused:

Maybe your command syntax is not correct? Please show us what you are doing.

Maybe your archives are corrupt, or if they are multi-volume archives maybe some members are missing? Try unpacking these three **known good** archives to test whether 7z is really working or not.

[_zip30.zip_](http://sourceforge.net/projects/infozip/files/Zip%203.x%20%28latest%29/3.0/zip30.zip/download)
[_7z920_extra.7z_](http://downloads.sourceforge.net/sevenzip/7z920_extra.7z)
[_rarlng.rar_](http://www.rarlab.com/rar/rarlng.rar)

All three are source code file, and so should be completely safe. The Rar file, gives "unsupported method" when attempted to extract via **7z**, but extracts perfectly with **unrar non-free**.

---

