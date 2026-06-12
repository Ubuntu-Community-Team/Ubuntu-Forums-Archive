---
title: "changing extentions of files."
date: 2010-02-22
forum: General Help
---

### Post by nos09 on 2010-02-22
here is the thing. my friend gave me the the lyrics folder and all lyric are in text files what if i want to convert them in .lyics extention.

i use rhythm box so everytime the new songs is played then i have to open the files manually if i can change text lyics files in to the .lyrics files then i can just give the path to the rhythembox and it will show the lyrics autometically.

the problem is there are too many files. so is there any way to change them all at once without changing thier name for example greenday.txt, here's your letter.txt to ( greenday.lyrics, here's your letter.lyrics)

all of them at once.

---

### Post by hemimaniac on 2010-02-22
you could install gprename ( i believe it is in the repos unless they took it out, you could google it) and this is a batch renamer so you could use the replace option and just put 

before : txt replace with .lyrics in the replace tab

---

### Post by am4tor on 2010-02-22
> **nos09 said:**
> ... too many files. so is there any way to change them all at once without changing thier name for example greenday.txt, here's your letter.txt to ( greenday.lyrics, here's your letter.lyrics)

all of them at once.
 
Make a search in **synaptic** with word "rename", You'l find progs like "prefixsuffix" or "Thunar Bulk Rename" -with GUI. Install Thunar and start-it from Menu .
There You may change only suffix as you wish.
B.r.

---

### Post by gmargo on 2010-02-22
[SIZE=2]As hemimaniac suggested, install the[/SIZE][SIZE=2] **gprename** package[/SIZE] (it may already be installed) and do them all with one command:
```

rename 's/\.txt$/.lyrics/' *.txt

```Now I've reread your message and I'm not sure if this is what you asked, since you said "is there any way to change them all at once without changing thier name".
Is it the file extension you wanted changed?  Or something inside the file?

---

### Post by nos09 on 2010-02-22
> **gmargo said:**
> [SIZE=2]As hemimaniac suggested, install the[/SIZE][SIZE=2] **gprename** package[/SIZE] (it may already be installed) and do them all with one command:
```

rename 's/\.txt$/.lyrics/' *.txt

```Now I've reread your message and I'm not sure if this is what you asked, since you said "is there any way to change them all at once without changing thier name".
Is it the file extension you wanted changed?  Or something inside the file?

yes its file extensions. like i've got lyrics in text file in a folder say : music/lyrics/Avril and there are 10 txt files. i m giveing the name of 3 of them, 
1. hot.txt
2. one of those girls.txt
3. girlfriend.txt

now i want them to convert into.

1. hot.lyric
2. one of those girls.lyric
3. girlfriend.lyric

this was just example there are thousands of files like this i want to convert all of them at once. and please use example given above if you give a code to me. thanks

---

### Post by x C0MMAND0 x on 2010-02-22
If they all end in .txt, you simply need a command to remove the last 4 characters from the filename, and then add .lyric in place of it.  Does that sound correct?

---

### Post by nos09 on 2010-02-22
> **x C0MMAND0 x said:**
> If they all end in .txt, you simply need a command to remove the last 4 characters from the filename, and then add .lyric in place of it.  Does that sound correct?

yes just remove .txt and add .lyric instead of it

---

### Post by gmargo on 2010-02-22
Ok, just renaming files from _**.txt**_ to _**.lyric**_.  Over a bunch of sub-directories containing files which may have spaces in the name.  Here we go:
```

# change into the top level directory of your lyrics files
cd music/lyrics
find . -type f -name '*.txt' -print0 | xargs -0 rename 's/\.txt$/.lyric/'

```If you want to "try before you buy", then add a **-n** option on the **rename** command.

---

