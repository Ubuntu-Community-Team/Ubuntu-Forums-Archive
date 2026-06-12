---
title: "Opening folder problems"
date: 2010-10-22
forum: General Help
---

### Post by Gargon0 on 2010-10-22
I'm having problems with my PLACES folders. Everytime I attempt to move 1 folder to another or even attempt to open the folder, it opens a web browser. I'm running Ubuntu from an 06 hp pavillion with intel. i initially was having problems with my web cam. (it doesn't work) but when my boyfriend had me trouble shoot this new problem, (not being able to open folders) began. Idk what to do and I need help!!!!

---

### Post by mc4man on 2010-10-22
I knew this was going to become a common issue - filed various bugs starting 3 months ago - not fixed or addressed yet.

To return to nautilus as default folder handler

 r. click on any folder (if none available on Desktop then just create one) -> Open With -> Other Application
scroll down and choose 'Open Folder'

**In the future** when using the Open With -> Other Application menu on a folder make sure  that the 'Remember this application for "folder" files' is not enabled - otherwise any app chosen will become the new default folder handler

orig. bug that dead ended as a 'dupe'
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833)

New bug to prevent this from happening as much (could use confirming - myself I'm giving up - [have re-built nautilus]("http://ubuntuforums.org/showthread.php?t=1591892") to stop this behaviour here
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)

---

