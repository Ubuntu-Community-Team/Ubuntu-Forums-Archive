---
title: "How Do I make k3b Close A Data DVD+RW?"
date: 2010-12-08
forum: General Help
---

### Post by Spaceman9 on 2010-12-08
I'm trying to backup my data files to a DVD+RW and for some reason even though I set k3b to "No Multisession" k3b doesn't close the DVD. What do I have to do to make k3b burn a data DVD+RW and close the stupid thing instead of leaving it open for more data? Thanks for any help.

---

### Post by Spaceman9 on 2010-12-08
Ok, I found out I was doing wrong.

First I had to set the &#8220;Permissions&#8221; in k3b so by checking off 
cdrdao
cdrecord
growisofs
so that each of them was set to root. That&#8217;s done in the &#8220;Found Programs&#8221; window in &#8220;Settings", &#8220;Set Up System Permissions&#8221;.

Then in &#8220;Set Up K3b&#8221;, &#8220;Advanced", I had to un-check  &#8220;Automatically erase CD-RW&#8217;s and DVD-RW&#8217;s&#8221;. DVD-RW&#8217;s and DVD+RW's should never be erased only over written.

---

