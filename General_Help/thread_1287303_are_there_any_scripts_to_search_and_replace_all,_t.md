---
title: "are there any scripts to search and replace all, text in multiple files?"
date: 2009-10-10
forum: General Help
---

### Post by cosmoshell on 2009-10-10
are there any scripts to search and replace all text, in multiple files? I have allot of files to go threw and replace text, anyway to not have to open one after the other?


like to replace "hat" with "kite"

---

### Post by lloyd_b on 2009-10-10
There's a command-line program called "sed" (stream editor) that can do this.  "man sed" in a terminal window for more info, but a basic sed command like this is what I think you're looking for:```
sed -i "s/\<oldtext\>/newtext/g" *.txt
``` will look through all .txt files in the current directory, and replace the word "oldtext" with "newtext".

Make sure you have backup copies of all the files before using - a messed up sed command can do a lot of damage. :)

Lloyd B.

Edit - "\<" and "\>" around the search string will limit it to whole words ONLY.  That way "s/\<hat\>/kite/g" won't change "that" to "tkite". :)

---

### Post by cosmoshell on 2009-10-10
delete post

---

### Post by cosmoshell on 2009-10-10
delete post

---

### Post by cosmoshell on 2009-10-10
> **lloyd_b said:**
> There's a command-line program called "sed" (stream editor) that can do this.  "man sed" in a terminal window for more info, but a basic sed command like this is what I think you're looking for:```
sed -i "s/\<oldtext\>/newtext/g" *.txt
``` will look through all .txt files in the current directory, and replace the word "oldtext" with "newtext".

Make sure you have backup copies of all the files before using - a messed up sed command can do a lot of damage. :)

Lloyd B.

Edit - "\<" and "\>" around the search string will limit it to whole words ONLY.  That way "s/\<hat\>/kite/g" won't change "that" to "tkite". :)

how can I make it change "that" to "tkite". it doesent do this eather way, I want it to change "that" to "tkite".

---

### Post by cameronedwards on 2009-10-10
> **cosmoshell said:**
> how can I make it change "that" to "tkite". it doesent do this eather way, I want it to change "that" to "tkite".
im guessing if it was in the desktop and you wanted to change magic to kitten then: "sed -i "s/\</home/username/Desktop/magic>//home/username/Desktop/kitten/g" *.txt"

ok that didn't work...

---

### Post by cosmoshell on 2009-10-10
> **cosmoshell said:**
> how can I make it change "that" to "tkite". it doesent do this eather way, I want it to change "that" to "tkite".

edit bad example copy paste, I want hat = kite    that = tkite

---

### Post by lloyd_b on 2009-10-10
> **cosmoshell said:**
> edit bad example copy paste, I want hat = kite    that = tkite

"s/hat/kite/g" will do that.  I added the "\<" and \>" (which marks the beginning and end of words) on the assumption that you *didn't* want this behavior.

Lloyd B.

---

