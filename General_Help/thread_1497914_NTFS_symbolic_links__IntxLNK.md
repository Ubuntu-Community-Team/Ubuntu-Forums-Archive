---
title: "NTFS symbolic links / IntxLNK"
date: 2010-05-31
forum: General Help
---

### Post by MWP on 2010-05-31
Hi all,

For a while now i have been backing up (rsync) to a 1.5TB NTFS formatted USB drive.
Now the time has come that i need that backup :(

Looking at the contents of the NTFS drive, all my symbolic links have been converted into a single file which contents starts with the text "IntxLNK".
It seems this is some kind of SMB/CIFS/Microsoft link file.

Does anyone know how i can convert these "link files" back into linux symbolic links?

Thanks in advance!!

---

### Post by Endolith on 2011-02-27
I'd like to know this, too.  I'm trying to migrate all my files from EXT to NTFS, but Ubuntu's choking on the symlinks.  NTFS supports symlinks just fine, and [Link Shell Extension]("http://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html") is smart about moving them (unlike Ubuntu), but when I try to move links from EXT to NTFS they're converted into these files that start with "IntxLNK" at the beginning.  Is there some way I can move symlinks from EXT to NTFS?

---

### Post by dcstar on 2011-03-01
> **Endolith said:**
> I'd like to know this, too.  I'm trying to migrate all my files from EXT to NTFS, but Ubuntu's choking on the symlinks.  NTFS supports symlinks just fine, and [Link Shell Extension]("http://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html") is smart about moving them (unlike Ubuntu), but when I try to move links from EXT to NTFS they're converted into these files that start with "IntxLNK" at the beginning.  Is there some way I can move symlinks from EXT to NTFS?

You cannot expect all things on a Linux filesystem to be able to be copied to a foreign filesystem. NTFS does **not** support all Linux filesystem features and attributes.

Linux symlinks are either specific pointers to inodes (hard links) or mounted filesystem location meta-data (soft links), both of these become invalid when moved to a foreign filesystem.

---

### Post by mcduck on 2011-03-01
links, permissisons, ownerships and such are features of the filesystem itself, not just some special type of files. And the implementation is very different between Linux fileyssems and te NTFS versiosn that support similar features. That makes converting them between different filesystems rather hard, if not completely impossible. (not to forget than even the ability to reliably read/write NTFS from Linux is quite a new thing, and Windows still hasn't made any move at all towards such co-operation with different operating systems... ;))

(by the way, Ubuntu handles moving symbolic links just as well (if not better, considering that all this stuff works by default in any Linux version) as the windows shell extension you mentioned, both are able to move or copy a link inside or into a *filesystem that supports the link*. Linux does that as long as you are working with Linux filesystems, and that Windows extension does it if you are working with NTFS filesystem.)

Also, while it's a bit late for the OP of this thread, the best way to handle backups into other than Linux filesystems is to make the backup into a .tar.gz file. That allows maintaining directory structure, ownership, permissions and links etc. even if the backup archive is located on a filesystem that doesn't support such features, like FAT or NTFS drive.

---

