---
title: "Help with command line"
date: 2009-08-28
forum: General Help
---

### Post by t4ggs on 2009-08-28
Hi, as you know windows creates in every folder a file named Thumbs.db so i want to get rid of them, so i opened a terminal and run locate Thumbs.db and it found all of them
now, in order to delete them what should i do? i guess: locate Thumbs.db | rm

but it didnt worked....so what should i do??

---

### Post by scragar on 2009-08-28
```
find **StartDir** -name **FileName** -type f -exec rm -f {} \;
```
This will find all normal files(type f) in StartDir with the file name "FileName".

---

### Post by t4ggs on 2009-08-28
i didn understand....instead of file i should write Thumbs and instead of f i should write db?? what instead of StarDir??? and could u maybe explain the syntax of the command??? i would want to learn more... and thanks

---

### Post by scragar on 2009-08-28
Sorry, StartDir is the directory find should look inside, to search the whole system use '/' to search just your home folder use '~/' to search something mounted like a USB drive or something like that you'd use '/media/...' Where ... is whatever the media is called. Find will take long and longer the more it has to check first.

You're looking for a file called 'Thumbs.db'

Leave the filetype as it is, in linux there are a few types, these are different to s file extention, there's the obvious ones, like directories and normal files, but also block devices(like your hard drive), links(like shortcuts) and a few others. If you're ever in doubt it's probably a file or a directory.

```
find /home -name Thumbs.db -type f -exec rm -fv {} \;
```
That line is probably what you're looking for, since it'll search your home directory, but you probably want to search /media as well, since that's where windows file systems and removable media turn up.

---

### Post by credobyte on 2009-08-28
How to find and remove files: [http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/](http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/)

---

### Post by t4ggs on 2009-08-29
ok, thank u guys i ve done as u told me an credobyte, i checked your link, but still when enterin locate Thumbs.db it founds  a lot and they are all in /home

another question, what is bad with locate Thumbs.db | rm???

---

### Post by t4ggs on 2009-08-29
ohh i think i know, locate is perhaps searching an index and find do it physically....still i dont understand whats wrong with locate Thumbs.db | rm

---

### Post by CatKiller on 2009-08-29
> **t4ggs said:**
> still i dont understand whats wrong with locate Thumbs.db | rm

What would you be removing with that command? That's what's wrong with it. You've not actually told rm what it is that you want removed.

That's what the {} in the locate command signifies. It represents each filename returned by the locate command, so that you can do something (-exec something) to it. It's possible that ```
rm -
``` would take arguments from the [standard input]("http://en.wikipedia.org/wiki/Standard_streams#Standard_input_.28stdin.29") but I've never tried it, since find is a tool that's specifically designed to find files and do something to them.

---

### Post by andrew.46 on 2009-08-29
Hi t4ggs,

> **t4ggs said:**
> could u maybe explain the syntax of the command??? i would want to learn more... and thanks

There is a reasonably clear page that deals with the find command and its syntax:

find - Ubuntu Community Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

All the best,

Andrew

---

### Post by t4ggs on 2009-08-29
Thanks to every one of you, now I have a better comprehension.

---

