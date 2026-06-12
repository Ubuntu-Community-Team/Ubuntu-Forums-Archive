---
title: "Trash not working"
date: 2010-03-05
forum: General Help
---

### Post by deez on 2010-03-05
I'm running ubuntu 9.10 64 and it's been great for the past 2 months.  Today some problems started with the trash.  It started as the trash not responding at all.  It wouldn't empty, wouldn't show what was in it, nothing.  

So I searched and someone suggested checking permissions, so I said sudo chmod 666 .local/share/Trash and then every time I wanted to trash something, the computer said I didn't have permissions to do that.  So I figured I reinstall.  I did that and the problem has changed.  

Now I can delete whatever I want, but it does not go into the trash.  It is deleted permanently and the trash is forever empty.  But if I look at .local/share/Trash there are three additional folders, 'files' 'info' and 'expunged'  Expunged is empty, but everything I've deleted is in 'files' and a matching file can be found in 'info'.  What's going on??

---

### Post by jerrrys on 2010-03-05
there are a lot of ways to get the job done, but for ease of use i would try **bleachbit**, its in the software center...

---

