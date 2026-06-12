---
title: "Assertion Failed"
date: 2010-05-12
forum: General Help
---

### Post by dstuttgen on 2010-05-12
Hello, new Ubuntu user here. Running HP G60-120us AMD Turion X2 dual core 2.o ghz 3072 MB DDR2 SDRAM Dual booting Ubuntu 10.04 and Win Vistavirus

While saving bookmarks in Firefox I get this Fail pop-up box. Anyone know what it is about and how do I make it behave itself and go away?

Assertion Failed
ASSERT: parent node must have _DOMElement set
Stack Trace: 
0:PMV_nodeRemoved([object ResultNodeClassInfo],[object ResultNodeClassInfo],4)
1:moveItem(94,85,-1)
2:PMIT_doTransaction()
3:doTransaction([xpconnect wrapped nsITransaction])
4:PlacesTxn_doTransaction([xpconnect wrapped nsITransaction])
5:doTransaction([xpconnect wrapped nsITransaction])
6:EIO_onFolderMenuListCommand([object XULCommandEvent])
7:oncommand([object XULCommandEvent])


It seems the 0: P  wants to display as 0:P  ?!?!?!
ASSERT: parent node must have _DOMElement set
Stack Trace: 
0: PMV_nodeRemoved([object ResultNodeClassInfo],[object ResultNodeClassInfo],4)
1: moveItem(94,85,-1)
2: PMIT_doTransaction()
3: doTransaction([xpconnect wrapped nsITransaction])
4: placesTxn_doTransaction([xpconnect wrapped nsITransaction])
5: doTransaction([xpconnect wrapped nsITransaction])
6: EIO_onFolderMenuListCommand([object XULCommandEvent])
7: oncommand([object XULCommandEvent])


Thanks, Dan

---

### Post by pootan on 2010-05-17
I'm getting this as well and also on certain pages just by loading. A browser restart helps for a little bit but isn't a permanent solution. I marked firefox for re installation and this didn't help either. I'd rather not remove firefox completely because I have a lot if tweaks in  about:config. Any answers on this?

---

### Post by AggravatedGestalt on 2010-05-31
I am dealing with same annoyance too. Seems to have just started this week.  Below is one of many examples of the error message:    ASSERT: node must have _DOMElement set.     I guess if this persists, I will post more error messages eventually.

---

### Post by pootan on 2010-08-18
It's become an annoyance for me i have to live with. Looking at the bugs filed they say they've released a fix but nothing is answered after that. I might just try out a Firefox beta and see if the problem persists

---

