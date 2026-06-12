---
title: "saving former copies in gedit"
date: 2010-03-30
forum: General Help
---

### Post by linxuser14 on 2010-03-30
I was wondering if anyone has thought/done, having a way for gedit to append a oldfile~ to a say

 oldfile~~ before it overwrites the original file, and replaces the oldfile~? Or is gedit deleting

 the oldfile~, renaming current, and saving current edit as original? I'm not sure if I'm 

explaining my question right. My concern is when editing a 2nd time the last version backed up is lost.


  I know a bit of redundancy is created but it sometime being able to go back and see what it was

 previous to the last time would be nice.


  Currently, if I think the need might arise I open a gksu nautilus to show the oldfile~ 's and

 rename them to oldfile-1~, then oldfile-2~ ,... etc. Just wondering if anyone has simplified the concept.


  I haven't been able to form a search request to find such a thing. But, I'll continue to try.

:guitar:

---

### Post by Barriehie on 2010-03-31
I use vim and it's got pretty much the same behavior.  If you can BASH I'll post the script when I get it done.  What it does is oldifle~ becomes oldfile.mm-dd-yyyy.HH.MM.SS-*seconds since the epoch*  Every time an oldfile~ is created it gets renamed as above.  I've still got some bugs to work out before it works like I want.  Right now it can't find .oldfiles~ and many config files are .somefilename

---

