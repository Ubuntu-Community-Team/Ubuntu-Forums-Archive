---
title: "wine version stuck at 1.1.44"
date: 2011-04-10
forum: General Help
---

### Post by paddyponchero on 2011-04-10
Removed wine and installed wine1.2 but wine --version still shows 1.1.44
Then removed wine1.2 and installed wine1.3 wine --version still shows 1.1.44

Have tried removing all versions and reinstalling and deleting my .wine folder.

On my other computer upgrades work perfectly and the correct verion is display, am totally stumped.

---

### Post by davidmohammed on 2011-04-10
if you type 

which wine

does it report /usr/bin/wine?

If it doesnt, maybe you compiled/installed manually and you are picking up a older wine version in your path?

---

### Post by paddyponchero on 2011-04-10
Thanks for the help :) Need wine to do my tax return otherwise I have to try to find my windows cd in the attic :frown:

You're right which wine gives

/usr/local/bin/wine

Can I just delete that version? I can't make uninstall because the source is long since gone in cleaning up my drive.

---

### Post by davidmohammed on 2011-04-11
I would try renaming your /usr/local/bin/wine to something else - then retry 

```
which wine
``` 

- hopefully the officially installed wine path will be then displayed

If you get any wine issues due to moving from v1 to v2/3 its probably worth renaming your ~/.wine folder and then reinstalling your tax software.

---

