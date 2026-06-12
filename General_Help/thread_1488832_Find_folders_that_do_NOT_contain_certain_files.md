---
title: "Find folders that do NOT contain certain files"
date: 2010-05-20
forum: General Help
---

### Post by merry_meerkat on 2010-05-20
[SIZE="2"]Hello,
I am trying to find out how to search for **folders** that do **not** contain certain files. Could anyone let me know how to do that?[/SIZE]

More details: My music collection of 20+GB a is organised into folders *(Artist-Album)*. I would now like to ensure that every album folder contains the respective cover art image as a **cover.jpg** file. Quite a few do already, but many don't. So I would like to find all folders (not files) that fulfil the following criteria:
[LIST=1]
[*]is a subfolder of /home/user/Music;
[*]does NOT contain further subfolders (i.e. don't want to find artist folders);
[*]does NOT contain a file named cover.jpg.
[/LIST]
Thanks a lot for any help!

---

### Post by pr0t3g3 on 2010-05-20
What do you mean?  Do you want a folder made specifically for certain files?

---

### Post by merry_meerkat on 2010-05-20
Hi, no I don't want to make a folder, just **find** folders:
I have about 600 folders with music (one folder per album) and I want to know *which* of these folders do NOT contain a file called **cover.jpg**.

Hope this makes it clearer. Thanks again!

---

### Post by mmmichael on 2010-05-22
There must be a simple one line piece of code that can do this,  but I don't know what it is. This should work though:

```
cd ~/Music
find ./* -maxdepth 0 -type d > albums
find ./* -maxdepth 1 | grep cover.jpg > has_art
gedit has_art
```

In the editor window, click Search, then Replace.
In the search field type /cover.jpg
Leave the replace with field blank and click Replace All.
Click Save.
Close the editor and back to the terminal.

```
diff albums has_art > needs_art
less needs_art
```

Now your /home/Music directory should have three new files:
albums, containing a list of albums
has_art, listing albums that have the cover file
needs_art, listing folders that do not contain cover.jpg.

---

### Post by merry_meerkat on 2010-05-22
Thanks!!
This already gets me most of the way.

(there's a further complications: the albums are in artist subfolders, so your instructions alsoreturn artist folders - but, as I said, it's already a great help)

Thanks again.

---

### Post by mmmichael on 2010-05-22
I don't know exactly what your /Music directory looks like, but maybe you can replace this part

```
find ./* -maxdepth 0 -type d > albums
find ./* -maxdepth 1 | grep cover.jpg > has_art

```

with

```
find ./*/* -maxdepth 0 -type d > albums
find ./*/* -maxdepth 1 | grep cover.jpg > has_art

```


Repeat the whole sequence, changing those 2 lines. The files albums and has_art will be overwritten with the new data.
Maybe?...

---

### Post by kaibob on 2010-05-23
> **merry_meerkat said:**
> Hi, no I don't want to make a folder, just **find** folders:
I have about 600 folders with music (one folder per album) and I want to know *which* of these folders do NOT contain a file called **cover.jpg**.

Hope this makes it clearer. Thanks again!
The OP has almost certainly moved on, but I wanted to see if I could resolve his issue with a bash one-liner. I was able to accomplish this with process substitution, but the resulting command was too long. So, I instead wrote a simple shell script that is similar to mmmichael's suggestion. In this script, the maxdepth option has to be adjusted to reflect the extent to which the shell script should traverse the directory structure. Depending on the OP's needs, a mindepth option may also be needed.

```
#!/bin/bash

cd /target/directory

find ./* -maxdepth 3 -type f -iname "cover.jpg" | sort | while read line ; do
   echo "${line%/*}" >> file1
done

find ./* -maxdepth 2 -type d | sort >> file2

comm -3 file1 file2

rm file1
rm file2
```

---

