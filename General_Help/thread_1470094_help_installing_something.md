---
title: "help installing something"
date: 2010-05-02
forum: General Help
---

### Post by termin on 2010-05-02
hello im trying to install peazip and its different then the usual ./configure, make, make install
instead it has two folders (please look at attachment)

thanks

---

### Post by linuxonbute on 2010-05-02
> **termin said:**
> hello im trying to install peazip and its different then the usual ./configure, make, make install
instead it has two folders (please look at attachment)

thanks

I think you are doing it the hard way.
Goto  [http://peazip.sourceforge.net/index.html](http://peazip.sourceforge.net/index.html)

Download the Linux DEB installer.

When it is downloaded it looks like you will see an icon on your desktop.
Right click on it and left click on 'Open' in the list which comes up.
Follow the instructions.

---

### Post by krismatth3 on 2010-05-02
For reference, it looks like the tar file that you have is intended to be expanded over /. A .deb is certainly preferable, but:  ```
 # tar xvf filename.tar -C / or # tar zxvf filename.tar.gz -C / 
```  should do the trick. (Or just cp -R the files from where you extracted them to)

---

### Post by termin on 2010-05-03
> **linuxonbute said:**
> I think you are doing it the hard way.
Goto  [http://peazip.sourceforge.net/index.html](http://peazip.sourceforge.net/index.html)

Download the Linux DEB installer.

When it is downloaded it looks like you will see an icon on your desktop.
Right click on it and left click on 'Open' in the list which comes up.
Follow the instructions.

thanks i just downloaded the source blindly without knowing. the link is okay and it installed perfectly.

---

