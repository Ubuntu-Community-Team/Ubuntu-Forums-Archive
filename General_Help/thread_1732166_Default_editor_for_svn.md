---
title: "Default editor for svn"
date: 2011-04-17
forum: General Help
---

### Post by bob_75 on 2011-04-17
I am using Ubuntu 10.10. When I do svn commit it brings up emacs gui. (I didn't like nano so I changed it using some random tutorial online) I would like it to be emacs -nw but for some reason, it just won't do it. What do I change/edit so that svn commit always brings up emacs in nw mode? (shell mode?)

Thanks much.

---

### Post by jpkotta on 2011-04-20
> **bob_75 said:**
> I am using Ubuntu 10.10. When I do svn commit it brings up emacs gui. (I didn't like nano so I changed it using some random tutorial online) I would like it to be emacs -nw but for some reason, it just won't do it. What do I change/edit so that svn commit always brings up emacs in nw mode? (shell mode?)

Thanks much.

I do it with the EDITOR environment variable.  Put this in your ~/.bashrc:
```
export EDITOR="emacs -nw"
```

Apparently, Subversion looks at the SVN_EDITOR variable too.  [http://svnbook.red-bean.com/en/1.5/svn-book.html#svn.advanced.externaleditors](http://svnbook.red-bean.com/en/1.5/svn-book.html#svn.advanced.externaleditors)

---

