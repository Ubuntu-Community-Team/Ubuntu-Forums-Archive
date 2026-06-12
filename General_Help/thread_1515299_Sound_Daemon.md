---
title: "Sound Daemon"
date: 2010-06-22
forum: General Help
---

### Post by MikeBeveridge on 2010-06-22
G'day I have recently installed 10.04 and am loving it.  the only issue I have is as follows

When I go to System>preferences>sounds.  I get the "Waiting for Sound system to respond" message.   I do have sound but just cannot access that menu.  I created a new user and noticed that they do not have the same issue.  ie when that second user opens System>preferences>sound the window opens as you would expect. 

I have been searching for a while and cannot seam to find a solution.  I have tried adding the pulseaudio to the startup applications.  Its almost as if my account is the root account, as that account suffers the same issue.  I had a look under the user and groups menu and noticed that my account is an "administrator"  I assume that is different to root.  And it won't let me change it anyway.   I cannot seem to get the pulseaudio process to run.

Any ideas would be greatly appreciated.

---

### Post by MikeBeveridge on 2010-06-22
OK, i think i found my issue.  All the files and folders in /home/myuser is owned by root.   not by me.    How do change that?

chown myuser  folder?

---

### Post by MikeBeveridge on 2010-06-22
it appears that I cannot change the owner of my home folder because it is mounted on a ntfs formatted volume.  All the new users I have created have there home mounted on an ext3 volume which allows the changing of ownership.

Of course I am assuming the ownership of the .pulse folder is the cause of my original issue.

---

### Post by MikeBeveridge on 2010-06-22
bump

---

### Post by MikeBeveridge on 2010-06-27
Well this weekend I reorganized my files and now have my home mounted on an ext4 partition.  This has solved my sound daemon problem.

This thread should be marked as solved.

Cheers


Mike

---

