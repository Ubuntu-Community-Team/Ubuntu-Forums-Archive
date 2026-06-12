---
title: "Converting a &quot;load java&quot; script from Windows to Ubuntu"
date: 2010-12-20
forum: General Help
---

### Post by ChrisDragonKni on 2010-12-20
Hello,

I have an old script which I used on Windows and am trying to work out the equivilant to use with Ubuntu. The script originally used wjview to load a java class. I have googled a bit and see that wjview is microsoft's java command line viewer. Could anyone suggest how to load this java program?

The original CMD script looked like this:

@start wjview /a host="domain.com"  com/domain/Example.class


Many thanks to anyone who can help.

---

### Post by katykat on 2010-12-20
Try
wine wjview /a host="domain.com"  com/domain/Example.class

Apparently its a windoze file, so wine should know how to run it....

---

