---
title: "Can you think of a better way?"
date: 2006-03-26
forum: General Help
---

### Post by Dankitymao@gmail.com on 2006-03-26
Hello!

 So, I have this Ubuntu Linux fileserver (which runs wonderfully and is quite simple to administer), for my roommate and my friends to use as a sort of private .Mac-style net-accessible storage space.  Currently, the setup is a bit odd, as I don't have a good idea of the possible gamut of servers that could be used to accomplish this; NFS is used for connections on the internal NAT (basically, to my Mac, my Ubuntu laptop, and my roommate's Mac), and SFTP is used for connections from the outside.  I tried to get NFS to successfully allow connections from the outside, but didn't get it to work right away, and didn't try too hard because I read that there were many security concerns about using NFS in such a way.

So, now that I've described the setup a bit, my question is this: What would be a way to improve this setup?  I'd like even external connections to have a mountable-disk type connection (like NFS, or even Samba/CIFS style), if possible, but don't know anything other than NFS to achieve this with...or how to secure NFS for use in this fashion.  It would have to be usable by Windows, Linux, and Mac users alike, since my friends run the gamut of OS preferences.  

Any ideas?  Thanks so much for any suggestions!

~DM

---

### Post by barfos on 2006-03-26
Well, are there a finite number of friends you want to give access to?  Or  is this intended for anyone to use anonymously.

In the anonymous case you might want ftp.

Although NFS doesn't let you restrict who can mount the share by user/pass, you can say "just allow this and this remote machine" by domainname.  This probably isn't good in the anonymous case. Or else you'll have millions of people mounting your share. 

The most widely supported on all platforms would be SMB, but I don't think it was designed to go over the entire internet.

---

### Post by Dankitymao@gmail.com on 2006-03-26
There is a definite (short) list of who has access.  Currently, said access is controlled by SFTP login/password, but I'm not opposed to implementing an IP-based access control list or something if there is a better solution that uses such...or even RSA key access, which I know can be done through SSH/SFTP, but I don't know if it can be used for NFS (maybe by giving the public key to those I want to have access?)...

---

