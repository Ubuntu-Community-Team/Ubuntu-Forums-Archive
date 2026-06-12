---
title: "vi and emacs issue"
date: 2009-11-25
forum: General Help
---

### Post by Diametric on 2009-11-25
Hello All,

Some years ago I purchased a RedHat 9 book and am now beginning to work my way through it.  I've just installed Ubuntu and am at the section in the book where text editors are being addressed.  I was able to launch VIM and work through that, but I can't seem to launch an emacs session.  My question is this:

1.  If emacs is installed, how is it accessed?  When I attempt to run emacs, e3, emacs22, emacs23 etc, I get a prompt suggesting I install various packages.  If I do need to install a package, would someone be so kind a to walk me through that? I've never installed 3rd party apps on a Linux distro.

2.  I would like the ability to run the original vi if possible.  We use it at work, and I would like to focus on the editor.  Not a huge deal, but it would be nice to get some info on this.

So, if it's an issue of simply accessing existing files via the shell, how are they accessed (I have a decent command line lexicon)?  If it's a 3rd party install, I might need a bit of hand holding.

Thanks in Advance,
-Diametric

---

### Post by Brandon Williams on 2009-11-26
> **Diametric said:**
> 
1.  If emacs is installed, how is it accessed?  When I attempt to run emacs, e3, emacs22, emacs23 etc, I get a prompt suggesting I install various packages.  If I do need to install a package, would someone be so kind a to walk me through that? I've never installed 3rd party apps on a Linux distro.


You're not going to install 3rd part apps. emacs is part of standard Ubuntu; it just isn't installed by default. When you try to run it, the instructions that are output telling you about the missing app also tell what you need to do to install it. It should be something like:
```
sudo apt-get install emacs22
```

If you only want to run it in a console, you might want this instead:
```
sudo apt-get install emacs22-nox
```

> **Diametric said:**
> 
2.  I would like the ability to run the original vi if possible.  We use it at work, and I would like to focus on the editor.  Not a huge deal, but it would be nice to get some info on this.


When you say 'the original vi', do you simply mean that you want a version of vi with the same functional limitations as the original vi? If you use the -C command line switch for vim, it will run in 'compatible' mode, which will give you mostly what you want.

---

