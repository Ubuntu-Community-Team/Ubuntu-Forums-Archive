---
title: "vim 7.2 aborts at start-up"
date: 2009-12-04
forum: General Help
---

### Post by akashiraffee on 2009-12-04
I can't use the stock ubuntu 9.10 vim, it does not include all the features I need.  So I built from source, which I have done using the exact same vim72 source many times on fedora and debian without problems.

It appears to make fine then after install:

Vim: Caught deadly signal ABRT
Vim: Finished.
Aborted

---

### Post by akashiraffee on 2009-12-04
This only happens if there is a .vimrc (even if it is empty).  It also happens whenever vim sources a runtime script, eg

:syntax enable 

will do it.

I found this launchpad question from October, which describes the exact same problem in relation to the distro package:

[https://answers.launchpad.net/ubuntu/+source/vim/+question/86350](https://answers.launchpad.net/ubuntu/+source/vim/+question/86350)

Apparently, the poster corrected the problem by downloading an *updated *version of the vim package.  This implies the ubuntu packagers were aware of it and simply hacked the source, which seems inappropriate since it is obviously NOT a vim bug.

I have tried disabling SELinux but that is not the problem.

Anyone who knows anything about this, it would be nice to hear from you ;)

---

### Post by Simian Man on 2009-12-04
> **akashiraffee said:**
> I can't use the stock ubuntu 9.10 vim, it does not include all the features I need.  So I built from source, which I have done using the exact same vim72 source many times on fedora and debian without problems.

Did you try installing the full vim package.  IIRC Ubuntu only comes with vim-tiny which is only the vi subset of vim.  Try installing *vim* and  *vim-gnome* and you will have more functionality.

If this isn't the problem, then exactly what features of vim are missing from the version in the repos?

---

### Post by akashiraffee on 2009-12-04
No, I am not using vim-tiny, I'm using vim-nox (I don't like gvim).

> **Simian Man said:**
> exactly what features of vim are missing from the version in the repos?

The first one is that it does not support server mode, whereby you have one vim open and send a file to it (eg, from the filebrowser).

**vim --remote some.file**

This can be macroed into a menu option by most filebrowsers.

That's enough to make me rebuild, since it cripples the way I use vim. 

I'll let you know if I find anymore 8-)

---

### Post by akashiraffee on 2009-12-04
Ubuntu didn't hack the vim source, vim was patched because of this.   All apologies.

For posterity, you must add the patches up to at least #44:
[http://www.vim.org/patches.php](http://www.vim.org/patches.php)

There is a gzipped single file for each set of one hundred in the ftp directory (eg. 7.2.001-100) so you do not have to do them all.

---

