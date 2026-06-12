---
title: "Run program to check programs dependencies"
date: 2011-05-18
forum: General Help
---

### Post by slooksterpsv on 2011-05-18
I'm not talking about like:

apt-get check

I mean it's like, and I thought it was this:

valgrind <application>

Needs:
x
y
z

Does anyone know what I'm talking about? A lot of programs I'm getting segmentation faults like Rhythmbox, a few games, etc. so I dunno.

EDIT: gdb kind of works, but doesn't show me what another program would... hmmm

---

### Post by hulkman on 2011-05-20
Enter the following command into the terminal to see a packages information including dependencies:

 dpkg --info package.deb

The following command will also resolve dependencie issues many times:

sudo apt-get -f install

-----------------------
[http://www.dotdeb.com](http://www.dotdeb.com)

---

