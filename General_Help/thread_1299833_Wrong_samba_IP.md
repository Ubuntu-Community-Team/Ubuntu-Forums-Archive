---
title: "Wrong samba IP"
date: 2009-10-24
forum: General Help
---

### Post by peardox on 2009-10-24
I was looking for the answer to this earlier and found only an archive so I'm forced to make a new post

The problem is with Samba (sometimes) having the wrong IP for a share

There are two solutions

1) Don't try mounting //<machine name>/share instead mount //<machine IP>/share

Sadly (1) only works if you do permanent mounts

This method fixes everything...

2) Edit /etc/samba/lmhosts (hope its here on Ubu, using Centos)

Add a line to it to the file like this

<Machine name> <space> <Machine IP>

e.g. (from my server setups)

Fuji 10.1.1.123

This will only work with static IPs

This should fix you

You can verify this by logging in as the same user as has the share then typing smbtree, give it your password for the share and you should see all the shares listed

You'll need to restart samba or the machine to let it pick this up (I think nmbd uses is)

Hope this is useful

---

