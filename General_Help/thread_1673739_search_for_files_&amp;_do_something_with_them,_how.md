---
title: "search for files &amp; do something with them, how to?"
date: 2011-01-22
forum: General Help
---

### Post by LewRockwellFAN on 2011-01-22
I've spent all day looking for a way to do something I expected to be easy and I'm half expecting somebody to point out the obvious solution I've been overlooking and be exposed as an idiot. I'm trying to search a directory recursively (including all the sub-directories, sub-sub-directories, etc.) for all jpgs and copy them to another directory, preferably renaming the ones that have duplicate names. Of all the GUI linux search utilities I've tried the one that comes on the default install comes the closest in that it will allow me to select files from the list of findings and will allow me to export a list of their complete names including path to a text file. But that is it. I can't simply copy them. Am I missing something? Surely there must be a way to do this other than installing a Windows program to run under Wine. That is what I'm going to try next, while awaiting y'all's collective advice. Fortunately the files are on a FAT 32 in case the Windows program can't handle that. I could just reboot and do this in W2k but I have processes going on that I hate to interrupt. I'm thinking it might be possible to operate on that text file with some terminal commands but I haven't figured out how yet.

---

### Post by Vaphell on 2011-01-22
find command is all you'll ever need for such stuff
it's recursive with optional depth parameter, offers tons of search options and allows to perfom an action on each found object.

```
find <directory> -type f -name '*.[jJ][pP][gG]' -exec mv -n "{}" <destination> \;
```
detecting a name collision requires some additional effort but it's nothing that can't be done.

search dir for any file (-type f) with a name ending with .jpg (any combination of small and capital letters) and perform an action (-exec) of move (mv) the object({}) without overwriting (-n) to destination.
any files left in the source dir will be those that need renaming (run find again without -exec part to get the list)

---

### Post by LewRockwellFAN on 2011-01-23
Thanks, Vaphell! I've been studying man pages to understand that line completely.  I think I understand all but the last 2 characters "\;". I think I need to change "mv -n" to "cp -i" to do what I want but the rest of it seems to be right on the money. What are those last 2 characters for?

---

### Post by nothingspecial on 2011-01-23
The ; exits the find command.

The \ escapes it so bash doesn`t interpret/expand it as a special character.

---

### Post by LewRockwellFAN on 2011-01-23
Thanks, nothingspecial. I went ahead and used the command with the substitution I mentioned and the "\;" included and it worked fine so now that you've cleared up that question I'll mark this solved. :)

---

