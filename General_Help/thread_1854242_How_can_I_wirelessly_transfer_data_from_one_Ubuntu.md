---
title: "How can I wirelessly transfer data from one Ubuntu laptop to another?"
date: 2011-10-04
forum: General Help
---

### Post by Ulysses1994XF04 on 2011-10-04
I just got an Asus Eee PC 1001PXD and just successfully installed Ubuntu 11.04 on it. I want to upload about 30 GB of data from my old laptop which also has Ubuntu on it (version 10.04 though) wirelessly, but I'm fiddling around with the bar on top and the icons on both computers and I can't get them to "sense" eachother. I only have a tiny 2GB USB stick and I don't want to plug and unplug them and transfer them back and forth 15x. 

How can I wirelessly transfer data from one Ubuntu laptop to another?

---

### Post by v1ad on 2011-10-04
through scp:
something like
```

scp -R username@ip:/home/username/* /home/username/folder_where_u_want_to_save

```
in terminal. just make sure you have ssh installed, if not do:
```

sudo apt-get install ssh

```

---

### Post by v1ad on 2011-10-04
[http://vikashazrati.wordpress.com/2008/02/03/quicktip-transferring-files-between-two-ubuntu-systems/](http://vikashazrati.wordpress.com/2008/02/03/quicktip-transferring-files-between-two-ubuntu-systems/)

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

[https://help.ubuntu.com/8.04/switching/preparing-storage.html](https://help.ubuntu.com/8.04/switching/preparing-storage.html)

[http://ubuntumanual.org/posts/154/copy-files-remotely-using-scp-in-ubuntu](http://ubuntumanual.org/posts/154/copy-files-remotely-using-scp-in-ubuntu)

---

