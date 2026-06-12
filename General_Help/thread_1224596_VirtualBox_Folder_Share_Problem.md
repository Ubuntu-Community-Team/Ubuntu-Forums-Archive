---
title: "VirtualBox Folder Share Problem"
date: 2009-07-27
forum: General Help
---

### Post by tyblogger5 on 2009-07-27
HELP!  I am trying to enable a folder share on my VirtualBox Ubuntu System.  But I'm having a hard time, any ideas on how to do it so you can read AND write.:confused:

---

### Post by loomsen on 2009-07-27
Choose a folder with write permissions to be the shared one. For example, create a folder 
~/vbox-shares
and change the permissions to rwx for everyone. 
```

chmod -R a=rwx ~/vbox-shares
```

Note: doing this will add write permissions for anyone, this is the user, the group and others!

---

### Post by GodsMadClown on 2009-08-07
How can I thank this guy?  I had my virtualbox running under a dedicated user (vbox), but the directory I was trying to share on the host was owned by my primary user (bill).  Adding global write privileges took care of the problem.

The path that you're trying to share needs to be writable by the user running the virtualbox.

---

