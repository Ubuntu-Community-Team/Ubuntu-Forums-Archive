---
title: "Deleted Home Folder won't go away"
date: 2011-01-15
forum: General Help
---

### Post by tobold on 2011-01-15
Hey folks, 

Two month ago I accidentally deleted my home folder (yes, very stupid idea but it wasn't on purpose).

I managed to recover the home folder from /home/.Trash-0/tobias by copying it back to where it belongs and changing the file ownership from "root" to my user (tobias). 

After this recovery I tried to delete /home/.Trash-0/tobias but it wouldn't work. Whenever I tried, a new folder appeared in /home/.Trash-0/ (root home) named tobias.2, tobias.2.2 and so on. (see first screenshot). This means I had two copies of my home folder on my hard disk (2 x 156.1 GB at that time).

At that time I didn't care since I had enough disk space left (33.8 GB, see second screenshot) and thought Ubuntu would take care of this some time by removing the files in /home/.Trash-0/. 

Fast forward to today, I get warnings of low disk space. My home folder today is around 160 GB but together with the deleted one in /.Trash-0/ I only have 1.3 GB disk space left in my home folder.

Any ideas how to delete the unused second home folder copy? Or is there some other way to free the disk space occupied by .Trash-0/ ?

(Ubuntu 10.04. LTS on vaio VPCEB1S1E btw)

Thanks in advance!


[IMG]http://i.imgur.com/HFdj7.png[/IMG]

[IMG]http://i.imgur.com/LQouJ.png[/IMG]

---

### Post by tobold on 2011-01-15
Never mind, I solved it by deleting the folder via the console:

sudo rm -R /home/.Trash-0/files/tobias.2.2.2

---

