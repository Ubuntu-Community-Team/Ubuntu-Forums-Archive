---
title: "Sorry for askin this ques :-)"
date: 2006-04-29
forum: General Help
---

### Post by minhaz4u on 2006-04-29
When I type the path in terminal...how do I type it if there is space in the filename???

For eg : 
therez a folder named:   **/My Documents**
How do I type this in terminal with a remove command???
plz help :(

---

### Post by ZylGadis on 2006-04-29
I don't know of a "folder" named My Documents, unless you have created it, of course. Which is not really good. Try to shun the things you learned in Windows, as most of them don't apply here. This is just a general bit of advice. (And yes, folders are really called directories in linux).
To your question: when you write the first few letters of a file's or directory's name and then press Tab, the name will be autocompleted. If there is more than one option, pressing Tab again will show all options.
Otherwise, non-alphanumeric characters in names must be escaped with backslash (unless you have changed your escape character, which I doubt). So My Documents becomes My\ Documents.
Hope that helps.

---

### Post by bluevoodoo1 on 2006-04-29
/My\ Documents


rmdir /My\ Documents

rmdir -r /My\ Documents
(be **careful** with that, it will remove the directory and all files in it)

---

