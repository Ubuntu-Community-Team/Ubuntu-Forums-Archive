---
title: "Samba share permission issue"
date: 2012-06-11
forum: General Help
---

### Post by flycast on 2012-06-11
I have the following share:
> [shared tools]
	writeable = yes
	wide links = no
	path = /mnt/home/samba/shares/sharedtools
	write list = @sharedfiles
	force directory mode = 775
	force group = sharedfiles
	force create mode = 775
	user = @sharedfiles

The folder has the following ownership:
> Owner: root
Group: sharedfiles
Others: -

The folder permissions are 775.

The user "eric" is a member of "sharedfiles" as well as other groups.

If the folder has groups "sharedfiles" and permission of 775 and I login as "eric" and eric is a member of "sharedfiles" then why are my Samba permissions read only?

---

### Post by flycast on 2012-06-11
Hmmm...Even though all the group permissions look good I cannot copy directly into that folder when I am logged in directly on the linux machine. Looks like an issue with permissions???

---

### Post by flycast on 2012-06-11
I *think* I found the issue. This was a drive used in another system. The old system was using acl's. I installed acl and removed any acl permissions on the folder recursively. Now all looks fine.

---

