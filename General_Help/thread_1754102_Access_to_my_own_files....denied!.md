---
title: "Access to my own files....denied!"
date: 2011-05-09
forum: General Help
---

### Post by OllieGab on 2011-05-09
One thing I still struggle with after over 2 years of Linux (Ubuntu) is to access certain files despite the fact that I am the owner. And despite the fact that I'm root when trying.
I'm trying to remove some files (in backup .ful type folder) from an external HD but get the message that it is read only.
I tried first with 'sudo nautilus' but was told that Nautilus couldn't handle that sort of operations.
I tried sudo.....rm from the command line but was still denied.
Why? I just want to remove some stuff from my OWN machine!:-|

Cheers Ollie

---

### Post by mikewhatever on 2011-05-09
Sometimes it's the permissions (grub.cfg), since by design, some files aren't supposed to be edited. Other times, it's the file system that's been mounted as read only. In the latter case, all files in that file system will be read only, which means, no one can delete anything, even the owner. Anyway, Linux doesn't have the same notion of ownership as humans. It cares not about the name or the id number of the person who bought the computer, it just follows the specified rules.

---

### Post by tredegar on 2011-05-09
You need to give us some more information:

You say it is an "external HD". What is it formatted as (FAT, NTFS, EXT*)?

When it is mounted, what are its permissions?

The output of **ls -al /media/*[COLOR="Blue"]whatever[/COLOR]*** would be helpful here.

---

### Post by OllieGab on 2011-05-10
My external HD makes a lof of funny noises at the moment when I plug it in, though eventually it mounts and can display its contents. Perhaps, if partly broken, it only mounted in a read-only soft of mode? Could that be possible?
I'll get myself a new one and see if it behaves differently!

---

