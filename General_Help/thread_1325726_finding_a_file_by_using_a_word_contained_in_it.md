---
title: "finding a file by using a word contained in it"
date: 2009-11-13
forum: General Help
---

### Post by yanvolking on 2009-11-13
Hello Community,

Is there a line command which allows one to locate a file by using a key word contained in it?  I thought "grep" could do this but I have not found a way of making it work.

Thanks

---

### Post by audiomick on 2009-11-13
My big fat smart book refers to a thing called Beagle that might be what you are after.

---

### Post by delcypher on 2009-11-13
Hmm pretty sure you can just do

```
grep -r --files-with-matches 'search string' /folder/to/search/
```

That will recursively serarch /folder/to/search with your search string. Use the -F option if you don't plan to actually be using regular expressions. Note this searches the contents of the file. Not the file name.

---

### Post by audiomick on 2009-11-13
I actually haven't used either, but according to my book grep can only search text files, whereas this Beagle thing can also deal with open office formats and a number of others.

There is also a command "find" that looks for files

---

### Post by spcwingo on 2009-11-13
How about the locate command with a wildcard.  Say you wanted to look up a file with Ubuntu in the name. That code would be:

```
locate *ubuntu
```

Let me know if that does the job.  :)

---

### Post by yanvolking on 2009-11-14
hello Delcypher,

I tried using your suggestion on a word processor file : /home/exercises/09097_eric.doc, which contains the word "news" in its text.

in the terminal I put:

yan@yan-acer:~$ grep -r --files-with-matches 'news' /home

and this is what I got :

yan@yan-acer:~$ grep -r --files-with-matches 'news' /home
/home/yan/.kde/share/apps/amarok/mysqle/amarok/magnatune_tracks.MYD
/home/yan/.kde/share/apps/amarok/mysqle/amarok/jamendo_albums.MYI
/home/yan/.kde/share/apps/amarok/mysqle/amarok/opmldirectory_albums.MYD
/home/yan/  
and on it went for hundreds of lines...

Maybe I did not explain myself clearly.  I am looking for a command which enables finding the location of a file(s) containing a specific word/symbol INSIDE IT.

Any further suggestions?

Thanks in advance

Yan

---

### Post by oldos2er on 2009-11-14
Maybe this will help: [http://www.matisse.net/OSX/intro_unix/05d_Searching_for_Text.html](http://www.matisse.net/OSX/intro_unix/05d_Searching_for_Text.html)

---

