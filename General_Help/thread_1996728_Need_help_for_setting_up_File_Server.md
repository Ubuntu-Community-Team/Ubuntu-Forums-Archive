---
title: "Need help for setting up File Server"
date: 2012-06-04
forum: General Help
---

### Post by GCisking on 2012-06-04
Hello Everyone,

First i would like to introduce myself my name is Guian i live in The Netherlands and i'm 23 years old.

I have a school project that i need to set up .
 Windows 2008 server Domain Controller and member server
 Ubuntu 11.04 (File Server)
 Windows 7 client
Due to lack of experience in Ubuntu OS, I need help to set up a file server. 
My question is:
  How can i configure in Ubuntu  that allow windows domain user to have access there shared folders?
  Do i need to set up an ntfs partition, if so how can i make the permission so that everyone can access?
  And last how can i set up a permission that Group1 have the  access to that folder and not Group2.

what i want to do is:
I've created Groups in windows. 
        Group 1 = members are user1 and user2
        Group 2 = members are user3 and user4
I want is that user 1 and 2 have the access in Group1 shared folder, but only user 1 have the full permission user 2 can only read and write. In Group2 both user have only read  and write permission but  user1 have permission to access in Group2 shared folder.
Ubuntu OS is already joined the Windows domain, also created as shared folder but i cant create new file due to the permission.

Sorry that i asked too much and my grammar are terrible. I hope you all can understand my questions.


Thank you all every much

---

### Post by nj_peeps on 2012-06-04
This is a pretty good howto,
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

After Samba/Winbind is setup, you can create shares and use AD accounts for access control.

You only have to do the PAM section if you plan on using AD accounts to admin the box (ie: ssh, desktop login, etc)

---

### Post by GCisking on 2012-06-04
Thank you for your reaction.

1 thing do i need to configure Keberos Realm?

---

### Post by nj_peeps on 2012-06-04
Yes, you would need to to do the Kerberos join, for for AD user authentication to happen correctly.  Active Directory uses Kerberos to encrypt auth data that is travelling on the network, to make it secure.

If you do not want to do this part, you could use an LDAP bind, but from my experience, it's harder to do it that way, and you would need to create a service account, with permissions to do lookups, for the ubuntu box to use to do the LDAP lookups.

---

