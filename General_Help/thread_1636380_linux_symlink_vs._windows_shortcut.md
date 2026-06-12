---
title: "linux symlink vs. windows shortcut"
date: 2010-12-03
forum: General Help
---

### Post by MichaelBurns on 2010-12-03
Here's what I think that I understand:

Windows uses a "shortcut" to make a file appear to be present in a folder without actually taking up (much) space in the folder.  Apparently, the "shortcut" is an actual file that contains a small amount of information: the name and location of the target file and some actions that should be taken.

Linux uses a "link" to associate different file names in possibly different directories with the same inode (the actual (meta?)data for the file).  Apparently, the "link" is just part of the inode, along with the original file name and location, and in fact for "hard links" there is no distinction between the "original" file (name) and the newly created link.  For "symlinks", actions on the link are treated differently than on the "original" file (name), but the "symlink" is still apparently just a part of the same inode.

So, apparently, these two concepts that appear essentially identical to the end user are implemented very differently by the operating system (file manager).  In windows, there are two files in two different locations, and there is a definite subordination from the shortcut to the target.  In linux, there is only one inode that gives the illusion of two different files in two different locations, and subordination is blurred.

Here's my confusion:

My file manager (nautilus at the moment) can seemlessly display files from fat32, ntfs, and ext2 simultaneously, and I can even copy and paste from among the three.  If I didn't know about the distinctions, I would assume that the three file systems behaved identically.  Furthermore, as I understand the linux philosophy, everything is a file and is part of the same directory tree rooted at /.  So, what inhibits the implementation of a symlink on the particular branch of this tree that happens to be resolved from fat32?  I'm sure that it is possible in principle to implement symlinks on fat32; I just want to understand why it is not done in practice.

---

### Post by asmoore82 on 2010-12-03
> **MichaelBurns said:**
> Furthermore, as I understand the linux philosophy, **everything is a file** and is part of the same directory tree rooted at /.  So, what inhibits the implementation of a symlink on the particular branch of this tree that happens to be resolved from fat32?  I'm sure that it is possible in principle to implement symlinks on fat32; I just want to understand why it is not done in practice.

You're thinking correctly - *Everything* is a file!
Even directories - they are special files that contain lists of other files.
A typical file entry in a directory is a name to file object(**inode**) mapping. This "typical" mapping is a **hard link**. 

It's important to note that a file's name is never stored within the inode itself. The inode does contain a hard link count so that the system can detect when the inode is truly free to be deleted. So, there is nothing special about the file's "real" name, as far as the OS is concerned, it is just a hard link.

A **soft link**, or **symbolic link**, or **symlink** is a name to name mapping. This requires resolving (possibly multiple levels of soft links) to a hard link to retrieve the file's actual data.

So, in Linux (?Unix), links are implemented entirely at the directory layer and Fat32 directories cannot comply.

The efficiency of the Linux implementation is enormous!
Moving files around within the same filesystem is simply an edit operation on the "directory" files and doesn't have to touch the actual file's inode or sectors. This is also the roundabout explanation of why there is no "rename" command. You can't "rename" a file because the file object itself(inode) has no name.

---

### Post by mcduck on 2010-12-03
In Linux, the launchers (files with .desktop extension) are pretty much equivalents of Windows shortcuts.

Anyway, I'd say the main functional difference betweeen a Linux symlink and a Windows shortcut is that a shortcut takes you to the destination location, while a link brings the destination to where the link is.

For example, you have a shortcut and a link on your desktop (home/mcduck/Desktop), both pointing to a directory located on another drive (/mnt/media/files). Clicking on the shortcut will change your location to /mnt/media/files, while clicking on the link would change your location to /home/mcduck/Desktop/link/, just like if the link was an actual directory and the files really were in that location.

Tis difference in behavior, and the fact that symlinks are implemented at the filesystem level, not as an user interface feature, make them work for all programs as well instead of just the user. Ever tried to get a Windws program to follow a shortcut? Symlinks don't have such problems. :)

So no, a windows shortcut and a symlink are in no way practically identical to the user". A Windows shortcut and a Linux launcher (pointing to some location) would be identical.

And what prevents you from creating symlinks on the FAT or NTFS partitions is simply that those filesystems completely lack support for this kind of features. They wouldn't even know how to store such thing on the filesystem (besides, they don't even use inodes and lack support for most of the stuff Linux filesystems do anyway).

You can create a symbolic link pointing to a FAT or NTFS filesystem, though, that's not a problem as long as the link itself is on a Linux filesystem.

---

### Post by mc4man on 2010-12-03
you can create at least some types of soft links on a ntfs drive (haven't tried others, don't quite see the point of doing so
see screen for links to a .desktop and a script, both work as expected
(though more than possible i'm missing the point here..

---

### Post by asmoore82 on 2010-12-03
...continued...

The windows implementation lacks strong philosophy -
It confuses Shortcuts with Launchers and attempts a one-size-fits-all solution.
It works out OK for Launchers(if you can put up with binary blobs and windows) but is overkill for Shortcuts. Simple shortcuts shouldn't be a physical file themselves and shouldn't be able to hold custom icon data.

But, armed with this knowledge, you can easily simulate a windows shortcut with a linux launcher...

Right-click the Desktop and "Create Launcher"
Type -> "Location"
Name -> "<anything>"
Location -> "file://path/to/file/"

This will make a "Shortcut" Launcher (GUI-only) that is copyable to Fat32.

I edited the icon name by hand with gedit so here's what I ended up with:
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Link
Icon[en_US]=emblem-symbolic-link
URL=file:///home
Name[en_US]=Home
Name=Home
Icon=emblem-symbolic-link
```

---

### Post by mcduck on 2010-12-03
> **mc4man said:**
> you can create at least some types of soft links on a ntfs drive (haven't tried others, don't quite see the point of doing so
see screen for links to a .desktop and a script, both work as expected
(though more than possible i'm missing the point here..

true, current version of NTFS does support both soft and hard links, but the implementation is different from how Linux filesystems do them (so it's not compatible) and it really is rather rarely used feature in Windows. Perhaps because it took so  long for Microsoft to add it and because most people don't know about it anyway and you'd have to use the CLI to make them (which isn't fun at all with Windows, if you ask me. :D)

edit: have you actually tried if those symlinks say there when you unmount the drive? I was pretty sure you couldn't create a Linux-style symlink on NTFS...

(there's only one kind of soft link, so if you can symlink one thing you can symlink anyhting. Hard links of course won't work, but you can't make them between different filesystems anyway so it's not related to differences between Windows and Linux filesystems)

---

### Post by MichaelBurns on 2010-12-04
Thanks, everyone!  I learned a little bit more about links, and I learned the existence of *.desktop files.  (I think that I knew of these before, but I certainly didn't realize that they were like Windows' shortcuts.)  What a strange choice of file extension.  When creating a text file or a binary executable, I can use any file extension that I want (even no extension at all).  On the other hand, I must use .a or .so (appropriately) when linking with gcc, and .sh for a bash script, but I thought this was an issue with the particular program (gcc or bash) rather than a filesystem issue.  So, I'm wondering, why specifically .desktop?  Is this something in Nautilus, or is it more fundamental to Linux?

---

### Post by mcduck on 2010-12-04
It's not a Nautilus-specific thing (after all, you don't even use Nautilus to launch your programs, it's just the file manager). It's a freedesktop.org specification supported by most desktop environments.

[http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec]("http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec")

Pretty neat, actually, as it allows your programs to show automatically and correctly categorized regardless of what desktop environment, window manager or application launcher you happen to use. And also can include program names and descriptions and such information in many different languages etc. things, all in a single file.

---

