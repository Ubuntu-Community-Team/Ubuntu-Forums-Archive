---
title: "Removing all .jpg's from folder &amp; subfolders"
date: 2009-10-01
forum: General Help
---

### Post by ngrieb on 2009-10-01
I have been using Linux for about 2 years, but have a really noob question:
I was wondering what the easiest way to delete all .jpg images from a folder containing subfolders would be (I want to delete them in subfolders too). At first I thought that this would be easy just a rm -rvf *.jpg, but this does not seem to work. Why is this? Is there any way I can do this without some crazy shell script? (Perhaps by using a pipe from grep to rm, or something odd like that?). Thanks in advance.

---

### Post by kaibob on 2009-10-01
This will do what you want:

```
find /target/directory -name '*.jpg' -type f -delete
```

I'm sure you understand the need to be careful with this.

---

### Post by undecim on 2009-10-01
The reason this doesn't work is because *.jpg represents every file and directory in the current working directory that ends in ".jpg". It won't do subdirectories...

The command that kaibob posted should do the trick though.

---

### Post by ngrieb on 2009-10-01
I'll give it a try, and yes I realize very much that rm or delete are potentially dangerous commands, which is why I asked in the first place. I really don't want to get things wrong cause I like my other pics...just not my useless space wasting album art. Thanks. =-)

---

