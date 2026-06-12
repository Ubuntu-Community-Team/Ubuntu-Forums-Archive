---
title: "Trouble with mount.cifs while smbclient works (12.04)"
date: 2012-05-14
forum: General Help
---

### Post by texastwister on 2012-05-14
Just upgraded to Precise and am working to restore access to the windows shares I use at work.  

smbclient connects immediately: 
```
sudo smbclient //pc1n7i01d03.us.dell.com/dttuatnas2 -A /etc/.smb_creds.txt
```

mount.cifs fails (with "mount error(13): Permission denied"): 
```
sudo mount.cifs //pc1n7i01d03.us.dell.com/dttuatnas2 /mnt/ -o credentials=/etc/.smb_creds.txt
```

my credentials file is as follows (with the proper values, of course):

```
username=mynamehere
password=password
domain=MyDomain
```

I remember on a previous occasion having resolved a problem by including a mount option "noserverino".  I've tried that to no effect.  I've also tried "sec=ntlmv2"

The syslog contains this message in response to each failed attempt:

```
CIFS VFS: cifs_mount failed w/return code = -13
```

I'm baffled and appreciative of any suggestions you can provide.  Thanks in advance.

---

