---
title: "HELP! can't restore important files from the trash!"
date: 2011-01-23
forum: General Help
---

### Post by &gt;hankim&lt; on 2011-01-23
Dear community.

But the reason I write is that I have a enormus conflict right now and I  wonder if some charity soul would be pleased to help me. 

The thing is that, don't ask me why, I have 5 folders in the virtual rubbish bin **that can not be seen** and restored but is crucial for me to recover them.

What could it be happening?

I was trying too record 5 folders with brasero and I sttoped the  process, then all of a sudden the folders dissapeared and after I found  then in the reclycling bin by *->* *right click/properties *
in this "basic" windows there It's said: *content: 413 elements ... 663.1 MiB in total* ...
also the picture of the bin appears full, and when I put the pick ontop of it it says: 5 elements in the bin...

please how can I restore them? 

thank you
Han

---

### Post by theOGRE on 2011-01-24
Open up a terminal and type:
```
ls -A ~/.local/share/Trash/files/
```That should show what's in your trash bin. If you find the file or folder you want, then:
```
mv ~/.local/share/Trash/files/<my-lost-file> ./
```That will put it in the current directory. Although if you cancelled the operation, I doubt the files would be any good.

---

### Post by &gt;hankim&lt; on 2011-01-24
Thx for the reply theOGRE,
Is that what I did wrong? shouldn't have cancelled that right?

ok then I could take them out... but where did it go? 
it is not where they where before neither in the bin anymore. I have no clue

cheers

---

### Post by &gt;hankim&lt; on 2011-01-24
AAAH! thx so much man! You saved my ***! I just found them at .home directory with ctrl+H

Fairwell!

---

