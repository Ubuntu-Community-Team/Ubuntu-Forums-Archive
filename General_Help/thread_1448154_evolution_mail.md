---
title: "evolution mail"
date: 2010-04-06
forum: General Help
---

### Post by hammergil on 2010-04-06
I have my Ubuntu on one partition and I would like to have all of my emails actually stored (not backed up) on a different partition.  Is this possible?  Right now the default location for emails is /home/.evolution (I think)...can I change the path for the mail folder to a different partition?

thanks in advance

---

### Post by ajgreeny on 2010-04-06
You could probably do it by linking the mail folders of evolution to the actual mail folders on the other partition.  I don't use evolution, so can't really help any more than that, but I don't see why it should not work.

Try it out by copying your mail folders from evolution where they are at the moment to the new location.  Now making sure they are actually moved first, delete the mail folders from the ~/.evolution folder in home, and then drag the folders from the new location to the ~/.evolution folder with the mouse middle button, and choose to "link".

I can see no reason why that would not work, but try it out. You will have the mail folder backed up in the new location, so can always go back again to the old way if needed.

---

