---
title: "CUPS Problem"
date: 2006-06-01
forum: General Help
---

### Post by rbrugman on 2006-06-01
After upgrading to Dapper and completely removing and purging CUPSYS after it wouldn't install I am having problems.  When I try to add a printer, USB printers don't even show up.  The main page shows "Canon" as an available printer to add although I never have owned a Canon printer.  When I try to add a printer, aside from USB printers not being shown, it says "426 Upgrade Required" and goes back to the main page.

In short, I cannot readd my printers!  Can anyone help?

Thanks!

Robert

---

### Post by EndPerform on 2006-06-24
Try putting the following line in your cupsd.conf:

```
DefaultEncryption IfRequested
```

That will eliminate the 426 error and let you get on with printer configuration.

---

