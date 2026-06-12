---
title: "Free FTP Hosting"
date: 2010-04-28
forum: General Help
---

### Post by Hman242 on 2010-04-28
I need a FTP host for a rather large file of mine, I also need this host to be free. Any recommendations?

---

### Post by Leppie on 2010-04-28
exactly how large is "rather large"?
can you not split the files in parts?

---

### Post by Hman242 on 2010-04-28
I have done that, but when I reassemble it, it seems to corrupt it. I'm not able to the the file(.exe) on the other computer. The file is 5.5GB.

---

### Post by Leppie on 2010-04-28
how exactly did you split the file?
normally an application would just cut the file into manageable pieces and after which the pieces only have to be concatenated. 
try something like lxsplit:
```
sudo apt-get install lxsplit
```then split the archive into pieces:
```
lxsplit -s hugefile.exe 200M
```you can then upload the pieces and download them on the windows machine and put them together with hjsplit or 7zip, or something similar.

Are  you actually sure the executable wasn't corrupt before splitting up the file?

---

### Post by Hman242 on 2010-04-28
I don't believe so, but there no way(that I know of) to tell without being able to transfer the complete intact file.

---

### Post by Leppie on 2010-04-28
use an external drive?
or if you have an official windows cd/dvd you can create a windows livecd using BartPE: [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by Hman242 on 2010-04-28
I don't have a storage meduim that's big enough for the file and I'm too cheap to go out and buy one. The purpose of the thread was to find a free FTP host, if there is one.

---

### Post by Leppie on 2010-04-29
there's plenty of free sites offering free storage, however most have a file size limit of around 200mb. some have a limit of 500mb.
i've never seen free storage being offered for files larger than 1gb though...
and of course, free storage has very limited bandwidth...

---

