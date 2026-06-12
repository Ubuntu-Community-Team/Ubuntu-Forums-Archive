---
title: "Links in /home"
date: 2009-12-28
forum: General Help
---

### Post by steveM49 on 2009-12-28
I'd like to set up my /home directory to a different drive from the / directory.  I thought that I'd be able to issue a command like: 

sudo ln -s /mnt/sdb1/home/username /home/username

I set up the links first, then tried to create the user.  The user manager refused to use an existing /home directory for username.  I then rm the link, set up the user and tried again with the link. Now it links to a new file home/username/username.

This seems like the kind of thing people would be doing all the time.  What am I doing wrong?

Steve

---

### Post by scragar on 2009-12-28
Why are you linking it? Just set it up as a new partition to be mounted on /home and leave it at that.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

EDIT: You're using a different drive, don't resizing any partitions, you're good to skip that part.

---

### Post by steveM49 on 2009-12-29
Not quite what I wanted to do.  But it had the right effect.  Thanks.

Steve

---

