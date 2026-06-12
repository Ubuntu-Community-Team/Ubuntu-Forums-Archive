---
title: "how to unzip files"
date: 2009-09-20
forum: General Help
---

### Post by chsd9 on 2009-09-20
its my 1st time using ubuntu,how do you unzip files? i keep getting error msg

---

### Post by staf0048 on 2009-09-20
You should be able to just right click on the file you need to unzip and select "extract here"

For ZIP files, make sure you have gzip installed.  Do a search through Synaptic. 

 If this doesn't work, please let us know exactly what error message you're getting.

---

### Post by kevdog on 2009-09-20
What kind of file do you want to unzip?  (The extension)?

---

### Post by chsd9 on 2009-09-20
i got it,thnx alot!!

---

### Post by rtyb on 2009-09-20
Seems like you already managed to...

but just in case get 7zip  :D

You should see it third, in the ¨All¨ Category when Showing ¨All Available Applications¨ (Add/Remove Applications)

---

### Post by infurnus on 2009-09-20
I found "e" to be an excellent program for this. Simplistic and perfect for the job. 

found here:[http://martin.ankerl.com/files/e](http://martin.ankerl.com/files/e)

depends on: apt-get install ruby file gzip bzip2 tar p7zip \
unzip unrar lzop rzip rpm binutils lha arj cabextract unace ppmd

you can either copy it to /usr/bin or link it :\ be sure to chmod +x 



I made one in perl that fixed the gzip issue - if anybody wants to add a tidbit in ruby to copy @ARGV (file.gz) to file.gz.tmp then extract @ARGV then mv file.gz.tmp to file.gz it will work around the issue. However, this program is still teh awesomezorz

---

