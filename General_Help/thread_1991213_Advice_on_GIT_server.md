---
title: "Advice on GIT server"
date: 2012-05-30
forum: General Help
---

### Post by obatron on 2012-05-30
I have a project to create a git server for a large number of students.   Each student would have one or more repositories whom they would share access to selected other students on a project by project basis.  (they determine who they wish to share them with.)   i.e. Different repositories will have different access lists.

My vision is to create a server with an NFS mounted data store.   Install git and gitolite.   Users would clone their project to the server setting the access permissions per gitolite.   They would also be able to view their repositories (as well as the users who they've shared access with) via the git web page.    They would not see or have access to other repositories.

I'd rather not allow shell access to the server as they will begin to use it as a computational server (and of course, attempt to hack it to pieces trying to steal each other's stuff as well as compromise the system.)   

I thought I would see if anyone else had done something like this and if there were anything I should be mindful of or best practices when doing this.

Thanks!
Bob

---

