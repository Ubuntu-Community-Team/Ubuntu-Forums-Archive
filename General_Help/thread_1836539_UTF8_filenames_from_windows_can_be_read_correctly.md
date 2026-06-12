---
title: "UTF8 filenames from windows can be read correctly"
date: 2011-08-31
forum: General Help
---

### Post by hakermania on 2011-08-31
Hi there, nautilus doesn't seem to be capable of reading utf8 characters when these come from a windows machine.
Let's say I have some Greek songs with Greek names in my Windows partition and I zip them *from* windows. Then I log in to ubuntu and take the zip file from the windows partition and I unzip it.
The Greek filenames are broken, they are like:
?????????.mp3 (invalid encoding)

Same thing with .txt files that come from windows. If they have normal name but contain Greek characters, i cannot read them properly, I get strange characters like those in the filenames of i.e. the songs.

Strange...

PS: In the language support I've installed Greek but menus and windows use English

---

### Post by tredegar on 2011-08-31
My guess is that the filenames are not UTF-8 (which would display properly) encoded, but you can convert them to UTF-8 with the **convmv** utility.

---

### Post by hakermania on 2011-09-01
thanks, i will try this

---

