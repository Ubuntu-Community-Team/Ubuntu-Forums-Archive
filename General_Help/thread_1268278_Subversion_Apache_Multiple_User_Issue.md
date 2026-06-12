---
title: "Subversion Apache Multiple User Issue"
date: 2009-09-16
forum: General Help
---

### Post by davidpuzey on 2009-09-16
Hullo Ubuntu Community,

I've set up Ubuntu server 9.04 with LAMP and SSH, I also installed Subversion and linked it to Apache. I'm aiming to set this up as a project server, with each project having its own repository, thus I have used SVNParentPath when setting up SVN with Apache to specify the location I will store the repositories in. I am currently using AuthUserFile to specify a user file. I was wondering if it was possible to set up some way of allowing some user to access certain repositories and other users to access other repositories. So I can have different users for different projects (however some users should be able to access multiple projects), also I'd quite like not to have a different user file for each repository. I have looked at using AuthzSVNAccessFile and having different groups for each project, however it doesn't seem to work when using SVNParentPath (if it does then it would be great if someone could explain how to use it) only with SVNPath. I have searched around a bit on the net, but haven't managed to come up with anything useful, I hope you guys can help.

Hope that made sense,
Thanks in advance,

David

---

### Post by davidpuzey on 2009-10-06
sorry for a bump but I'd quite like an answer

---

