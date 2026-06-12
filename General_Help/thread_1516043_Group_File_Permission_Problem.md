---
title: "Group File Permission Problem"
date: 2010-06-23
forum: General Help
---

### Post by Wittaker on 2010-06-23
So I have two main users I'm running on my ubuntu server installation, my administrator and a guest account I route all my CIFS traffic through. I've used webmin to set up most of this.

I log in to the administrator account through VNC since I'm not entirely comfortable with only using the command line to adminster the system. I also run ktorrent while using vnc since the GUI is intuitive and familiar.

The problem is that all the files downloaded by ktorrent are owned by my administrator account, but I want my guest samba user to be able to move them around and delete them too. I've changed the primary group of both accounts to "users" which allows my samba user to read the files, but not move or write to them.

How could I go about making sure both users can read, write and delete the same files?

Keep in mind that my knowledge of ubuntu is somewhat limited. I've been using guides for the most part to set up this server.

---

### Post by bkline on 2010-06-23
> **Wittaker said:**
> ... How could I go about making sure both users can read, write and delete the same files?

The group read flag controls whether those users can read the files.  The group write flag similarly lets the users write to the files.  The group write flag for the parent directory controls whether the users can delete the files in that directory (including files for which they don't have write permission), as well as add files to that directory.  So in order to be able to move a file, the group write flag would need to be set for both the source directory and the target directory.

HTH

---

### Post by Wittaker on 2010-06-23
Thanks for the reply, I'll try to figure out how to do that on my own. If I can't, I'll post back here.

---

