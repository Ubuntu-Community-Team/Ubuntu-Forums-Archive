---
title: "Can't Update"
date: 2010-07-01
forum: General Help
---

### Post by fjgaude on 2010-07-01
My Ibuntu 10.4 system can't be updated because of error message:

"Segmentation faulty tree"

coming from **apt-get check**. It reads 50% of then stops. It shows reading the package lists, the Done.

Any help, please!

---

### Post by sisco311 on 2010-07-02
According to this thread: [thread]19563[/thread]
you have to remove the .bin files from apt's cache (/var/cache/apt/).

EDIT: a recent blog post with some explanation: [http://tfpettingill.com/blog-dev/2010/06/installation_of_ubuntu_linux_1.html](http://tfpettingill.com/blog-dev/2010/06/installation_of_ubuntu_linux_1.html)

---

