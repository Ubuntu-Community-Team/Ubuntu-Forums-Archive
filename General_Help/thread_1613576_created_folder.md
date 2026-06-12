---
title: "created folder"
date: 2010-11-04
forum: General Help
---

### Post by franku2011 on 2010-11-04
I been try figured to give a user ability to c without give them root privalage 


How do I do this?


Thanks in advance

---

### Post by sisco311 on 2010-11-05
What?

Check out this links about Unix/Linux file permissions:
[uhelp]community/FilePermissions[/uhelp]
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by franku2011 on 2010-11-05
I reposted my question sorry for the typo

I want now how I can give a user permission to create folder without give them root privlage

---

### Post by sisco311 on 2010-11-05
Did you read the links I posted?

They need write and execute permissions on the parent directory. You could add them to a common group, i.e. **users** (but you can create a new one if you wish), change the group of the directory to **users** and set the permissions to 0775. If the sticky bit is set (1775), then only the only the owner of the directory or the owner of the file will be able to delete that file.

HTH

---

