---
title: "Customizing my FS: What filesystem features depend on an inode size of 256?"
date: 2012-03-22
forum: General Help
---

### Post by stlu on 2012-03-22
Hello,

I am trying to have total control over creation of a filesystem.  I have been sticking with a plan to have minimal features, but I have an external hard drive, and I wanted to add the feature "has_journal" in case it is accidentally unplugged, without taking any other features called for in /etc/mke2fs.conf.

If somebody could fill this in, it would answer my question.  Assume that the filesystem in question will never need to have any additional features other then what is called for in the mkfs.ext2/ext3/ext4 commands.

**Ubuntu 9.04 (referring to /etc/mke2fs.conf):**
section [defaults]
sparse_super: Does it need 256 (I doubt it)
filetype: Does it need 256 (I doubt it)
resize_inode: Does it need 256?
dir_index: Does it need 256?
ext_attr: Does it need 256?

section [ext3]
has_journal: Does it need 256?



Ok, now for the latest version, as of this post.  In this scenario I am looking at installing ubuntu 11.10 on my internal drive, and I am curious which features in ext4 must have the inode size set to 256.

**Ubuntu 11.10(referring to /etc/mke2fs.conf):**
section [ext4]
extent: Does it need 256?
huge_file: Does it need 256?
flex_bg: Does it need 256?
uninit_bg: Does it need 256?
dir_nlink: Does it need 256?
extra_isize: Does it need 256?


I hope that this way a lot of questions can be answered all at once.

Finally, in the case of my external hard drive, I wonder if I picked the correct features for my usage.  from dumpe2fs, the current features I set are:
"has_journal dir_index filetype sparse_super"

I am storing a lot of files, so that is why I chose dir_index and filetype.  I have used mke2fs without any features, so I know that sparse_super is a MUST for anything larger then 1GB.  Again, being an external drive, I am adding has_journal because it is more vulnerable then an internal drive, easily being unplugged before an unmount actually completes.

I called mke2fs with arguments including ^resize_inode,^ext_attr" to cancel those two, as I don't plan to make changes or enhancements to the functionality of this filesystem.

Thanks for advice!

---

### Post by stlu on 2013-01-15
Bump.  I still can't find out more about this...

---

### Post by rnerwein on 2013-01-16
> **stlu said:**
> Bump.  I still can't find out more about this...
hi
to find out have a look at: /etc/mke2fs.conf
for me i always create with those defaults and using mount for specail access (performance ...).
have a look at the: man mount
ciao

---

