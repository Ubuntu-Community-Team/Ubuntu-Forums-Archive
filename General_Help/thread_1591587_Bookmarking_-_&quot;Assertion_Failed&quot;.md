---
title: "Bookmarking - &quot;Assertion Failed&quot;"
date: 2010-10-09
forum: General Help
---

### Post by Megaptera on 2010-10-09
Ubuntu 10.04 with Firefox.

When using menu > bookmark manager > bookmark this page I get a po-up titled "Assertion Failed" with the following text:


ASSERT: parent node must have _DOMElement set
Stack Trace: 
0:PMV_nodeRemoved([object ResultNodeClassInfo],[object ResultNodeClassInfo],1)
1:moveItem(237,199,-1)
2:PMIT_doTransaction()
3:doTransaction([xpconnect wrapped nsITransaction])
4:placesTxn_doTransaction([xpconnect wrapped nsITransaction])
5:doTransaction([xpconnect wrapped nsITransaction])
6:EIO_onFolderMenuListCommand([object XULCommandEvent])
7:oncommand([object XULCommandEvent])
8:doCommand()
9:EIO_onFolderTreeSelect()
10:onselect([object Event])
11:select(5)
12:onxblmousedown([object MouseEvent])




No idea why smilies show up!!!! Not in the pop-up!!!

I can click 'ok' a couple or three times and eventually bookmark, but what's gone wrong and how can I put it right??

Thanks in advance

---

### Post by lovinglinux on 2010-10-09
Start Firefox in safe mode and check if the problem persists. Could be an extension causing this.

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by Megaptera on 2010-10-10
Thanks, I'll get on with that. Sorry 'bout delay in replying ... it's morning now!!

---

