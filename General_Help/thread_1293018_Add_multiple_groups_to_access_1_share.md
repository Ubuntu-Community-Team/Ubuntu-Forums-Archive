---
title: "Add multiple groups to access 1 share?"
date: 2009-10-16
forum: General Help
---

### Post by Roasted on 2009-10-16
I don't mean to compare to Windows, but with Windows you can add more than 1 group to have certain permissions to a folder on the network.

That way with say, "Public" I can add all of the groups accordingly to have access to that folder, such as Guidance, Office, Administration, Teachers, etc.

In Ubuntu, all I can see doing is adding 1 group to have access to the share. How can I set up multiple groups to have access to a folder with the same setup like I described above WITHOUT opening permissions to 777?

---

### Post by bodhi.zazen on 2009-10-16
Easiest way in Linux is with ACL :

[http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13)


There is a GUI for ACL if you wish

If you want a GUI interface, use Eiciel, it is in the repositories

[http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html](http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html)

---

### Post by Roasted on 2009-10-16
How exactly does this work? If I make a bunch of changes in the ACL program and then run ls -l on the directory, what will I see?

---

### Post by bodhi.zazen on 2009-10-16
> **Roasted said:**
> How exactly does this work? If I make a bunch of changes in the ACL program and then run ls -l on the directory, what will I see?

you will not see them with ls -l

See : [http://www.enterprisenetworkingplanet.com/netsysm/article.php/3077971](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3077971)

---

