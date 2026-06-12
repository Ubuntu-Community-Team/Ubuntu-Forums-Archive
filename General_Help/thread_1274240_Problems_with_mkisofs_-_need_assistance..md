---
title: "Problems with mkisofs - need assistance."
date: 2009-09-24
forum: General Help
---

### Post by credobyte on 2009-09-24
```
dd if=/dev/cdrom of=cd.iso bs=1024 
```Problems:

[LIST=1]
[*]Every file name in the ISO image contains ( at the end ) a new symbol: **;**
[*]512Mb CD resulted in a 235Mb ISO image
[/LIST]

Any ideas/suggestions ? I'm trying to backup my motherboard and video driver CD's ( will die soon ), but as far as I see .. I've backed up something unusable.

---

### Post by sedawk on 2009-09-24
You can use tool isoinfo on CDs or iso-images.
```

isoinfo -d dev=/dev/cdrom # UNTESTED
isoinfo -d -i ./cd.iso

```
Important is this output:
Logical block size is: 2048
Volume size is: 123456

So to create an iso image of the above CD you use
```

dd if=/dev/cdrom of=cd.iso bs=2048 count=123456

```
(Or try using a tool like isodump.)

When creating an iso image with dd you do not change
any data - you create a 1:1 copy.
So there is no way to mess up file names with "dd".
(Unless you mount the iso image the wrong way - but
 I think that is not a problem with Ubuntu ...)

In the subject you talk about "mkisofs". When creating
CDs with mkisofs you should use the options "-r" and
"-J" (see man page).
Otherwise you might really see funny "old-school"
file names like README.TXT;1

For further details check:
[http://en.wikipedia.org/wiki/ISO_9660](http://en.wikipedia.org/wiki/ISO_9660)
[http://en.wikipedia.org/wiki/Rock_Ridge](http://en.wikipedia.org/wiki/Rock_Ridge)
[http://en.wikipedia.org/wiki/Joliet_(file_system](http://en.wikipedia.org/wiki/Joliet_(file_system))

---

### Post by credobyte on 2009-09-24
Sorry, looks like I've 'misspelled' the thread title - I had problems with dd, not mkisofs ( creating an ISO from a folder resulted in a bootable ISO image ).
Anyway, I still can't seem to find, where's the problem regarding ISO size when doing dd - it's still 1/3 of an actual size of my CD :-k

---

### Post by sedawk on 2009-09-25
If the size of the iso image is smaller then
blocksize (2048)* Volume size (number of blocks) given
by isoinfo there is something wrong.

A workaround might be to copy the whole CD to a new
directory and to create an iso of that directory with
mkisofs (for recursive copies I like the rsync tool).

Copy-protected CDs often have broken blocks so that
tools like dd have to give up and cannot copy the
whole CD.

---

