---
title: "wget all &quot;Title_*.txt , staying in folder"
date: 2010-03-11
forum: General Help
---

### Post by Dayofswords on 2010-03-11
i cant figure out how to download all the files using wget , what i want to do is download all files in a web directory(stay in that folder) that match "Title_*.txt", anyone know how?

i looked through the gnu's wget manual but it didnt explain it very well

---

### Post by Dayofswords on 2010-03-11
i did what i wanted to the long way
making a text file and putting every url I wanted to download into it

using```
wget -i /home/username/urllist
```

basically what i'm looking for is the something that does ```
wget http://example.com/dir/Title_*.txt
```
but wild cards arent allowed

---

### Post by nikhilbhardwaj on 2010-03-11
does this help
[http://stackoverflow.com/questions/273743/using-wget-to-recursively-fetch-a-directory-with-arbitrary-files-in-it](http://stackoverflow.com/questions/273743/using-wget-to-recursively-fetch-a-directory-with-arbitrary-files-in-it)

[http://www.thegeekstuff.com/2009/09/the-ultimate-wget-download-guide-with-15-awesome-examples/](http://www.thegeekstuff.com/2009/09/the-ultimate-wget-download-guide-with-15-awesome-examples/)

---

