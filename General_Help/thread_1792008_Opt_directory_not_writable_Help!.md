---
title: "Opt directory not writable? Help!"
date: 2011-06-27
forum: General Help
---

### Post by Shvesley on 2011-06-27
Im trying to install a game called "PlaneShift" and Im getting an error message when the game tries to install to my opt directory. It says....

The directory
/opt
is not writable by the current user

I have no idea what to do. At the moment the installer is on my desktop. I am running Ubuntu 11.04.

---

### Post by LukeMorrison on 2011-06-27
Did you attempt the command using sudo?  It may just be a simple permissions issue.

---

### Post by Shvesley on 2011-06-27
I don't know how to do that.

---

### Post by oldos2er on 2011-06-27
Your user account only has write access within your home folder, "sudo" elevates write privileges to system folders, including /opt. For example ```
sudo sh ~/Desktop/PlaneShift-v0.5.7-x64.run
```

---

