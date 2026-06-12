---
title: "Save PDF Data w Evince (IRS Forms, etc)"
date: 2012-04-02
forum: General Help
---

### Post by rajan on 2012-04-02
As most of us will be working on taxes soon, I want to share a fix for a problem I ran into while trying to fill out the IRS forms. The problem is that Evince does not properly save data included on forms, such that if you fill out your form (i.e. 1040), save it and then open the saved copy, the data will not be visible. The workaround is here:

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/518230](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/518230)

and it's very simple. If you have a form that Evince is incapable of saving data onto, use the following command:

```
pdfopt <oldfile> <newfile>
```

Then edit the <newfile>. 

I have been searching for the solution to this for a while, so hopefully it helps someone else not have to look as hard for the fix. It appears that the bug is fixed in later versions so it's possibly not a problem anymore. 

```
rajan@malathi:/tmp$ uname -a
Linux malathi 2.6.32-40-generic #87-Ubuntu SMP Tue Mar 6 00:56:56 UTC 2012 x86_64 GNU/Linux
```

---

