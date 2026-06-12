---
title: "folder creation permissions denied"
date: 2011-01-11
forum: General Help
---

### Post by Pedroparamo on 2011-01-11
I'm trying to  create a folder using the archive manager to install Resin (web server)  in the usr/local folder but I get the error message 'error creating  directory: Permission denied.'  

Is this the easiest way to install an app--by using the Archive Manager--and if so how do I establish the correct permissions.

Pedro Paramo

---

### Post by tredegar on 2011-01-11
You need to be root to install anything to **/usr/local**

So either do that or install it to your home directory.

I don't think you'll get far with resin, or linux, until you have read about and understood linux file permissions and just exactly what "Permission Denied" *means*.

Here's a [link]("http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/file-permissions.html") to get you started, but search-engines are your friend.

---

