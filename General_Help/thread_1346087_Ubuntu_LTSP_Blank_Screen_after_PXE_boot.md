---
title: "Ubuntu LTSP Blank Screen after PXE boot"
date: 2009-12-04
forum: General Help
---

### Post by Frogging101 on 2009-12-04
I have set up an LTSP server on Ubuntu. It has one client connected by a network patch cable. But I am having problems booting the client. When I start up the client with the cable connected, it gets an IP from the DHCP server, and then has these messages:

```
TFTP prefix: ltsp/i386/
Trying to load: pxelinux.cfg/[RANDOM STUFF, MESSAGE REPEATS]
Loading vmlinuz..................
Loading initrd.img...................................ready.
```

And after that, nothing but a blank screen. No splash screen, no cursor. NOTHING. If is press CTRL+ALT+F1, I see a small cursor at the top left, but it doesn't respond to the keyboard. If I press CTRL+ALT+DEL, the computer immediately restarts, again with no splash screen. How can I fix this?

**UPDATE:**

I'm getting a bit closer to the root of the problem. I think it has something to do with NFS. Here is my /etc/exports:
```

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
# /etc/exports #
/opt/ltsp/amd64 192.168.3.101(rw) 192.168.3.1(rw)
```

Am I missing anything? Or is NFS not the problem?

**UPDATE 2:**

Another update:

It is almost certainly the NFS, I found that the client is not accessing it AT ALL. That's why it isn't loading anything, and just displaying a blank screen. How do I fix that?

**UPDATE 3**


I found that /etc/fstab was empty (when chrooted to /opt/ltsp/amd64), could that be a factor?

---

### Post by Frogging101 on 2009-12-04
Bump. It feels like I'm the only one who never gets any answers.

---

### Post by Frogging101 on 2009-12-04
Bump. Please, I have been searching for a solution for days. I need an answer

---

### Post by Frogging101 on 2009-12-04
I'm getting a bit closer to the root of the problem. I think it has something to do with NFS. Here is my /etc/exports:
```

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
# /etc/exports #
/opt/ltsp/amd64     *(ro,no_subtree_check,no_root_squash)
```

Am I missing anything? Or is NFS not the problem?

---

### Post by Frogging101 on 2009-12-04
Bump.

I have a feeling this is a really simple solution, hence the frequent bumping.

---

### Post by Frogging101 on 2009-12-04
Another update:

It is almost certainly the NFS, I found that the client is not accessing it AT ALL. That's why it isn't loading anything, and just displaying a blank screen. How do I fix that?

---

### Post by Frogging101 on 2009-12-05
Bump.

Please, can some one help? Feels like I'm talking to myself here...

---

### Post by Frogging101 on 2009-12-05
Bump... I am completely stumped.

---

### Post by Frogging101 on 2009-12-05
Bump. This problem is one of the most perplexing problems I've ever had. If you can help, please do.

---

### Post by Frogging101 on 2009-12-05
I found that /etc/fstab was empty (chrooted to /opt/ltsp/amd64), could that be a factor?

---

### Post by Frogging101 on 2009-12-06
I managed to fix it, and I will be submitting a guide soon to help others with similar issues. For everyone that took the time to view this, thank you.

---

### Post by Dlax7 on 2009-12-11
Frogging101,

I am running into the same error as you and cannot find any other solutions on the internet to this problem.  How did you end up fixing this? If you could let me know that would be great.

---

### Post by Frogging101 on 2009-12-12
I am having a lot of problems with this. In fact, the problem is back again and I am once again stumped. sorry.

---

### Post by Dlax7 on 2009-12-13
Frogging101, 

I have found a solution that worked for me.  Go [here]("http://ubuntuforums.org/showthread.php?t=785439&page=2") and look at the #12 post and see if that solution works for you also.

---

### Post by cmcginty on 2011-01-05
Having the same problem, but the last link did not help. I'll try and post a solution when I find it.

---

