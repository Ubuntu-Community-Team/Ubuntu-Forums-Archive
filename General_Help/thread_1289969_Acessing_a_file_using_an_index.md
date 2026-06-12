---
title: "Acessing a file using an index"
date: 2009-10-13
forum: General Help
---

### Post by AndrewSimoes on 2009-10-13
After listing the files in a directory using 'ls'  , is it possible to use them without typing their names .. say by an index like their order number?

---

### Post by lloyd_b on 2009-10-13
> **AndrewSimoes said:**
> After listing the files in a directory using 'ls'  , is it possible to use them without typing their names .. say by an index like their order number?

Could you provide a little more information as to what you are trying to do?  AFAIK, there's nothing like a numerical index for the files.  But there are techniques that allow you to take the list of files, and process them one at a time.  For instance:[CODE]for FILE in *; do ls -l $FILE; done[/DONE] will loop through them one at a time, executing "ls -l" for each one.

If you tell us what the objective is, we can probably give you a shell command/script to accomplish it...

Lloyd B.

---

### Post by AndrewSimoes on 2009-10-13
My objective is simply to avoid tedious typing .

For example in my Music directory I have Rachmaninoff. Then Piano Concerto 2 with other folders. So the cd command becomes long. It's also impractical to add each one of them as an alias.

---

### Post by diesch on 2009-10-13
Use file name completion: Type the first character(s) of a folder or file name, then hit <TAB>. If there's only one option to complete the name bash will type that for you. If there's more than one option bash will complete as much as is unique; hitting <TAB> twice will show you all possibilities to complete.

---

### Post by AndrewSimoes on 2009-10-16
Thanks. That was of great help.

---

