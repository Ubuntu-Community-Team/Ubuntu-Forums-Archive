---
title: "how to create read-only folders"
date: 2009-09-25
forum: General Help
---

### Post by oof on 2009-09-25
Hello ,

I would like that certain folders located in the Desktop will be protected from deletion by password, but at the same time that files lbelonging to such folders could be freely deleted created and changed (without the need to type a password). It seems this option cannot  be implemented by using  chown and chmod commands, at least not in the Desktop (access to desktop files does not require sudo privilages). So what can I do


 (I simply want that certain files in the desktop could not be deleted by mistake)


thanks for your help 

:P

---

### Post by Liolikas on 2009-09-25
You are right chown and chmod is what you need it can do job no matter where even on Dekstop. And chown root <file> will make file owner root so sudo password will be needed but others may be able to do something to to take away all rights from others you can chmod o-rwx <file>

More details in chown/chmod tutorials in google.

---

### Post by Frungi on 2009-09-25
I&#8217;m not sure if what you&#8217;re wanting to do is possible, but you should be able to get the same effect with a protected dummy file in each folder; can't delete a folder if you don&#8217;t have permission to delete a file inside.

---

### Post by oof on 2009-09-25
> **Frungi said:**
> I&#8217;m not sure if what you&#8217;re wanting to do is possible, but you should be able to get the same effect with a protected dummy file in each folder; can't delete a folder if you don&#8217;t have permission to delete a file inside.

 Frungi,  This is a nice workaround if it works but I tested it and the folder can still be deleted. I just did  sudo chown root:root ~/Desktop/xx/x sudo chmod 600 ~/Desktop/xx/x and then deleted ~/Desktop/xx folder with no need to type any password

---

### Post by Frungi on 2009-09-25
> **oof said:**
> Frungi,  This is a nice workaround if it works but I tested it and the folder can still be deleted. I just did  sudo chown root:root ~/Desktop/xx/x sudo chmod 600 ~/Desktop/xx/x and then deleted ~/Desktop/xx folder with no need to type any password
Well that seems… broken. I didn’t think you could delete files that you didn’t have permissions to, by deleting the folders containing them. Sorry.

---

### Post by oof on 2009-09-25
> **Frungi said:**
> Well that seems… broken. I didn’t think you could delete files that you didn’t have permissions to, by deleting the folders containing them. Sorry.

 you do not need to be sorry, everything is under control :)

---

### Post by c0mput3r_n3rD on 2009-09-25
with that chown root file_name, how do you undo that? haha

Never mind I got it:
sudo chown [username] file

---

