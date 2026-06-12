---
title: "Can't compile the following program."
date: 2011-07-18
forum: General Help
---

### Post by ALF102 on 2011-07-18
I followed the steps from the this website [http://rarcrack.sourceforge.net/](http://rarcrack.sourceforge.net/)

but after I run:

sudo make 

I got this output:

gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
rarcrack.c: In function ‘crack_thread’:
rarcrack.c:206:32: warning: comparison between pointer and integer
rarcrack.c: In function ‘init’:
rarcrack.c:283:6: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘char (*)[300]’
rarcrack.c:317:9: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
rarcrack.c: In function ‘crack_thread’:
rarcrack.c:205:11: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result

---

### Post by mc4man on 2011-07-18
You are only showing warnings, take a look in your source folder to see if a binary was created (typically a blue diamond file

---

### Post by seawolf167 on 2011-07-18
Aye, warnings usually still produce the compiled binary, if you see an "error: " then you'll have to do some work figuring out what is going wrong.

---

