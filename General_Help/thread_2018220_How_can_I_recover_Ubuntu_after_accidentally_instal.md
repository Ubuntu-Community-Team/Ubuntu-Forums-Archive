---
title: "How can I recover Ubuntu after accidentally installing another distribution over it?"
date: 2012-07-06
forum: General Help
---

### Post by it4update on 2012-07-06
I had Ubuntu 10.10 with a sound card problem, and decided to  install another distribution to solve it. I tried to tell the new distro  to install to another partition, but I must have made a mistake because  it installed *over* my existing Ubuntu.
  Is there a way to recover all my data? I'm especially interested in the contents of my former home directory.i want to recover every thing and folder name [U][B].
any suggestion will be appreciated .[/B][/U]

---

### Post by westie457 on 2012-07-06
Hi. Your best chance here is to use 'testdisk' running in a LiveCD environment to recover the previous partition layout. Testdisk is available in the repo's. 

Full instructions are here. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

There is also 'photorec' which comes with testdisk which can be used to recover files  (not partitions) and will require another hard drive to write the recovered files to.

There are no guarantees that you will recover anything, it is worth having a go at it though.

---

