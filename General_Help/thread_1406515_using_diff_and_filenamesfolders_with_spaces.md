---
title: "using diff and filenames/folders with spaces"
date: 2010-02-14
forum: General Help
---

### Post by faust99 on 2010-02-14
This is not really a problem as such, since I managed to compare two directories using Meld, but I am interested in whether it is possible to use diff to compare directories in which there are filenames and sub-directories that contain spaces in the name (e.g. /media/backup/external disc/new work.odt). Obviously the terminal does not allow manipulation of directories with embedded spaces...

Would you have to rename all directories and filenames so as not to have spaces (and how would you do this anyway)?

---

### Post by SecretCode on 2010-02-14
Terminal **does** allow manipulation of files and directories with spaces in - you just have to quote the entire string or escape (with \) the space characters.

```
diff file\ with\ spaces "another file with spaces"
```

---

### Post by faust99 on 2010-02-14
> **SecretCode said:**
> Terminal **does** allow manipulation of files and directories with spaces in - you just have to quote the entire string or escape (with \) the space characters.

```
diff file\ with\ spaces "another file with spaces"
```

Oh that's really cool-I didn't know, and "obviously" it wasn't so "obvious"!](*,) A paragraph from [this]("http://www.linuxcommand.org/lts0020.php#file") article confused me about embedded spaces in file/dir names:

> While Linux supports long file names which may contain embedded spaces and punctuation characters, limit the punctuation characters to period, dash, and underscore. **Most importantly, do not embed spaces in file names**. If you want to represent spaces between words in a file name, use underscore characters. You will thank yourself later.

I misread it.

Anyway, thank you SecretCode.

---

