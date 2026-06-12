---
title: "Rhythmbox auto-starts when mounting NTFS volume"
date: 2010-12-23
forum: General Help
---

### Post by AlphaNeil on 2010-12-23
[LEFT]Whenever I mount any of the ntfs volumes, instead of opening the volume, Rhythmbox starts automatically and scans volume for media files. It has nothing to do with media files as it starts even when there is no media file in the volume. 
Does it have anything to do with Nautilus? What can be the problem? 
[/LEFT]

---

### Post by tredegar on 2010-12-23
Your file associations are messed up.

Find the drive icon (in **/media** or **/mnt** ).
R-click it.
Choose Open with .... Other Application
Select "File Browser"
Select "Remember.."
Click Open.
Done.

---

### Post by AlphaNeil on 2010-12-23
Thanks tredegar. It solved my problem. Thank you very much.

---

