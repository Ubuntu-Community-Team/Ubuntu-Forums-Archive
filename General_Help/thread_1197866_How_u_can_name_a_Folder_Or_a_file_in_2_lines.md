---
title: "How u can name a Folder Or a file in 2 lines?"
date: 2009-06-26
forum: General Help
---

### Post by AlNaimi on 2009-06-26
Hi every one....
Could i name a folder Or a file in 2 lines...I don't mean that long, But as you do in text file (you press enter to go another line)..Is that possible?
Another Question:
I use Grsync to sync my folders and files to another device, But unfortunately none of my folders or files notes & emblems sync to the device?
Any idea...
Thanks

---

### Post by Agent ME on 2009-06-26
The filename should automatically wrap to the next line if it has spaces in it and it's too long to fit on one line in Nautilus.

---

### Post by WRDN on 2009-06-26
All text in filenames is treated as a literal string (i.e. you can't escape to a newline), so you cannot press Enter/Return and place text on a second line or more. As Agent ME mentioned, the text should wrap around to a new line if it's to long, but this is merely aesthetics, and the filename remains as a single line of text.

---

### Post by geirha on 2009-06-26
On ext2/3 filesystems, any character except the null character (\0) and / are allowed in filenames, so that means you can have newlines in filenames. However I strongly recommend against it. Applications and scripts may not expect a newline in a filename, and may break in weird ways when it encounters one.

Don't know if you can set newlines in filenames through nautilus, but in bash (the terminal) you can use $'\n'. E.g.:
```
touch $'file\nwith\nnewlines'
```

As I noted earlier, this is not a good idea. You have been warned :)

---

### Post by AlNaimi on 2009-06-26
Thanks guys
What about the another Question? Any Idea

---

