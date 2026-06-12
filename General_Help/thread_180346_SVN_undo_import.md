---
title: "SVN undo import"
date: 2006-05-22
forum: General Help
---

### Post by jazzgossen on 2006-05-22
This is not specifically Ubuntu related, but I hope somone here can help me anyway.

Is there any way to undo an import to an SVN repository? Every now and then when I import new stuff to the SVN rep where I store different projects, I either import stuff to the wrong place, or forget to not import big binary files that shouldn't be in the repository. 

Does anybody know if there is a way to undo these actions? I can of course do "svn rm xxx" and check the stuff in again, but that will still leave the files in the repository, right?

---

### Post by gerbman on 2006-05-22
[QUOTE=jazzgossen]I can of course do "svn rm xxx" and check the stuff in again, but that will still leave the files in the repository, right?[/QUOTE]Yup. The only thing I can think of is to recreate the repository using the current version. Of course, you would lose your revision history. There's probably a more elegant solution, maybe in the SVN [book]("http://svnbook.red-bean.com/").

Good luck.

---

