---
title: "luckyBackup / rSync issue with mapped drive. permission denied error?"
date: 2010-10-13
forum: General Help
---

### Post by ijason on 2010-10-13
greetings.

i am fumbling my way through the luckyBackup front-end for rSync. i successfully backed up a local drive, and am moving on to more advanced stuff. namely, a drive in a windows computer i am networked to.

i was able to find the correct link in my /home/.gvfs/ for the networked source drive. the destination drive is local, so no complications there. 

trouble starts when i tried to do the back-up. rSync puked with permission errors - presumably when it tried to actually start copying - after it indexed and calculated the space needed. weirdly, when i brows to the shared drive via the link on my desktop i get no requests for passwords. i'm listening to a file from there currently.

i have seen other people using rSync command line, and including their login credentials. i haven't found these options in the luckyBackup gui. luckyBackup does have a "remote" tab in the advanced settings for a backup, but it's not clear if that's intended for a LAN or WAN application?

any suggestions would be appreciated!

/ubuntu 10.10
/luckyBackup 0.41

---

### Post by ijason on 2010-10-13
update :

here is the error message :

> rsync: recv_generator: mkdir"/media/b_music/my music on windowsdesktop" failed: permission denied (13) *** skipping contents... ***

does rsync function by first putting a directory on the drive to be backed up? i'm not sure why it would try to write to the shared drive? more importantly, as far as windows is concerned other users can change the files. so i should have read/write permissions.

---

### Post by CharlesA on 2010-10-13
What's the syntax you are using? It's normally:

rsync source destination

---

