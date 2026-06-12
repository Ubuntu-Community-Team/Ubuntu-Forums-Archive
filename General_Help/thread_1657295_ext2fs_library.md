---
title: "ext2fs library"
date: 2011-01-01
forum: General Help
---

### Post by COKEDUDE on 2011-01-01
Can someone please tell me how to install the ext2fs library?

---

### Post by calavier62 on 2011-01-01
have you tried: 'sudo get-apt e2fslibs'?

---

### Post by COKEDUDE on 2011-01-01
> **calavier62 said:**
> have you tried: 'sudo get-apt e2fslibs'?

The command is this: 

```
sudo apt-get install e2fslibs
```

Yes I have.

---

### Post by QLee on 2011-01-01
[QUOTE=COKEDUDE]The command is this: 

```
sudo apt-get install e2fslibs
```Yes I have.[/QUOTE]

Presumably it didn't work or you wouldn't be asking this question. So, what was the error message dropped when you tried that?

---

### Post by COKEDUDE on 2011-01-02
> **QLee said:**
> Presumably it didn't work or you wouldn't be asking this question. So, what was the error message dropped when you tried that?

extundelete does not think it is installed. Every time I try to install extundelete it complains that e2fslibs is missing. I don't understand what the problem is. 

```
~ $ sudo apt-get install e2fslibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
e2fslibs is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 180 not upgraded.

```

---

### Post by mc4man on 2011-01-02
> try to install extundelete it complains that e2fslibs is missing
Where did you get extundelete from? Typically when an app complains about an installed library it's either incompatible version(s) or a path issue

Edit: 
you'd probably be better off building/installing the current source, takes all of a min. or so
ex.
> ~/Downloads/extundelete-0.2.0$ extundelete --help
Usage: extundelete [options] [--] device-file
Options:
  --version, -[vV]       Print version and exit successfully.
  --help,                Print this help and exit successfully.
  --superblock           Print contents of superblock in addition to the rest.
                         If no action is specified then this option is implied.
  --journal              Show content of journal.
  --after dtime          Only process entries deleted on or after 'dtime'.
  --before dtime         Only process entries deleted before 'dtime'.
Actions:
  --inode ino            Show info on inode 'ino'.
  --block blk            Show info on block 'blk'.
  --restore-inode ino[,ino,...]
                         Restore the file(s) with known inode number 'ino'.
                         The restored files are created in ./RESTORED_FILES
                         with their inode number as extension (ie, file.12345).
  --restore-file 'path'  Will restore file 'path'. 'path' is relative to root
                         of the partition and does not start with a '/' (it
                         must be one of the paths returned by --dump-names).
                         The restored file is created in the current
                         directory as 'RECOVERED_FILES/path'.
  --restore-files 'path' Will restore files which are listed in the file 'path'.
                         Each filename should be in the same format as an option
                         to --restore-file, and there should be one per line.
  --restore-all          Attempts to restore everything.
  -j journal             Reads an external journal from the named file.
  -b blocknumber         Uses the backup superblock at blocknumber when opening
                         the file system.
  -B blocksize           Uses blocksize as the block size when opening the file
                         system.  The number should be the number of bytes.

---

### Post by COKEDUDE on 2011-01-02
> **mc4man said:**
> **Where did you get extundelete from?** Typically when an app complains about an installed library it's either incompatible version(s) or a path issue

Edit: 
**you'd probably be better off building/installing the current source, takes all of a min. or so**
ex.

From the extundelete website. 

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

Its not in the Ubuntu or Debian repository. 

[http://packages.ubuntu.com/search?keywords=extundelete&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=extundelete&searchon=names&suite=maverick&section=all)
[http://packages.debian.org/search?keywords=extundelete&searchon=names&suite=stable&section=all](http://packages.debian.org/search?keywords=extundelete&searchon=names&suite=stable&section=all)

I tried to install it from source with no luck.

```
 ~ $ cd /home/mint/Downloads/extundelete-0.2.0
~/Downloads/extundelete-0.2.0 $ ./configure
Configuring extundelete 0.2.0
configure: error: Can't find ext2fs library

```

---

### Post by B.Bob on 2011-01-02
Install the e2fslibs-dev package - worked for me after that

---

### Post by COKEDUDE on 2011-01-03
> **B.Bob said:**
> Install the e2fslibs-dev package - worked for me after that

Yea I think you are right. This guide explains that I also need that. 

[http://www.techienote.com/2010/10/restoring-deleted-files-in-linux.html](http://www.techienote.com/2010/10/restoring-deleted-files-in-linux.html)

---

### Post by Sovello on 2011-08-04
> **COKEDUDE said:**
> From the extundelete website. 

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

Its not in the Ubuntu or Debian repository. 

[http://packages.ubuntu.com/search?keywords=extundelete&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=extundelete&searchon=names&suite=maverick&section=all)
[http://packages.debian.org/search?keywords=extundelete&searchon=names&suite=stable&section=all](http://packages.debian.org/search?keywords=extundelete&searchon=names&suite=stable&section=all)

I tried to install it from source with no luck.

```
 ~ $ cd /home/mint/Downloads/extundelete-0.2.0
~/Downloads/extundelete-0.2.0 $ ./configure
Configuring extundelete 0.2.0
configure: error: Can't find ext2fs library

```

Hello
Because you are building from source you must have the development files for ext2fs. then you need to install e2fslibs-dev, It should work fine.

---

