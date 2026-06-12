---
title: "list files which their names contain special character &quot;(&quot;"
date: 2010-03-27
forum: General Help
---

### Post by techbrainless on 2010-03-27
Hi All,

I am trying to list the files (in the current directory) which containing the special characters "(" in their names 

I have executed this  command :
$ls -ltr *(* 

 but am getting the command prompt ???

I have tried also something like this 
$ls -ltr */[()]/*
but getting error message:
bash: syntax error near unexpected token `('


I know it is easy question , but am really stuck in this question.

---

### Post by new_tolinux on 2010-03-27
This works (tested):
```
ls -ltr *\(*
```

---

### Post by techbrainless on 2010-03-27
thanks alot for the reply , it works fine............

---

