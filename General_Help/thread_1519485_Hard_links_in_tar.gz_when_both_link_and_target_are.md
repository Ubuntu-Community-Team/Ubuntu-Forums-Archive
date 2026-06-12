---
title: "Hard links in tar.gz when both link and target are in the archive"
date: 2010-06-28
forum: General Help
---

### Post by john1923 on 2010-06-28
Hi

I am copying my home folder from my old computer (Ubuntu 9.10) to my new one (Ubuntu 10.04)

I thought that I would make a tar archive of my home directory (~60GB), then copy it across the network and untar it in my new home folder.

The problem is that I have several hard links (30 at most). When I try and untar the tar in my new computer it runs into errors with the hard links.

I think the problem is that it has unzipped the hard link before it's target and detected an error.

One solution is to add --hard-dereference to the tar command , this will create a separate copy of each hard link. but I would really like an exact copy of my home folder on my new computer.

Does anyone have any ideas? Either copying my home directory, or how to make tar handle hard links sensibly?

Thank you in advance

---

### Post by gzarkadas on 2010-06-30
Try to feed tar the `--same-order' option when extracting; it may work (it may also not; never did it before :) ).

If the above will not work, make a list of all your hardlinks, use `--hard-dereference' with tar and when everything is extracted, replace the copies with hard links again. If _all your hardlinks are files_*,* this command (run at the original filesystem) will show them:

```

find -type f -a -links +1 2>/dev/null

```

You can also try `rsync' with the `-av -HAX --compress' options. rsync supports keeping hard links (-H) and also acls (-A) and extended attributes, as well as compression accross the wire.`man rsync' to find more.

---

### Post by john1923 on 2010-07-14
Thanks for the reply,

I moved my data using rsync and a portable hard disk formated with ext4. Not the most elegant way, but it worked.

---

