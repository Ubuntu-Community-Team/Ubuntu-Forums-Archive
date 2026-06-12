---
title: "How do I set/change mdraid array name?"
date: 2010-05-04
forum: General Help
---

### Post by Ypthor on 2010-05-04
I forgot to name some of my arrays and now I can't find a way to set it.

I thought I could do it with 'mdadm --assemble --update=name' but it doesn't seem to do any such thing. If I try and append a new name (e.g. =name:NAME or =name=NAME or =name NAME) I get an error message saying it's invalid and it doesn't prompt me if I don't either.

Can I set/change that name in any proper way? Do I use the above command? How, if so?

Or can I manually edit the superblock in any way?

It's not a critical problem, but I'd like those devices nicely named :)

(I know I could name them by recreating them, but I've been creating and recreating arrays for the last two days and I've just had enough, so that's not going to happen.)

---

### Post by coffee412 on 2010-05-04
According to the man page on mdadm you can only select the name (-N) when creating the array. Sorry to be bearer of bad news. 
> **-N**, **--name=** 
Set a **name** for the array. This is currently only effective when creating an array with a version-1 superblock. The name is a simple textual string that can be used to identify array components when assembling. 

coffee

---

### Post by Ypthor on 2010-05-08
Yes, I saw that too, I was hoping there would be some workaround.

Since then I stumbled upon a bug that makes named arrays unusable by autostarting a bogus array with one of the components (on my system at least), so it wouldn't work anyway.
 :) :| :(

---

