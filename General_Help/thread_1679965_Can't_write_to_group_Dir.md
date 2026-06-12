---
title: "Can't write to group Dir"
date: 2011-02-01
forum: General Help
---

### Post by rslaqui on 2011-02-01
Hi  I'm a newbee trying to setup a common dir for many users:

I have done:

sudo groupad webdevelopers
sudo useradd -G webdevelopers me

sudo mkdir /test
sudo chgrp -R webdevelopers /test
sudo chmod g+s /test

sudo chmod 775 /test

So: ls -la at / shows:
drwxrwsr-x   2 root webdevelopers  4096 2011-02-01 17:18 test

and: groups me shows:
me : me adm dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin admin sambashare webdevelopers

---- so since the dir is owned by webdebelopers group and the user me is part of the webdevelopers group 
I thought I'll be able to write at the dir /test
but vi /test/hi.txt can't save on :wq

What I did not get?
What I did wrong?


Thanks a lot.

---

### Post by sisco311 on 2011-02-01
Did you start a new login shell as user *me* after adding it to the new group?

---

### Post by rslaqui on 2011-02-03
Nop, that was it thanks a lot.

---

