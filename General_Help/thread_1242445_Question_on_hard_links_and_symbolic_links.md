---
title: "Question on hard links and symbolic links"
date: 2009-08-17
forum: General Help
---

### Post by jimhenry on 2009-08-17
I know the basic difference between hard links and symbolic links, and how to control which kind one makes with 'ln' vs. 'ln -s'.  There's something in the Ubuntu Pocket Guide that leaves me a bit puzzled, though:

> 
&#8208;s : Create symbolic link, rather than hard link. In nearly all situations, a symbolic link is preferable, making this practically a prerequisite command option
I'm not clear on why one would consider symbolic links preferable to hard links in nearly all situations.  In particular, I've had some recent problems with symbolic links breaking when I reorganized my directory structure, moving and renaming some files and directories; the hard links didn't break, of course, and didn't have to be recreated.

In some situations, of course (e.g. making a link across different filesystems) a hard link is not possible, or is fairly difficult and dangerous (e.g. hard-linking to a directory).  But those situations seem rather the exception than the rule.  The only reason I've thought of why a symbolic link might be preferable to a hard link is when you want it to be clear which location has the real or original file and which has a link to it; e.g. if you're afraid you might forget that two paths refer to the same underlying file, and edit one while intending to leave the other one in its original state, forgetting that they're references to the same thing.  Or if you're trying to free up disk space and you delete a large file, but no space is freed because there still exist one or more other hard links to it...   Could there be security problems with different hard links to a file having different permissions?  I did a quick test, making a file, making a hard link to it, then 'chmod -w' on the first file, then did 'ls -l' and saw that the second file also became read-only.  I'm not absolutely sure that a permission discrepancy couldn't occur under some other circumstances, but my understanding is that permissions and ownership information are in the (necessarily single) inode, not the (possibly multiple) directory entries.

I wonder if it might be useful to modify 'ls' and/or a file browser so that it highlights regular files with two or more hard links in some way?  You can do ls -l and look at the hard link count column, of course (though Nautilus > right-click on file > Properties doesn't seem to show the hard link count, and link count doesn't seem to be among the columns you can choose to display), but that assumes you're already thinking of whether a file has multiple hard links, and the only situation I can think of where hard links would be disadvantageous is when you've forgotten there are multiple links to one file.

---

### Post by jimhenry on 2010-04-25
I've discovered another advantage to symbolic links, and another advantage to hard links, since I posted the above:

1. If copying a directory hierarchy to an NTFS filesystem (presumably a fortiori if copying to an ext2 system), symbolic links within that hierarchy are preserved and don't take up extra space on the target system.  But hard links result in multiple copies of the same file on the target filesytem.

2. If copying a directory containing symbolic links to a VFAT filesystem (such as an mp3 player), neither the symbolic links nor the files they point to get copied unless you give the -L option to the cp command.

---

