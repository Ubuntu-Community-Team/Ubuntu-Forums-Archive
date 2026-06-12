---
title: "Samba sharing and password sync"
date: 2006-01-30
forum: General Help
---

### Post by olale on 2006-01-30
Hi!

I didn't get Samba sharing to work out of the box with Kubuntu Breezy, so I thought I'd through in some notes about how I solved some issues that others may have encountered as well.

I have a linux box with files that I want to use from my Mac. The easiest way to do this as I saw it was to install the samba packages and then just right-click on a folder and select "share". 

This didn't do the trick for me however, since I was rejected when I tried to access my machine from the Mac as an anonymous user. The problem seemed to be that first of all, there are no specific users that are allowed to access the Samba share, though nothing was noted about this in the interface for sharing folders. Also, in /etc/samba/smb.conf there is a line about "passdb backend" that seemed to cause some problems for me even after I enabled users to access the machine.

Therefore, the short solution for me was to first add some of the local users as samba users, with 

# sudo smbpasswd -a user
<enter samba password twice>

After this, I also had to comment out, using ";", the line containing "passdb backend" in smb.conf. After this I managed to connect from my Mac.

There is still one issue left to resolve, and that is to sync the passwords between Samba and Linux. The smbpasswd is supposed to be able to handle this if  "unix password sync = yes" is in smb.conf. However, with this option smbpasswd hangs after I have entered my new samba password and there is an error 

```

# smbpasswd
Old SMB password:
New SMB password:
Retype new SMB password:
cli_pipe: return critical error. Error was Call timed out: server did not respond after 20000 milliseconds
cli_oem_change_password: Failed to send password change for user olale
machine 127.0.0.1 rejected the password change: Error was : Call timed out: server did not respond after 20000 milliseconds.
Failed to change password for user
```

Anyone know what this is all about?

---

### Post by mlomker on 2006-01-31
I don't have first-hand knowledge, but I did a Google search.  [This post]("https://www.redhat.com/archives/redhat-list/2004-December/msg00424.html") suggests commenting out the line with 'pam password change = no', although that appears to be the default.

---

### Post by olale on 2006-02-02
Hi!

Unfortunately it didn't do the trick. Ah well, one of those quirks I'll have to live with I guess. If only Konserve could work for me then there wouldn't be any serious nuisances at least..

---

