---
title: "Syntax help for moving certain files out of a directory."
date: 2009-09-21
forum: General Help
---

### Post by x C0MMAND0 x on 2009-09-21
Okay, so long story short I have a folder with 6,000 some files.  I want to know the commands to do the following:

1. Move anything that contains "example" to a different directory
2. Delete anything that contains "example2" 
3. Move anything that contains "example1" or "example2" anywhere in the filename to a different directory

I admit I can navigate around the terminal and use it on a regular basis, but I could definitely use some help or an FAQ post on moving files around...

Thank you so much!

---

### Post by Johnny B on 2009-09-21
ls (folder) | grep 'example'  
this will give you a list of all files that contain 'example'


1. mv /folder/` ls (folder) | grep 'example' ` /different/directory
2. rm /folder/` ls (folder) | grep 'example2'  `
3. mv /folder/` ls (folder) | egrep 'example1|example2' ` /different/directory

---

### Post by x C0MMAND0 x on 2009-09-21
I'm trying to test that out but I'm having troubles...

As a test, I have my /home/brent directory.

I have a file in there that contains the word "test".  I want to move that file to /home/brent/documents

How would I do that?

mv /home/brent ls grep auto /home/brent/documents

?  Sorry. I'm a little unclear as the what the | means and also what ' means in the syntax...

---

### Post by x C0MMAND0 x on 2009-09-23
Bump.  I know there are plenty of people who know how to do this...

---

### Post by DaithiF on 2009-09-23
```
1. Move anything that contains "example" to a different directory
```
```
grep -l example * | xargs mv -t /path/to/destinationdir
```

2. Delete anything that contains "example2" 
```
grep -l example2 * | xargs rm -f

```

(that lower-case 'L' as a parameter for grep in the preceding examples.  Add 'i', ie. grep -li if you want to match example case insensitively -- Example, etc.)

3. Move anything that contains "example1" or "example2" anywhere in the filename to a different directory
```
mv *example[12]* /path/to/destinationdir
```

---

