---
title: "automatically make a list of files?"
date: 2010-09-14
forum: General Help
---

### Post by panti19 on 2010-09-14
i have a bunch of folders with karaoke files (thousands) (mp3 and cdg files) and i need to make a list of these files(a txt for example) so i can print it.
is there a program that can make that sort of list? or is there another way? terminal maybe..

thanks

---

### Post by pbrane on 2010-09-14
you could try
```

ls -R > karaoke_list.txt

```
in a terminal

---

### Post by howefield on 2010-09-14
To make a listing of eg, the music in your Music folder type the following into a terminal..

```
ls -R ~/Music > output.txt
```

Name the file whatever you want and it will be created in the folder that your are currently in.

---

