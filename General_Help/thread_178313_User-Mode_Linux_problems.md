---
title: "User-Mode Linux problems"
date: 2006-05-17
forum: General Help
---

### Post by hewhocutsdown on 2006-05-17
Tried to figure this out via internet/emailed the author of the article I was working off of, and the message delivery has failed.

Anyone used UML enough to know where my missing /usr/bin/linux file is?

(original message clip)
I was following through on your article here
([http://www-128.ibm.com/developerworks/edu/l-dw-linuxuml-i.html](http://www-128.ibm.com/developerworks/edu/l-dw-linuxuml-i.html)) and I
hit a stumbling block: in Section 4, I noticed that the command '$
./linux' yielded a 'bash: ./linux: No such file or directory'

On further examination, I discovered that, while I created a link to
/usr/bin/linux, there was no such thing as /usr/bin/linux. In fact, a
search found that nowhere in my /usr/bin directory or subdirectories
was there any reference to 'linux'.

I'm running Ubuntu (a Debian-based distribution) the development
version (codenamed Dapper Drake), so I'm not sure if perhaps this is a
Debian idiosyncracy, I haven't been able to find the answer on the net
as of yet.

---

### Post by hewhocutsdown on 2006-05-25
Fixed it....it helps if you install more than the docs and utilities packages. Used debian's user-mode-linux package.

---

