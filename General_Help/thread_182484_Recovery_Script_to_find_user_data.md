---
title: "Recovery: Script to find user data?"
date: 2006-05-26
forum: General Help
---

### Post by theturner on 2006-05-26
I wanted to upgrade my father's machine from Hoary to Breezy (and then Dapper), and I wanted to to it the wise way: Shrink the partition, install Breezy on another one, and if it works wipe the first one.
But apparently parted was a bit unlucky in resizing the (reiserfs) partition (and I'm guilty for ignoring all the warnings), and now after doing a ```
reiserfsck --rebuild-tree
``` I have all its data in a "lost&found" folder, with funny names like 510160_619036. Judging from the size, nothing got lost, but it's about 18.000 files.

[SIZE="3"]Is[/SIZE] there any way to sniff the files's mimetypes and sort them? I'd really need Evolution e-mails and address book, and common file types like doc, jpeg, html etc. wouldn't be too bad either. Any help is appreciated!

---

### Post by Denis on 2006-05-26
You could try the "file" command to find out what kind of file it is.  Then you can use some commands to narrow down your results.

For example: 
file /lost&found/* | grep Document
or
file /lost&found/* | grep "Microsoft Office Document"

will display a list of files of the type "Microsoft Office **Document**"

Look for other filetypes you may be interested in. The MIME type can also be used with "type -i".
You could look up types (or mime types) with the file command on another system to determine what type Evolution e-mails or addess book is. 

Good luck.

---

