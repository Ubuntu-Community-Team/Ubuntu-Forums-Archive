---
title: "Zipping contents of multiple folders"
date: 2010-10-08
forum: General Help
---

### Post by SRabin on 2010-10-08
Hi all;

I have a set of folders in some directory /home/dir, and I'd like to generate zip files for the contents of each folder separately. I'm wondering if there's a quick way to do this with a one-liner, or what the bash script would be.

Directory structure:
/home
[INDENT]/dir[/INDENT]
[INDENT][INDENT]/first[/INDENT][/INDENT]
[INDENT][INDENT]/second[/INDENT][/INDENT]
[INDENT][INDENT]/third[/INDENT][/INDENT]

and I want three files, first.zip, second.zip, and third.zip. I know zip isn't the best format, but these are for distribution to users on Windows machines and I'd prefer to keep them in the zip format.

---

### Post by zadehas on 2010-10-08
cd to /home/dir and then try this:

```
find -maxdepth 1 -type d -exec zip -r '{}'.zip '{}' \;
```

This will output a zip archive for each folder on the first sublevel of /home/dir (note maxdepth=1).

---

### Post by SRabin on 2010-10-08
Thanks - this is exactly what I was looking for!

---

