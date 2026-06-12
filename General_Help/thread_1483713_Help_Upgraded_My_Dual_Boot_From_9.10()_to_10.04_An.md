---
title: "Help? Upgraded My Dual Boot From 9.10(?) to 10.04 And No Boot..."
date: 2010-05-14
forum: General Help
---

### Post by formengr on 2010-05-14
i am not a savvy ubntu user (i'm a windows guy), but neither am i entirely in the dark...

i upgraded ubuntu from 9.10 (pretty sure it was .10...) and now my machine goes through the bios and i get a black screen w/a blinking cursor instead a boot choice to ubuntu or windows 7.  system worked fine prior to upgrade...

reading lots of things it appears i likely have a problem with grub2 (soemone correct me if i'm off base?) so i've been trying to restore and reinstall grub 2 (using this and silmilar threads for help: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)), got frustrated and reinstalled 10.04 over the upgrade install.  same blinking cursor...  :(

i did the following from this thread: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
> sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
and got this:
> /usr/sbin/grub-setup: warn: Your embedding area is unusually small.   core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.   core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be  installed in this setup by using blocklists.  However, blocklists are  UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.i've gotten that response from trying to reinstall/repair grub 2 also.

i'm near wit's end and am near completely wiping hdd and reloadng w7 OS. someone help me to save me from myself?  thanks in advance.

---

### Post by DCMR2 on 2010-05-14
don't panic. Have a look at this (and then panic)jk

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+users+guide](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+users+guide)

Oh. my bad, I see you already found it.

---

### Post by formengr on 2010-05-14
hehe. not panicing. i know there's away out (re-install w7!) but i'd like to work through this. and you linked the same link i posted 1st.  

help?

---

### Post by formengr on 2010-05-19
too much messing around... gave up and did a full reinstall of w7, then wubi. working with ubuntu 10.04 now.  now to make the nvidia drivers function...

---

