---
title: "Can I have one folder in two seperate places?"
date: 2010-12-17
forum: General Help
---

### Post by winchendonsprings on 2010-12-17
Not including symbolic links. 

Here is the situation. 
-I need to have a folder (named example.me) inside a folder called /sites.
-I need to also have that same folder (example.me) inside a folder called /public_html.
-Is this possible?
-Is this confusing?
-I can post the long version of the problem if needed.

---

### Post by dcstar on 2010-12-17
> **winchendonsprings said:**
> Not including symbolic links. 

Here is the situation. 
-I need to have a folder (named example.me) inside a folder called /sites.
-I need to also have that same folder (example.me) inside a folder called /public_html.
-Is this possible?
-Is this confusing?
-I can post the long version of the problem if needed.

Use a hard link (if they are on the same filesystem).

```
man ln
```

---

### Post by winchendonsprings on 2010-12-17
I thought hard links couldn't link folders. only files. no?

yes. hard link not allowed for directory

I need to have two folders that is technically only one folder and they can't be soft linked either. possible?

---

### Post by wojox on 2010-12-17
Why can't you use a symlink?

Are both folders in your /home directory?

> -I can post the long version of the problem if needed.

Please.

---

### Post by winchendonsprings on 2010-12-17
both folders are on a server and one needs an 'add-on' domain pointed to it.

but add-on domains can only point to folders in the /public_html directory. (at least on the server I'm using can't)

For a normal multi-site Drupal install sites need to be in /public_html/sites/example.me.

so I need the add-on domain to point to the folder example.me (/public_html/sites/example.me)

but I cannot point it past a folder within /public_html

I know it's confusing

more detailed version [here]("http://drupal.org/node/999788#comment-3842436")

---

### Post by StephenDavison on 2010-12-17
Try mount with the --bind option.  That might fit your need.

mount --bind olddir newdir

I just tried this (within my home directory) to bind ~/gobin to another directory name.  Now I see the same contents in both locations.

---

### Post by winchendonsprings on 2010-12-17
whoa, looks like mount --bind does what I need but, is there any chance it will become unmounted on the server for any reason?  or any other problem?

anything I should know?

---

### Post by StephenDavison on 2010-12-18
I just followed your link to read the full post on the Drupal forums.  Considering the mount required root access (i.e. sudo mount ...), I don't think that is going to work for you with Bluehost.

---

### Post by winchendonsprings on 2010-12-18
100% right you are. no root access. Just tried it. I'm new to ssh.

---

