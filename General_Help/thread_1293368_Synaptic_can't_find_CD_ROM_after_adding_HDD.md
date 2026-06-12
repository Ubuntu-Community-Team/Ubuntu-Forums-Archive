---
title: "Synaptic can't find CD ROM after adding HDD"
date: 2009-10-17
forum: General Help
---

### Post by Lee Wilkerson on 2009-10-17
After installing Ubuntu 8.0?, I added another HDD. Now Synaptic Package Manager can't find the CD in the CD ROM. It isn't even looking at the drive. I guess it's looking at the other HDD instead. Is there a .conf file for synaptic or do I need to tweak something else?
                                                                     Linux noob Lee

---

### Post by bwang on 2009-10-17
You don't need the CD-ROM unless you are offline or have a slow internet connection. If you want to add or remove it, you can edit /etc/apt/sources.list or do it via System>Administration>Software Sources.

---

### Post by Lee Wilkerson on 2009-10-17
Nope. Neither one of those works. That's where the problem is. That's the reason I'm here. If you will re-read carefully, you will understand - Synaptic does not even TRY to read the CD ROM _drive_. I can't even trick it with "file:///media/cdrom0/".

---

