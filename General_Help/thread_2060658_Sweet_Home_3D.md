---
title: "Sweet Home 3D"
date: 2012-09-20
forum: General Help
---

### Post by mtmigs on 2012-09-20
The current release of Sweet Home 3D is version 3.6 but Ubuntu Software Center loads version 3.4. Version 3.4 has problems loading a design created or modified by version 3.6. So we are having problems sharing files between the windows (version 3.6), Mac (version 3.6), and Ubuntu (version 3.4).

When a new version of Sweet Home 3D is released who migrates that version to the Ubuntu Software Center and possibly the Update Manager?

I put a message on the Sweet Home 3D forum and they said I should post the question here.

---

### Post by jerrrys on 2012-09-20
Looks like you can just download from a couple of sources.

[http://www.getdeb.net/software/Sweet%20Home%203D](http://www.getdeb.net/software/Sweet%20Home%203D)

[http://sourceforge.net/projects/sweethome3d/files/SweetHome3D/SweetHome3D-3.6/](http://sourceforge.net/projects/sweethome3d/files/SweetHome3D/SweetHome3D-3.6/)

As for the software center, don't know.

---

### Post by mhall119 on 2012-09-20
Somebody can submit the latest version to Ubuntu's Backports repository, or they can use a PPA to make it available.  In the future, we will have a process that will let the authors submit the latest version directly to the Software Center

---

### Post by cariboo on 2012-09-22
This really has nothing to do with creating programs for Ubuntu. Moved to General Help.

To answer your question, create a bug report agaunst the package in the repositories, and ask for it to be updated. The devs normally don't monitor the forums, so creating a bug report is the best way to ask about updating a package. To create the bug open a terminal of press Alt-F2 and type the following command:

```
ubuntu-bug sweethome3d
```

Of course you have to have a [launchpad]("https://launchpad.net/") account to create a bug report

---

