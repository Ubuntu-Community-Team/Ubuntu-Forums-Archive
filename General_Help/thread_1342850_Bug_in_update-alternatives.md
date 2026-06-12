---
title: "Bug in update-alternatives?"
date: 2009-12-01
forum: General Help
---

### Post by linucks42 on 2009-12-01
Hi,

I'm trying to change the default editor from nano to vi and get the following:

me@mypc: sudo update-alternatives --set editor /usr/bin/vi
update-alternatives: using /usr/bin/vi to provide /usr/bin/editor (editor) in manual mode.
Can't call method "slave" on an undefined value at /usr/sbin/update-alternatives line 1017.

This is on Kubuntu 9.10

It seems something so basic that I'm wondering whether I'm doing something silly or whether I should file this as a bug?


Thanks!

Jens

---

### Post by Migrus on 2009-12-06
Had the same problem trying to change from gcj to sun's java. Error message is not the best... 

What you need to do is provide one of the paths that update-alternatives knows about. You can list the known alternatives using the "list" command. For me that gives:

[FONT=Courier New]# update-alternatives --list editor
/bin/ed
/bin/nano
/usr/bin/emacs22
/usr/bin/vim.basic
/usr/bin/vim.tiny
[/FONT] 
And the following command works:
[FONT=Courier New]# update-alternatives --set editor /usr/bin/vim.basic[/FONT]

($fileset is undefined in 'sub prepare_install' if someone wants to report it properly)

---

### Post by linucks42 on 2009-12-06
Thanks for that Migrus - it worked fine when I tried what you suggested.

The error message could definitely be more informative!

Thanks,

Jens

---

