---
title: "Could not download all repository indexes"
date: 2010-04-10
forum: General Help
---

### Post by mravikiran on 2010-04-10
Hi friends i'm new to ubuntu... needed help!!!!
Getting following error message when i tried to update

**Could not download all repository indexes**
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

The above lines are the error message i get...please help me..

---

### Post by drs305 on 2010-04-10
mravikiran,

Welcome to Ubuntu and the Ubuntu forums.

You are most likely getting this error because you do not have the LiveCD you installed Ubuntu with inserted in your drive. 

You don't need it, so you can modify your files so it isn't expected.

Open Synaptic: System, Administration, Synaptic Package Manager.
From the main menu: Settings, Repositories, Ubuntu Software tab.
Untick the CD reference in the lower panel. 
That should eliminate the message.

If it is not ticked, check the "Other Software" tab to see if another CD is enabled in that section. If so, deselect it.

If that solves the issue, please click on the "Thread Tools" link at the top right of the first post and mark the thread "Solved". You can change it back later if needed.

---

### Post by mravikiran on 2010-04-10
Thanks a lot for the prompt reply and solution to the problem...my problem has been solved now...thanks a lot once again...have a great day

---

