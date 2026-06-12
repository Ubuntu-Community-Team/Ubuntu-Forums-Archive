---
title: "Deleted Nearly Everything in Home Dir"
date: 2011-06-23
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2011-06-23
Trying to install Texlive 2011, I typed a command from the website without thinking to take a good look at what it does:  rsync -a --delete --exclude="mactex*" rsync://somemirror/some/path/ /your/local/dir   and I typed in my home directory for /your/local/dir. Of course, almost everything in my home directory was deleted. Is there any way to attempt to recover this stuff without restoring? I thought there was a slim chance it might be in Trash, but that seems to have been deleted as well.

---

### Post by collisionystm on 2011-06-23
> **StarKid said:**
> Trying to install Texlive 2011, I typed a command from the website without thinking to take a good look at what it does:  rsync -a --delete --exclude="mactex*" rsync://somemirror/some/path/ /your/local/dir   and I typed in my home directory for /your/local/dir. Of course, almost everything in my home directory was deleted. Is there any way to attempt to recover this stuff without restoring? I thought there was a slim chance it might be in Trash, but that seems to have been deleted as well.


Nope... Your files are gone.

Next time watch out for that --delete /switch lol.

It deletes any files on the destination side that don't exist on the source.

rsync < source > < destination >

---

