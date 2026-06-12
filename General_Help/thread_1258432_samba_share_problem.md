---
title: "samba share problem"
date: 2009-09-05
forum: General Help
---

### Post by alphaniner on 2009-09-05
I have two machines running 9.04.  One has samba-server installed and some shares set up through Nautilus.  One shared folder is rwxrwxrwx with guest access, the others rwxr-xr-x.  I can write to the guest access folder, and if I logon with smbclient and enter the server password, copied files get the appropriate ownership.

However, while I can logon (smbclient) and mount (mount.cifs) the restricted shares with no problem, I don't have write access.  I get the error 'NT_STATUS_ACCESS_DENIED opening remote file'.  The user is the same on both machines, but I have also tried defining it explicitly (ie. using '-U alphaniner' with smbclient).  Is this right?

---

### Post by jnorthr on 2009-09-05
what you see looks ok to me. As i understand it, a permissions setup of rwxr-xr-x does not allow write access because the '-' shows it does not. Since write access is not allowed for either group or user, just for super-user as declared here, you could try changing the permissions settings for folder you want to share from rwxr-xr-x to rwxrwxrwx.
:)

---

### Post by alphaniner on 2009-09-05
I think you misunderstand.  The owner of all the shared folders is me (alphaniner), not root.  So, when I login or mount with alphaniner's credentials, shouldn't I have write access?  Changing the permissions to rwxrwxrwx is something I want to avoid.

---

### Post by jnorthr on 2009-09-05
sorry - think i did miss the point. it's a little early here.:rolleyes:

i would have expected to need the same owner on all folders on both ends of the wire/wireless with identical permissions settings. Your user profile may not be a 'super-user' so might not have all the abilities you think it does. I'd try using sudo access before your commands to look like the system administrator. Then retry. Still have a gut-feeling you are going to need write permission on the target folder b4 this will work.

---

### Post by alphaniner on 2009-09-05
Ownership and permissions are identical on both sides of the connection, ie:

drwxr-xr-x 2 alphaniner alphaniner

It just doesn't make sense to me that logging on as the owner of a folder doesn't give me permission to write to said folder...

---

### Post by jnorthr on 2009-09-05
As a temporary test, could you change the write permissions, then rerun your tests to confirm this is really a 'write' issue not a 'user profile' issue. You can always change the permissions back to what they were originally.

---

