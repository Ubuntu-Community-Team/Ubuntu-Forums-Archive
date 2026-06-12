---
title: "Grub&gt; uuid - Error 27: Unrecognized command?"
date: 2012-01-08
forum: General Help
---

### Post by 2CV67 on 2012-01-08
Even after installing the most recent version of Legacy Grub proposed by SynApt for Ubuntu 10.04 LTS (0.97-29ubuntu60.10.04.2), if I open a grub terminal & try "grub> uuid" I still get "Error 27: Unrecognized command" where I would expect to see a list of my partition uuids.

Is that normal or not?

Is there an explanation or diagnosis or fix?

Note: I already mentioned this in another thread, but maybe it got lost in that jungle, hence this specific question.

Thanks!

---

### Post by speed32219 on 2012-01-08
I never used that, have you looked in a file you created "uuid"?

To look at my partitions and UUID's, I run the command "sudo blkid".  Maverick 10.10.

IF you want to save them do:  sudo blkid > UUID_1_07_12

---

### Post by oldfred on 2012-01-08
The grub command line has few commands. To see UUID's use speed32219's command from Ubuntu terminal.

grub legacy commands
[http://www.gnu.org/software/grub/manual/legacy/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands](http://www.gnu.org/software/grub/manual/legacy/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands)
[http://www.centos.org/docs/5/html/Installation_Guide-en-US/s1-grub-commands.html](http://www.centos.org/docs/5/html/Installation_Guide-en-US/s1-grub-commands.html)

grub2 commands:
[http://www.gnu.org/software/grub/manual/grub.html#Command_002dline-and-menu-entry-commands](http://www.gnu.org/software/grub/manual/grub.html#Command_002dline-and-menu-entry-commands)

---

### Post by 2CV67 on 2012-01-08
I didn't dream this up - I got it from my all-time favourite site - Herman's Dual-Boot site.

He mentions it at least twice:
[http://members.iinet.net.au/~herman546/p15.html#root](http://members.iinet.net.au/~herman546/p15.html#root)
[http://members.iinet.net/~herman546/p15.html#cli](http://members.iinet.net/~herman546/p15.html#cli)

> You can also use the 'uuid' command from GRUB's Command Line Interface to get a list of file system UUID numbers 'on the fly' and then boot,
For example,
grub> uuid
(hd0,0) ext3 79a5a0ce-499e-4738-9d9b-60590f1b83fe
(hd0,1) ext3 6178d387-9ab5-4f23-a56d-8e0cba0addc3
(hd0,3) reiserfs 4d4939f2-de30-438a-896f-af6a77406eea

---

### Post by oldfred on 2012-01-08
I have always relied on Herman's site, so it must then work. I do not have old grub anymore to test myself. 

Ubuntu has made some changes to old grub legacy to work with ext4, so maybe they changed some other things?

---

