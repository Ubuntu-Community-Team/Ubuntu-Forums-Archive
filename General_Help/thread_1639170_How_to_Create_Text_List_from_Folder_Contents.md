---
title: "How to? Create Text List from Folder Contents?"
date: 2010-12-06
forum: General Help
---

### Post by Rasa1111 on 2010-12-06
Hey all,

 My apologies if this is in the wrong forum. 

I was recently contacted in regards to my *almost* 4,000 e-books,
by a couple of different people, 
asking if I could somehow provide a list of all my e-books. 
(almost 4 GB's worth)

So my question is...

 Is there a way for me to somehow create 
a simple text list/document, from my "e-books" folder? 

 Some way that I can take the title names of all the books in the folder,  and generate a simple text list of them. 
(without having to type out every one!) lol

 Is there a way to do this? 

If so, 
Would you care to enlighten a brother? lol

 Many thanks. <3

---

### Post by Keypel on 2010-12-06
> **Rasa1111 said:**
> Hey all,

 My apologies if this is in the wrong forum. 

I was recently contacted in regards to my *almost* 4,000 e-books,
by a couple of different people, 
asking if I could somehow provide a list of all my e-books. 
(almost 4 GB's worth)

So my question is...

 Is there a way for me to somehow create 
a simple text list/document, from my "e-books" folder? 

 Some way that I can take the title names of all the books in the folder,  and generate a simple text list of them. 
(without having to type out every one!) lol

 Is there a way to do this? 

If so, 
Would you care to enlighten a brother? lol

 Many thanks. <3

Just thought I'd bump this while waiting for an intelligent reply, There is definitely a way to do this. Something like opening a terminal and browsing to the dir and listing it's contents then piping the output to a text file. I've seen it done on a video tutorial but can't quite remember how it goes.

I could tell you the incorrect way of doing it if you like. Just open a terminal and browse to your your ebook folder and use ls command then just copy the info from the terminal to a new text file.

---

### Post by pricetech on 2010-12-06
In terminal;

cd /path/to/folder
ls > list.text

Open the resulting "list.text" file and there it is.  May need to edit out some extra stuff and / or reformat the file, but much easier than doing the whole thing manually.

Check the help that comes with ls to if there's an output more to your liking to start with.

---

### Post by Vaphell on 2010-12-06
find command is better because by default it goes down the tree recursively and looks into every subfolder

```
find <e-books folder> -type f -name "*extension" > list.txt
```
this dumps all matching files (-type f) to list.txt file

another one-liner to remove extensions and paths, leaving only name:
```
sed -r 's:(^.*/)|(\.[^\.]*$)::g' list.txt
```

this weird thing is a regular expression that is to be replaced by nothing (in other words deleted)
(^.*/) = line start (^) followed by any number (*) of anything (.), ended by /
(\.[^\.]*$) = dot (\.) followed by any number (*) of non-dots ([^\.]) and line end ($)
| = OR - so the command finds anything that looks like pattern1 or pattern2 and replaces it with empty string

---

### Post by Rasa1111 on 2010-12-06
Hey!
 Thanks everyone!
Great infos! 

It worked like a charm! :D woot! lol


> **pricetech said:**
> In terminal;

cd /path/to/folder
ls > list.text

Open the resulting "list.text" file and there it is.  May need to edit out some extra stuff and / or reformat the file, but much easier than doing the whole thing manually.



This is the post I tried from first ,
and it worked perfect. 

 Great to know!
and so easy!
damn, Many thanks!

 you guys rock! :KS  <3 :D

---

