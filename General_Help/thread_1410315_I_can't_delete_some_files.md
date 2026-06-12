---
title: "I can't delete some files"
date: 2010-02-18
forum: General Help
---

### Post by freechiru on 2010-02-18
I attempted to install the e-book software calibre ([http://calibre-ebook.com/](http://calibre-ebook.com/)), typing the code they give there into the terminal ( sudo python -c "import urllib2; exec urllib2.urlopen('http://status.calibre-ebook.com/linux_installer').read(); main()" ). 

However, when I try to run it (with the command "calibre") I am told I don't have permission to access one of the folders.  When I "sudo calibre", I am told that I don't have GLIBC 2.09.  The calibre website mentions that this might be a problem, and its solution is to download an older version and replace the new version files with the old ones.

HOWEVER, I don't have permission to delete, move, or do anything to the files (I have tried sudo rmdir) -- apparently I am not the owner (who is listed as "root").  It's now installed twice on my computer and seemingly can't be removed.

Could anyone suggest a stronger method of deletion?  Unless someone knows how to make my GLIBC, whatever that is, better.  Thank you.

---

### Post by jamesisin on 2010-02-18
You can take ownership of the files in question using the chown command:

```
sudo chown -R usergroup:username /path/to/folder
```

---

### Post by SuperSonic4 on 2010-02-18
rmdir only removes *empty* directories

```
sudo rm -rf calibre
``` will remove the folder calibre and it's contents.

---

### Post by freechiru on 2010-02-18
@ SuperSonic4: I don't know my coding...  >_<  Sadly, though, that didn't delete it -- the file doesn't show up when I "ls"any more, although it's definitely still there (unless I'm looking in a different place with the visual display thing), and that command doesn't delete it.

@ jamesisin: I was told -r was an invalid option...

Thanks.

---

### Post by jamesisin on 2010-02-18
My bad:

```
sudo chown -R usergroup:username /path/to/folder
```

---

### Post by freechiru on 2010-02-18
My bad, I wasn't looking in the right place.  It's gone now.  Thanks for your help!

---

### Post by colobix on 2010-02-18
YOu could try wiht root access. works for me
```
sudo su root
```

---

### Post by jamesisin on 2010-02-18
Sure.  Under Applications &#8212;> System Tools there is a Root Terminal too.

Probably not a good solution most of the time though due to the raw potential destructive power of running as root.

---

### Post by AlanR8 on 2010-02-18
The other way of deleting file you don't have permission to delete is to open Nautilus as Root. Then you can delete ANYTHING, so use with care!

> gksudo nautilus or sudo nautilus

will open Nautilus as Root

Fill your boots!

---

