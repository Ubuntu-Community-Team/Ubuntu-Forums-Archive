---
title: "Accessing Hard Drive Files on a Windows Computer"
date: 2009-09-19
forum: General Help
---

### Post by Shalgoth on 2009-09-19
My file server running linux decided to stop working the other day, no idea why. I pulled the 2nd hard drive out that i used for storage and plugged it into my windows computer. I am now using a live-cd to transfer the files that i need from the storage hard drive to my windows hard drive, but some of the files give me a "permission denied". How do i gain permission to use these files? thanks.

---

### Post by undecim on 2009-09-19
You can run "sudo chmod -R ubuntu:ubuntu /path/to/a/file/or/directory/"  to make user 1000 (the livecd user) the owner of those files, and that should fix the permissions error (though this will permanently change permissions on the drive, which can be bad depending on what the files are, if you want to fix your server and put that same drive back in without reformatting.)

---

