---
title: "Bash help: List full path of files"
date: 2011-07-31
forum: General Help
---

### Post by 98cwitr on 2011-07-31
I have a parent folder with many subfolders within, I need a simple list of paths to these folders and their contents recursively

So in /media/share/parent/child/

I would have child1 through child2000 (non-sequential)

so I'd have the output of:

/media/share/parent/child/child1/diffFileName.html
/media/share/parent/child/child4/anotherFileName.html
/media/share/parent/child/child7/stillDifferentHere.html
/media/share/parent/child/child32/srsly?.html
...
/media/share/parent/child/child2000/end.html


how could I do this? ls doesn't seem to help...and I get a bunch of extra metadata with find.

I know there's got to be a simple way to do this.

---

### Post by AlphaLexman on 2011-07-31
> **98cwitr said:**
> I need a simple list of paths to these folders and their contents recursively
What do you mean by 'list their contents' ??

What if the file is binary, or compressed, or just a text file ??

Please be more specific.

---

### Post by nipennem on 2011-07-31
> **98cwitr said:**
> 
how could I do this? ls doesn't seem to help...and I get a bunch of extra metadata with find.

What extra "metadata" do you get with

```
find /media/share/parent/child/
```

?

---

### Post by 98cwitr on 2011-07-31
> **AlphaLexman said:**
> What do you mean by 'list their contents' ??

What if the file is binary, or compressed, or just a text file ??

Please be more specific.

they are just text files. I dont want the content itself, just the full paths to the files.

Metadata as in length and extra lines (find seems to segment the output).

---

### Post by AlphaLexman on 2011-07-31
The 'find' command just outputs the relative path of files found.

What is your exact command and what is the output you are getting ??

Also, what is the expected output ??

---

### Post by 98cwitr on 2011-07-31
so using find, I've got all the paths out to a text file. Now I just need to select every 3rd line. How would I use 'sed' to do this?

---

### Post by nipennem on 2011-07-31
> **AlphaLexman said:**
> The 'find' command just outputs the relative path of files found.

Find will use absolute paths if you provide it with an absolute path.

Find does not segment nor add extra lines.

Example:
```
$ find /var/lib/dictionaries-common/
/var/lib/dictionaries-common/
/var/lib/dictionaries-common/hunspell
/var/lib/dictionaries-common/hunspell/myspell-en-au
/var/lib/dictionaries-common/aspell
/var/lib/dictionaries-common/aspell/aspell-en
/var/lib/dictionaries-common/wordlist
/var/lib/dictionaries-common/wordlist/wamerican
/var/lib/dictionaries-common/wordlist/wbritish

```

Hence, I am convinced that find does exactly what you described you wanted.

---

### Post by nipennem on 2011-07-31
> **98cwitr said:**
> so using find, I've got all the paths out to a text file. Now I just need to select every 3rd line. How would I use 'sed' to do this?

I don't see an easy solution with sed, but there is one with awk:

```
awk 'NR%3 == 0' filename
```

---

### Post by 98cwitr on 2011-07-31
> **nipennem said:**
> I don't see an easy solution with sed, but there is one with awk:

```
awk 'NR%3 == 0' filename
```

thanks!

Sorry, I realized that I had not explained fully my dir structure. A few -delete switches with find and I got what I needed. Thanks!

---

