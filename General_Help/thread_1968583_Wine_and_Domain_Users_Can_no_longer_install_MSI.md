---
title: "Wine and Domain Users: Can no longer install MSI"
date: 2012-04-29
forum: General Help
---

### Post by tmknight on 2012-04-29
Hi:

Fresh install of xubuntu 12.04 x86_64 and I can no longer perform install of a particular MSI (this MSI installed fine on 11.10, and another MSI I tried did work on 12.04 - so it seems random) - the MSI installs fine as local user.  I was able to perform execution of non-MSI based app as domain user.  I was able to work-around the issue by copying the prefix of the same user from a working system (which was an upgrade from 11.10 to 12.04 vs fresh install), but it is not elegant or desired.  I also as a test tried installing the MSI on the "working" system (an upgrade from 11.10 to 12.04) for an existing domain user that had not before executed the MSI - same issue.  Seems to be something in 12.04. Anyone else seeing this?  I have not through searching anyone reporting anything even close to this behavior, nor anything helpful on the error - hoping a direct question will yield fruit.  Like I said, I was able to create a work around, but would be interested if others are now seeing this on some MSI.

error:```

fixme:storage:create_storagefile Storage share mode not implemented.
err:msi:ITERATE_Actions Execution halted, action L"ValidateCommandLine" returned 1603
```

Cheers in advance!

---

