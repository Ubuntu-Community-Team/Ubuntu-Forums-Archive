---
title: "folders permission problems"
date: 2009-06-27
forum: General Help
---

### Post by roquin on 2009-06-27
Hi, everybody, im brand new over here, and new in linux,  im having a lot of problems to configure ubuntu OS But now i want to start with permission folder, files etc. My problem is i can't edit, open, unlock them.  I get a message like: only the owner can't do it, but im the owner. any advice i wold appreciate it, thanks

---

### Post by philcamlin on 2009-06-27
oh welcome to the forums :)

do you need help wih folder permnissions :P

---

### Post by kokkus on 2009-06-27
Security reasons. In windows you can delete and edit everything including system files. To get super user promission you have to start commands with gksudo. So to delete or edit any system related files, go to terminal and type gksudo nautilus . Nautilus is sort of what they call explorer in windows.

EDIT: You have to be careful though.
Only use this if you really need to. 
Put all your private files, documents, videos and mp3s etc. in your home folder.

---

### Post by oldos2er on 2009-06-27
> **roquin said:**
> Hi, everybody, im brand new over here, and new in linux,  im having a lot of problems to configure ubuntu OS But now i want to start with permission folder, files etc. My problem is i can't edit, open, unlock them.  I get a messege like: only the owner cant do it, but im the owner. any advice i wold apreciate, thanks

 Anytime you're working outside of your /home/username directory, you'll need to give yourself root (or admin) privileges. Please read [https://help.ubuntu.com/8.04/administrative/C/](https://help.ubuntu.com/8.04/administrative/C/) for more info.

---

### Post by roquin on 2009-06-27
KOKKUS thank you very much  your advice was accurate and help full

---

