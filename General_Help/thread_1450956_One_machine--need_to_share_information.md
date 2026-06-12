---
title: "One machine--need to share information"
date: 2010-04-09
forum: General Help
---

### Post by mike67114 on 2010-04-09
Two questions, but I think they have much in common.

1) What is the purpose of the "Public" folder under my 
/home/{*username*} directory?

2) How do I share a folder and its contents between two separate user accounts ON THE SAME MACHINE? ( not a network situation. )

 I don't mind changing permissions, but do I need Samba, etc? That seems to be an awfully heavy solution.

---

### Post by -humanaut- on 2010-04-09
chmod 666 on /home/yourdirectory would allow for groups, and others to Read & write from your /home that'd be the simplest way you could add the other user to a specific group and grant that group permissions to your /home/directory something like chmod 760

---

