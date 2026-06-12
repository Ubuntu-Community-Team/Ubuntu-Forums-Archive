---
title: "How to reference my file"
date: 2011-07-06
forum: General Help
---

### Post by kike_skate on 2011-07-06
Hi there. 
 
I create a program on Java that read my File.log this is made in windows. And to look the file i reference like this in my DB PostgreSQL "C://Example//Documents//Archivo.log" .. now im doing the same but in Ubuntu when i reference my file  "//home//Example//workspace//Archivo.log " .. it doesn't found it in ubuntu.

My question is how is the right way to reference my file to find it in ubuntu. 

I hope i can made my self clear. Sorry for my bad english.

---

### Post by nzjethro on 2011-07-06
It may be because you have double "/", when you only need one. Try again with
```
/home/example/workspace/Archivo.log
```

Also, run the command
```
locate Archivo.log
```
and check that the file path it outputs is /home/example/workspace/Archivo.log. If it outputs a different file path, substitute that file path.

---

