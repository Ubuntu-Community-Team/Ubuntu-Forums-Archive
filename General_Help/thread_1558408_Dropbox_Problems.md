---
title: "Dropbox Problems"
date: 2010-08-22
forum: General Help
---

### Post by roswell1211 on 2010-08-22
Hi,
I've had a look on ehre and on Dropbox's forum and can't find a good answer to my problem - maybe someone here can help, or advise me.
I am trying to use dropbox in Lucid.
I've installed it from the repos and it works for a while. Until I stop it and restart it or until I restart my machine.
Then it comes up saying 'Can't access dropbox folder' and fails to connect to the dropbox folder .
I'm pretty sure that this is a permissions issue, because if I completely 'uninstall' dropbox and the associated folders in my home folder and reinstall then it works temporarily again.
Also, if I run it as root is can connect to the 'Dropbox' folder.
I have tried chmod -R on the folder and it makes no difference. I haev tried chown and changing the owner to the user that I sign in with, but still no luck.
Can anyone help me or tell me of anyway to diagnose the problem better?

---

### Post by john newbuntu on 2010-08-22
I am assuming you have tried the following suggestions from the Dropbox forums:
sudo chown -R $USER ~/Dropbox
sudo chmod -R u+rw ~/Dropbox
sudo chown -R $USER ~/.dropbox
sudo chmod -R u+rw ~/.dropbox
The other thing is to try and unlink your account rather than re-installing dropbox each time and connecting it.  This is just a shot in the dark.  The interesting part is I have files that are owned by root and even those get sync'd just perfectly!! Go figure.

I downloaded version 0.7.110 from  [http://www.dropbox.com/downloading?os=lnx](http://www.dropbox.com/downloading?os=lnx) and have not experienced this  problem.  Not sure if this will solve your problem.  But if you have no  other ideas, try it.  Move(or delete) Dropbox, .dropbox-dist and  .dropbox prior to installation(if you haven't stored too many files  here)

---

### Post by dan000 on 2013-02-04
I had this same problem. Turns out the problem was inotify. Found my solution here: [http://askubuntu.com/questions/247461/how-do-i-fix-a-cant-access-dropbox-folder-error](http://askubuntu.com/questions/247461/how-do-i-fix-a-cant-access-dropbox-folder-error)

---

### Post by howefield on 2013-02-04
Old thread closed.

---

