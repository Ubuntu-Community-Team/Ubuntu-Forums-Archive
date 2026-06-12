---
title: "Can't install vim"
date: 2009-09-24
forum: General Help
---

### Post by QADude on 2009-09-24
Hello.

Just installed Ubuntu 7.04 (Feisty Fawn) on an old PC I had

I created a problem trying to install the full-blown version of VIM.

The VIM that comes with Ubuntu is vim-tiny, which doesn't let you do things like syntax highlighting.

So I tried to upgrade to vim-full. The command 'apt-get install vim-full' doesn't work - it fails with an error message:

**E: Couldn't find package vim-full**

I tried 'apt-get install vim'.  Same error as above -- apt-get couldn't find the package vim.

I tried 'apt-get install vim-common' and I get this message:

[B]Package vim-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vim-common has no installation candidate[/B]


Then I thought, perhaps vim-tiny is interfering with the installation of the full version of VIM.  So I did a stupid thing and removed vim-tiny so it wouldn't be in the package database: 'apt-get remove vim-tiny'.

Well vim-tiny is gone.  "vim" doesn't work anymore because the executable is no longer in /usr/bin.  But vi doesn't work anymore either.  I thought 'vi' was a default editor (maybe that's a Unix mindset).

I can't install vim-tiny again.  apt-get install vim-tiny returns the same error message as  **vim-common**.

I thought perhaps vim-tiny was on the Ubuntu installation CD.  I tried installing using  these commands:

[B]apt-cdrom add
aptitude install vim-tiny[/B]

Nope, still doesn't work.

So where can I get VIM?  I prefer **vim-full** or **vim**, rather than **vim-tiny**.  But I need an editor.  How do I get vim-full installed?

---

### Post by geirha on 2009-09-24
Ubuntu 7.04 was released april 2007, and its support ended 18 months later, october 2008. That means the repositories for that release are moved away. You should preferably install Ubuntu 8.04 LTS or 9.04, which will be supported until april 2011 and october 2010, respectively.

That being said, there's also a possibility to upgrade your current install to a supported version. See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

