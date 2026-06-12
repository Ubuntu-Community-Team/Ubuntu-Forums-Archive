---
title: "Seem to have lost tab-to-complete in bash on Lucid"
date: 2012-04-12
forum: General Help
---

### Post by pepsifx357 on 2012-04-12
I was playing around with my /home folder, which might have something to do with it.  Right now, I can't tab to complete unless it is in refference to a folder.

So if I run:

```
sudo apt-get install firef
``` then hit the tab key, nothing happens, no matter how many times I hit it.

Now if I just do a:

```
sudo apt-get install
``` then hit tab twice, I get a list of all of the folders in my /home/ben/ folder.

I have a file server that is serving me a /home file to replace the one on my computer.  I just copied my directory to the one on the server.  Not sure if that has toooo much to do with it. :)

Any ideas?

Thanks,

Ben

---

### Post by Rodney9 on 2012-04-12
Some of these ideas may help-

[http://ubuntuforums.org/showthread.php?p=11778710](http://ubuntuforums.org/showthread.php?p=11778710)


Rodney

---

### Post by pepsifx357 on 2012-04-13
Thanks for the info, but they didn't work.

Hate to give up, but I'm long overdue for a format and start over.

---

### Post by pepsifx357 on 2012-04-15
> **pepsifx357 said:**
> Thanks for the info, but they didn't work.

Hate to give up, but I'm long overdue for a format and start over.

Ok...so that didn't work.  And now I have a better understanding of the problem.

I have a /HOME nfs share on a FreeNAS server that I am using when I format my computer.

The autocomplete works before I attach the share.  I can't understand how it broke in the first place.

Which files should I be looking at to fix?  Obviously something in my home folder.

---

